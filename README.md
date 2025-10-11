# [中文说明](./README_cn.md)

# Note: 
 UE saves and loads games, automatically saves and loads sub-levels, controls flow, switches scenes, and serializes structures. 
 This project helps users become familiar with using these features, and the structure serialization blueprint will be provided in the next version.

# Video [youtube](https://www.youtube.com/watch?v=mHXQYDZ_rW4)

# Setup
 1. Add 'LQuickFrame' to the project plugin folder and enable the plugin.
 2. Right-click in the 'Content' folder, select 'QuickFrame/LSavePreset' to create a save preset.
 3. Configure 'LSavePreset' and add it to 'ProjectSettings/Game/LQuickFrameSettings'.
 4. Set 'Game Instance Class' to LGameInst in 'ProjectSettings/Maps & Modes'.
 
# interface 'LBaseInterface'
 
 ```c++
 // Automatically called when loading is completevoid 
 OnInit(bool bLoaded)
 // Objects that do not need to be saved during special periods use this
 bool IsNowCanSave()
 // Custom serialization for saving and loading
 void OnSerialize(FArchive& Ar)
 ```

# Common Functions
 ```C++  
 // Save World
 LSaveSystem->SaveWorld
 // Save Object
 LSaveSystem->SaveObject
 // Load Object
 LSaveSystem->LoadObject
 /* 
 * New World(scene switching)，Process Description
 * 1. Asynchronously load the scene and switch, then load sublevels.
 * 2. After the scene is loaded, wait for navigation data to load.
 * 3. Call LBaseInterface->OnInit(false) on all objects.
 * 4. Call LGameInst::OnGameStart
 */
 LGameInst->NewWorld
 /*
 * Load World，Process Description
 * 1. read slot info，Switch scenes and automatically load sub-levels.
 * 2. After the scene is loaded, wait for navigation data to load.
 * 3. Call LBaseInterface->OnInit(true) on all objects.
 * 4. Call LGameInst::OnGameStart
 */
 LGameInst->LoadWorld
 // Open and Close Levels
 LGameInst->OpenCloseLevels
 ```

 # Plugin Address [Unreal Market](https://www.fab.com/listings/72639c17-68d0-4e4a-8f92-0f0c3efb2b12)

 # Copyright © 2025 liwei   email:289423619@qq.com