ARG NAMESPACE
ARG PREREQS_TAG
FROM ${NAMESPACE}/ue4-build-prerequisites:${PREREQS_TAG}

# Enable verbose output for steps that patch files?
ARG VERBOSE_OUTPUT=0

# The git repository that we will clone
ARG GIT_REPO=""

# The git branch/tag/commit that we will checkout
ARG GIT_BRANCH=""

# Install our git credential helper that retrieves credentials from build secrets
COPY --chown=ue4:ue4 git-credential-helper-secrets.sh /tmp/git-credential-helper-secrets.sh
ENV GIT_ASKPASS=/tmp/git-credential-helper-secrets.sh
RUN chmod +x /tmp/git-credential-helper-secrets.sh && echo '' && echo 'RUN directive complete. Docker will now commit the filesystem layer to disk.' && echo 'Note that for large filesystem layers this can take quite some time.' && echo 'Performing filesystem layer commit...' && echo ''

# Clone the UE4 git repository using the build secret credentials
# (Note that we include the changelist override value here to ensure any cached source code is invalidated if
#  the override is modified between runs, which is useful when testing preview versions of the Unreal Engine)
ARG CHANGELIST
RUN --mount=type=secret,id=username,uid=1000,required \
	--mount=type=secret,id=password,uid=1000,required \
	CHANGELIST="$CHANGELIST" \
	mkdir /home/ue4/UnrealEngine && \
	cd /home/ue4/UnrealEngine && \
	git init && \
	git remote add origin "$GIT_REPO" && \
	git fetch --progress --depth 1 origin "$GIT_BRANCH" && \
	git checkout FETCH_HEAD && echo '' && echo 'RUN directive complete. Docker will now commit the filesystem layer to disk.' && echo 'Note that for large filesystem layers this can take quite some time.' && echo 'Performing filesystem layer commit...' && echo ''

# Apply our bugfix patches to broken Engine releases such as 4.25.4
# (Make sure we do this before the post-clone setup steps are run)
COPY --chown=ue4:ue4 patch-broken-releases.py /tmp/patch-broken-releases.py
RUN python3 /tmp/patch-broken-releases.py /home/ue4/UnrealEngine $VERBOSE_OUTPUT && echo '' && echo 'RUN directive complete. Docker will now commit the filesystem layer to disk.' && echo 'Note that for large filesystem layers this can take quite some time.' && echo 'Performing filesystem layer commit...' && echo ''

# Run post-clone setup steps, ensuring our package lists are up to date since Setup.sh doesn't call `apt-get update`

# Ensure Setup.sh uses the same cache path when building either UE4 or UE5
ENV UE_GITDEPS=/home/ue4/gitdeps
ENV UE4_GITDEPS=/home/ue4/gitdeps
RUN mkdir "$UE_GITDEPS" && echo '' && echo 'RUN directive complete. Docker will now commit the filesystem layer to disk.' && echo 'Note that for large filesystem layers this can take quite some time.' && echo 'Performing filesystem layer commit...' && echo ''

# When running with BuildKit, we use a cache mount to cache the dependency data across multiple build invocations
WORKDIR /home/ue4/UnrealEngine
RUN --mount=type=cache,target=/home/ue4/gitdeps,uid=1000,gid=1000 sudo apt-get update && \
	./Setup.sh --exclude=Android --exclude=Mac --exclude=Win32 --exclude=Win64 && \
	sudo rm -rf /var/lib/apt/lists/* && echo '' && echo 'RUN directive complete. Docker will now commit the filesystem layer to disk.' && echo 'Note that for large filesystem layers this can take quite some time.' && echo 'Performing filesystem layer commit...' && echo ''

# The linker bundled with UE4.20.0 onwards chokes on system libraries built with newer compilers,
# so redirect the bundled clang to use the system linker instead
COPY --chown=ue4:ue4 linker-fixup.py /tmp/linker-fixup.py
RUN python3 /tmp/linker-fixup.py /home/ue4/UnrealEngine/Engine/Extras/ThirdPartyNotUE/SDKs/HostLinux/Linux_x64 `which ld` && echo '' && echo 'RUN directive complete. Docker will now commit the filesystem layer to disk.' && echo 'Note that for large filesystem layers this can take quite some time.' && echo 'Performing filesystem layer commit...' && echo ''

# Remove the sample `XXX` example platform code, since this breaks builds from 4.24.0 onwards
# (For details of what this is, see: <https://forums.unrealengine.com/unreal-engine/announcements-and-releases/1617783-attention-platform-changes-ahead>)
RUN rm -r -f /home/ue4/UnrealEngine/Engine/Platforms/XXX && echo '' && echo 'RUN directive complete. Docker will now commit the filesystem layer to disk.' && echo 'Note that for large filesystem layers this can take quite some time.' && echo 'Performing filesystem layer commit...' && echo ''

# Apply our bugfix patches to UnrealBuildTool (UBT)
COPY --chown=ue4:ue4 patch-ubt.py /tmp/patch-ubt.py
RUN python3 /tmp/patch-ubt.py /home/ue4/UnrealEngine/Engine/Source/Programs/UnrealBuildTool && echo '' && echo 'RUN directive complete. Docker will now commit the filesystem layer to disk.' && echo 'Note that for large filesystem layers this can take quite some time.' && echo 'Performing filesystem layer commit...' && echo ''
