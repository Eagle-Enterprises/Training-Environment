# Blueprint List

This file describes all of the Blueprint files that have been made by the Eagle
Enterprise Training Environment team that provide the functionality and logic to
the systems within the Environment that make it as realistic as possible.

## [TEMPLATE] Blueprint Name

**Path:** `/AirSim/Unreal/Environments/Blocks/Content/Blueprint/`

**Description:**

Describe the function, inputs, and outputs of a blueprint

**Author:** Adam

--------------------

## BP_Menu

**Path:** `/AirSim/Unreal/Environments/Blocks/Content/Blueprint/BP_Menu`

**Description:**

This Widget BP show the Pause Menu. Has a button to Continue, Reset
(In Progress), and to Exit the Game.

**Author:** Adam

--------------------

## BP_Demo1_Instance

**Path:** `/AirSim/Unreal/Environments/Blocks/Content/Blueprints/BP_Demo1_Instance`

**Description:**

This instance stores variables to be tracked throughout the entirety of the
demonstration. Variables like how many demo's have been completed and how much
time has elapsed per demo to be displayed in the Game End Screen.

**Author:** Adam

--------------------

## BP_Demo_Complete_Screen

**Path:** `/AirSim/Unreal/Environments/Blocks/Content/Blueprint/BP_Demo_Complete_Screen`

**Description:**

Widget that displays the times taken per demo and has buttons to either restart
the training Environment or Exit.

**Author:** Adam

--------------------

## BP_Level_Progress_Actor

**Path:** `/AirSim/Unreal/Environments/Blocks/Content/Blueprint/BP_Level_Progress_Actor`

**Description:**

This actor contains the logic to show the Pause Menu and tracks on Reset (which
is broken at the moment)

**Author:** Adam

--------------------

## BP_Level_Progress_Logic

**Path:** `/AirSim/Unreal/Environments/Blocks/Content/Blueprint/BP_Level_Progress_Logic`

**Description:**

This BP contains all of the logic that spawns the BP_Level_Progress_Actor and
advances the game play through the 3 demonstrations (TODO)

**Author:** Adam

--------------------

## BP_Demo_Display

**Path:** `/AirSim/Unreal/Environments/Blocks/Content/Blueprint/BP_Demo_Display`

**Description:**

This Widget Blueprint displays the current number of the demo on the HUD

**Author:** Adam

--------------------
