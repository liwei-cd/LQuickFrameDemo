# 注意： 该项目可以帮忙用户快速熟悉插件使用，如 存档世界，存档对象，世界切换，自动子关卡存读档，流程控制，结构体序列化等功能。 

# 设置
 1. 把'LQuickFrame' 添加到工程插件文件夹下，并开启插件。
 2. 在'Content'文件夹下右键，选择'QuickFrame/LSavePreset'创建存档预设。
 3. 配置'LSavePreset'并添加到 'ProjectSettings/Game/LQuickFrameSettings'。
 4. 设置'Game Instance Class'为LGameInst 在 'ProjectSettings/Maps & Modes'。

# 常用功能
 ```C++
 //存档世界
 LSaveSystem->SaveWorld
 //存档对象
 LSaveSystem->SaveObject
 //读档对象
 LSaveSystem->LoadObject
 //新世界
 LGameInst->NewWorld
 //读档世界
 LGameInst->LoadWorld
 //打开和释放关卡
 LGameInst->OpenCloseLevels
 //读档完成回调
 LGameInst::OnGameStart
 ```

# 特殊功能
 **对象需继承 'LBaseInterface' 接口**
 ```c++
 //读档完成时，自动调用 
 void OnInit(bool bLoaded)
 //在特殊时期不需要存档的对象使用
 bool IsNowCanSave()
 //自定义存读档
 void OnSerialize(FArchive& Ar)
 ```

# Copyright © 2025 liwei   email:289423619@qq.com