# Training-Environment

Software Repository for files relating to the Training Environment IPT. This
holds all the plugin files, Unreal Assets, and Unreal Blueprint files used to
create the Eagle Enterprises Training Environment.

## Visual Studio 2022 (the purple one, not the blue one)

How to setup Visual Studio for gUnreal Engine [Game Development](<https://docs.unrealengine.com/5.0/en-US/setting-up-visual-studio-development-environment-for-cplusplus-projects-in-unreal-engine/>)

Once complete, congrats you just took your first step into game development 😊🕹

## Install Unreal Engine v.4.27.2

1. Download the [Epic Games Launcher](https://www.unrealengine.com/en-US/download>)
2. Create an Account and Sign In
3. On the left hand side, navigate to UE
4. Click the 'plus' sign next to `Engine Versions` and select `4.27.2`
5. Once installed, the Launch Button in the upper right should have the version included

## Clone and Build AirSim

1. `git clone https://github.com/Microsoft/AirSim.git`
2. `cd AirSim`
3. Open Developer Command Prompt for VA 2022 **Run as Administrator**
4. Run `build.cmd`
5. Verify `AirSim/Unreal/Environments/Blocks/Blocks.uproject` exists

    [AirSim Documentation Source](https://microsoft.github.io/AirSim/build_windows/#build-airsim>)

## Clone Training Environment Repository

1. Outside of the AirSim Directory: `git clone https://github.com/Eagle-Enterprises/Training-Environment.git`
2. Copy the file from Step 5 above to `Training-Environment/AirSim/Unreal/Environments/Blocks/`

## Open Project

1. Open Unreal Engine 4.27.2
2. Have it open the file `Training-Environment/AirSim/Unreal/Environments/Blocks/Blocks.uproject`

## Unreal Development

Please see the documentation here for [Unreal Development](Unreal_Development.md)
