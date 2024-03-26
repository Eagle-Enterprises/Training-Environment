# Training Environment in Docker

This guide is for those who have not already installed AirSim and Unreal Engine
4.27.2 on the local machines.

## Link your GitHub Account with your Epic Games Account

<https://www.unrealengine.com/en-US/ue4-on-github>

## Verify you can see this GitHub Repository

<https://github.com/EpicGames/UnrealEngine>

## Install Docker

Windows: [Install Docker Desktop for Windows](https://docs.docker.com/docker-for-windows/install/)
Mac: [Install Docker Desktop for Mac](https://docs.docker.com/docker-for-mac/install/)

## Create a GitHub Personal Access Token

   1. Settings >> Developer Settings >> Personal Access Tokens >> Tokens(classic)
   2. Generate new token >> Generate new token (classic)
   3. Make arbitrary note and expiration
   4. Select `read:packages` Scope
   5. Generate Token
   6. Copy & Save the Token Value

## Login to ghcr.io

   1. Open Command Prompt/Terminal of Choice
   2. `export ACCESS_TOKEN=<TOKEN VALUE>` <<-- PSAT Value
   3. `export USER_NAME=<NAME VALUE>` <<-- GitHub Username
   4. `echo ACCESS_TOKEN | docker login ghcr.io -u USERNAME --password-stdin`

## Pull Prebuilt Container Images

`docker pull ghcr.io/epicgames/unreal-engine:dev-4.27`

*This will take a while

## Running the container

* `export PROJECT_PATH=<cloned directory>/Training-Environment/AirSim/Unreal/Environments/Blocks`
* `docker run --rm -ti -v "PROJECT_PATH:/project" ghcr.io/epicgames/unreal-engine:dev-4.27`

See here for the [Complete Guide](https://docs.unrealengine.com/4.27/en-US/SharingAndReleasing/Containers/)
