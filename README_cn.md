# 注意： 
 UE保存和加载游戏，自动子关卡存读档，流程控制，场景切换，结构体序列化。
 该项目帮忙用户熟悉功能的使用，结构体序列化蓝图在下个版本提供。

# 视频教程 [youtube](https://www.youtube.com/watch?v=mHXQYDZ_rW4)

# 设置
 1. 把'LQuickFrame' 添加到工程插件文件夹下，并开启插件。
 2. 在'Content'文件夹下右键，选择'QuickFrame/LSavePreset'创建存档预设。
 3. 配置'LSavePreset'并添加到 'ProjectSettings/Game/LQuickFrameSettings'。
 4. 设置'Game Instance Class'为LGameInst 在 'ProjectSettings/Maps & Modes'。

# 接口'LBaseInterface'
 ```c++
 //读档完成时，自动调用 
 void OnInit(bool bLoaded)
 //在特殊时期不需要存档的对象使用
 bool IsNowCanSave()
 //自定义存读档
 void OnSerialize(FArchive& Ar)
 ```

# 常用功能
 ```C++
 //存档世界
 LSaveSystem->SaveWorld
 //存档对象
 LSaveSystem->SaveObject
 //读档对象
 LSaveSystem->LoadObject
 /* 
 * 新世界(切换场景)，流程说明
 * 1. 异步加载场景并切换，再加载子关卡。
 * 2. 场景加载完成，等待寻路导航数据加载。
 * 3. 调用所有对象 LBaseInterface->OnInit(false)
 * 4. 调用 LGameInst::OnGameStart
 */
 LGameInst->NewWorld
 /*
 * 读档世界，流程说明
 * 1. 读取slot信息，切换场景，并自动加载子关卡。
 * 2. 场景加载完成，等待寻路导航数据加载。
 * 3. 调用所有对象 LBaseInterface->OnInit(true)
 * 4. 调用 LGameInst::OnGameStart
 */
 LGameInst->LoadWorld
 //打开和释放关卡
 LGameInst->OpenCloseLevels
 ```

# 插件地址 [虚幻商城](https://www.fab.com/listings/72639c17-68d0-4e4a-8f92-0f0c3efb2b12)

# Copyright © 2025 liwei   email:289423619@qq.com