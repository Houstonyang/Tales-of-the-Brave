# 勇者奇谭 V1.0.0

基于 **Unity 2022.3 与 C#** 开发的 2D 横版动作游戏，包含平台跳跃、近战战斗、三类敌人、关卡传送和存档系统。

[Windows 游戏下载](https://github.com/Houstonyang/Tales-of-the-Brave/releases) · [算法与技术说明](docs/TECHNICAL.md)

## 下载与运行

1. 打开 [Releases](https://github.com/Houstonyang/Tales-of-the-Brave/releases)，下载附件 `Tales-of-the-Brave-v1.0.0.zip`。
2. 将压缩包**完整解压**到一个文件夹。
3. 双击 `My project 2.exe` 启动游戏。

EXE 名称沿用当前构建产物，游戏名称为《勇者奇谭》。请保留 EXE、`My project 2_Data`、`MonoBleedingEdge`、`UnityPlayer.dll` 和 `UnityCrashHandler64.exe` 的相对位置。

GitHub 自动生成的 `Source code (zip)` / `Source code (tar.gz)` 是仓库快照，不是可运行的游戏包。仓库根目录中单独的 EXE 也缺少运行依赖，请使用 Release 附件。

## 游戏内容

- **角色操作**：水平移动、落地跳跃、近战攻击、受击击退与死亡处理。
- **敌人行为**：野猪巡逻与加速追击、蜜蜂随机巡逻与定向追踪、蜗牛缩壳防御。
- **场景交互**：宝箱开启、存档点激活和关卡传送。
- **界面反馈**：血条、延迟扣血效果、暂停面板、失败面板、音量设置和受击震屏。
- **数据保存**：记录角色位置、生命值与当前场景。

## 操作方式

| 操作 | 键盘 | 手柄 |
| --- | --- | --- |
| 移动 | A / D 或左右方向键 | 左摇杆 |
| 跳跃 | Space | 南侧按键，通常为 A / × |
| 攻击 | J | 西侧按键，通常为 X / □ |
| 交互 | E | 东侧按键，通常为 B / ○ |
| 调试读档 | L | 无专用绑定 |
| 暂停与音量设置 | 点击设置按钮 | 通过 UI 操作 |

## 算法与技术

| 模块 | 实现 |
| --- | --- |
| 敌人 AI | 有限状态机（FSM）、状态模式、巡逻 / 追击 / 技能切换 |
| 移动与战斗 | Rigidbody2D、冲量跳跃与击退、攻击触发器、受伤无敌倒计时 |
| 环境感知 | OverlapCircle 地面与墙体检测、BoxCast 目标检测、LayerMask 筛选 |
| 飞行敌人 | 随机目标采样、向量归一化追踪、按轴阈值判断到达及攻击范围 |
| 动画 | Animator 参数、StateMachineBehaviour、动画控制攻击区域启停 |
| 模块通信 | ScriptableObject 事件通道、UnityEvent、接口抽象 |
| 场景管理 | Addressables 异步加载、Additive 场景组织、协程等待与加载防重入 |
| 存档 | GUID 标识、字典映射、Newtonsoft Json / JsonUtility 序列化 |
| 地图与画面 | Tilemap、组合碰撞体、URP 2D |
| 视听反馈 | Cinemachine、DOTween、AudioSource / AudioMixer |

算法原理、关键公式、设计取舍、依赖版本和源码索引见 [完整技术文档](docs/TECHNICAL.md)。技术文档基于本地 Unity 工程的实际代码整理。

## 仓库内容

本仓库用于项目展示、技术说明与 Windows 构建发布。当前没有收录完整的 `Assets/`、`Packages/` 和 `ProjectSettings/`，因此不能仅凭仓库中的 `.sln` / `.csproj` 还原 Unity 工程。

- `README.md`：游戏介绍、下载入口与操作说明。
- `docs/TECHNICAL.md`：算法与工程技术说明。
- **Releases 附件**：包含运行依赖的完整 Windows 游戏压缩包。

完整工程的开发入口为 Unity `2022.3.42f1c1` 下的 `Assets/Settings/Scenes/Initialization.unity`；该路径属于本地原始工程。

## 当前状态

- 发布包已核对所需运行文件，排除了 `DoNotShip` 调试目录；此次整理未重新构建或执行完整游戏测试。
- 宝箱开启与存档点点亮状态尚未纳入存档，当前存档不是完整世界快照。
- 移动时间步长、输入订阅、加载失败处理和存档健壮性等限制详见技术文档。
- 项目中有移动端输入配置，但当前提供的是 Windows 构建，未据此承诺移动端兼容性。

## 素材与许可

项目包含第三方素材和插件，其使用范围以各自许可为准。本仓库目前未声明统一开源许可证；公开展示不代表授予第三方素材再分发或商业使用许可。
