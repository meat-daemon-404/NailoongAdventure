# 奶龙冒险 · Nailoong Adventure

[![Unity 6.3 LTS](https://img.shields.io/badge/Unity-6.3_LTS_(6000.3.11f1)-000000?logo=unity)](https://github.com/meat-daemon-404/NailoongAdventure)
[![Zero External Assets](https://img.shields.io/badge/Architecture-100%25_Procedural_C%23-512BD4?logo=csharp)](https://github.com/meat-daemon-404/NailoongAdventure)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

> **100% 纯代码过程化生成的 3D 动作冒险游戏（Unity 6.3 LTS）** —— 零外部 3D 模型、零外部贴图、零外部音频资产：从奶龙（Nailoong）的 `SkinnedMeshRenderer` 骨骼蒙皮建模、三连击与四技能粒子特效、三阶段 Boss AI、三大主题关卡（阳光海滩 → 奇幻森林 → 熔岩火山），到 13 种 WAV 音效与 6 首多声道 BGM，全部在运行时由纯 C# 代码实时合成。

## 核心技术与玩法特性

### 1. 纯 C# 过程化骨骼建模与动画（`Assets/NailoongAdventure/Scripts/`）
- **实时参数化网格与蒙皮（`ProceduralMeshBuilder`）**：通过球谐变形、胶囊体布尔拼接与法线平滑生成奶龙角色与敌人网格，动态绑定骨骼权重与面部表情贴图。
- **手感调优与操作缓冲**：支持 **Coyote Time（土狼时间 0.12s）**、**Jump Buffer（跳跃输入缓冲 0.15s）**、三段普攻连招（含顿帧 Hitstop 与相机震屏）以及 4 个主动技能（火焰喷射、肚皮冲击、旋风横扫、奶龙护盾）。

### 2. 三大主题关卡与三阶段 Boss 战
- **关卡递进**：
  1. **阳光海滩（Beach）**：教学引导、椰林跳跃平台与巡逻小怪。
  2. **奇幻森林（Forest）**：移动浮台、毒雾陷阱与远程射手协同。
  3. **熔岩火山（Volcano）**：升降岩浆柱与三阶段 Boss 决战（近战冲锋 → 环形弹幕召唤 → 狂暴全屏冲击波）。
- **无障碍与多语言支持**：内置中/英文双语切换、色盲友好高对比度血条与伤害数字指示。

### 3. 过程化音频合成器（`ProceduralAudioGenerator`）
- 运行时直接通过 PCM 波形合成（正弦波、方波、粉红噪声包络与 FM 调制）生成 **13 类交互音效（SFX）** 与 **6 首场景/Boss 背景音乐（BGM）**，无需携带任何 `.mp3` / `.ogg` 外部文件。

### 4. 双端自动化构建管线（`GameBuilder.cs` & `build.bat`）
- **Windows x64 独立包**：`GameBuilder.BuildWindows64()` 一键输出免安装可执行程序。
- **WebGL 浏览器版**：`GameBuilder.BuildWebGL()` 集成 Brotli/Gzip `.unityweb` IndexedDB 缓存、移动端虚拟摇杆适配与 `link.xml`（`ManagedStrippingLevel.High` 防裁剪保护）。

## 快速构建与运行

```bash
git clone https://github.com/meat-daemon-404/NailoongAdventure.git
cd NailoongAdventure

# 方式一：使用 Unity Hub 打开工程（推荐 Unity 6000.3.11f1 或更高 Unity 6 LTS 版本）
# 打开后无需导入任何外部资源包，直接点击 Play 即可自动引导进入主菜单

# 方式二：Windows 命令行一键静默打包（Windows64 / WebGL）
build.bat
```

## 目录结构

```text
NailoongAdventure/
├── Assets/NailoongAdventure/
│   ├── Scripts/                 # 过程化建模、战斗状态机、Boss AI、音频合成与 UI 系统
│   ├── Editor/GameBuilder.cs    # Windows64 与 WebGL 命令行构建入口
│   └── link.xml                 # 高强度 IL 裁剪保留规则
├── ProjectSettings/             # Unity 6.3 LTS 工程配置
├── build.bat                    # Windows 批处理一键打包脚本
├── CHANGELOG.md                 # 版本演进记录
└── CONTRIBUTING.md              # 贡献指南与代码规范
```

## 许可证

本项目代码基于 [MIT License](LICENSE) 开源，仅用于过程化游戏开发与技术教学演示。
