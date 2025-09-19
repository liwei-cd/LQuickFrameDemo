# [中文说明](./README_cn.md)

# Note: This project can help users quickly familiarize themselves with plugin usage, such as archive world, archive objects, world switching, automatic sub-level save and load, and flow control, and struct serialization.

# Setup
 1. Add 'LQuickFrame' to the project plugin folder and enable the plugin.
 2. Right-click in the 'Content' folder, select 'QuickFrame/LSavePreset' to create a save preset.
 3. Configure 'LSavePreset' and add it to 'ProjectSettings/Game/LQuickFrameSettings'.
 4. Set 'Game Instance Class' to LGameInst in 'ProjectSettings/Maps & Modes'.
 
# Common Functions
 ```C++  
 // Save World
 LSaveSystem->SaveWorld
 // Save Object
 LSaveSystem->SaveObject
 // Load Object
 LSaveSystem->LoadObject
 // New World
 LGameInst->NewWorld
 // Load World
 LGameInst->LoadWorld
 // Open and Close Levels
 LGameInst->OpenCloseLevels
 // Load Completion Callback
 LGameInst::OnGameStart
 ```

# Special Functions
 **Objects must inherit the 'LBaseInterface' interface**

 ```c++
 // Automatically called when loading is completevoid 
 OnInit(bool bLoaded)
 // Objects that do not need to be saved during special periods use this
 bool IsNowCanSave()
 // Custom serialization for saving and loading
 void OnSerialize(FArchive& Ar)
 ```

 # Copyright © 2025 liwei   email:289423619@qq.com