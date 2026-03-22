- 👋 Hi, I'm @Hanlb88888
- 👀 I'm interested in Betaflight, FPV drones, and flight controller firmware
- 🌱 I'm currently learning Betaflight firmware development and PID tuning
- 💞️ I'm looking to collaborate on open-source flight controller projects
- 📫 How to reach me: via GitHub Issues or Discussions
- 😄 Pronouns: He/Him
- ⚡ Fun fact: Betaflight powers thousands of FPV racing drones worldwide!

---

# 🚁 关于 Betaflight 的 GitHub 研究专题总结
*Betaflight Research Topics on GitHub — A Comprehensive Guide*

> Betaflight 是目前最流行的开源无人机飞控固件之一，广泛应用于 FPV 竞速、自由飞和多旋翼无人机领域。以下是 GitHub 上最多、最全的 Betaflight 相关研究专题整理。

---

## 📌 一、官方核心仓库（必读）

| 仓库 | 描述 | Stars |
|------|------|-------|
| [betaflight/betaflight](https://github.com/betaflight/betaflight) | 🏆 官方飞控固件（C语言），核心代码库，包含 PID、滤波、调度、传感器融合等所有模块 | ⭐ 10k+（持续增长）|
| [betaflight/betaflight-configurator](https://github.com/betaflight/betaflight-configurator) | 跨平台图形化配置工具（Vue.js），用于配置和管理 Betaflight 固件 | ⭐ 3k+ |
| [betaflight/blackbox-log-viewer](https://github.com/betaflight/blackbox-log-viewer) | 黑盒飞行日志可视化分析工具（JavaScript），用于调参和故障排查 | ⭐ 400+ |
| [betaflight/betaflight-tx-lua-scripts](https://github.com/betaflight/betaflight-tx-lua-scripts) | OpenTX/EdgeTX 遥控器端 Lua 脚本，支持从遥控器直接配置飞控 | ⭐ 600+ |
| [betaflight/firmware-presets](https://github.com/betaflight/firmware-presets) | 官方飞控配置预设片段库，社区贡献的调参方案集合 | ⭐ 100+ |

---

## 📌 二、主要研究专题

### 🔧 1. 固件架构与代码分析

Betaflight 固件基于 **Cleanflight** 演进而来，核心研究方向包括：

- **实时调度系统（RTOS-like Scheduler）**：基于优先级的任务调度机制，保证姿态控制循环的低延迟
- **PID 控制器**：包括 P/I/D 三项增益、Anti-windup、TPA（油门 PID 衰减）
- **陀螺仪数据处理**：IMU 数据读取、滤波（Gyro/D-term RPM Filter、Notch Filter）
- **电调协议**：DShot（150/300/600/1200）、OneShot、MultiShot、Brushed
- **传感器融合**：加速度计辅助姿态估算、气压计、GPS

**相关仓库：**
- [cleanflight/cleanflight](https://github.com/cleanflight/cleanflight) — Betaflight 的前身，理解历史演进的必读仓库 ⭐ 2.7k+（2025年数据）

---

### 📊 2. 黑盒日志分析与 PID 调参工具

| 仓库 | 描述 |
|------|------|
| [Plasmatree/PID-Analyzer](https://github.com/Plasmatree/PID-Analyzer) | 经典 Python PID 分析工具，从黑盒日志提取频率响应并可视化 ⭐ 400+ |
| [stefapi/PID_tune](https://github.com/stefapi/PID_tune) | 支持 Betaflight/INAV 日志的 PID 调参辅助工具 |
| [chugzb/betaflight-pid-autotuning](https://github.com/chugzb/betaflight-pid-autotuning) | 基于黑盒日志的自动 PID 调参工具（含神经网络方案） |

---

### 🤖 3. 仿真与强化学习

| 仓库 | 描述 |
|------|------|
| [utiasDSL/gym-pybullet-drones](https://github.com/utiasDSL/gym-pybullet-drones) | PyBullet 多旋翼强化学习仿真环境，支持 Betaflight 控制算法研究 ⭐ 1.9k+ |
| [rubenCodeforges/ardudeck](https://github.com/rubenCodeforges/ardudeck) | 一体化 GCS，支持 ArduPilot/Betaflight/iNav，含 SITL 仿真 |

---

### 🛠️ 4. 硬件支持与飞控板开发

- **STM32 系列深度优化**：F4/F7/H7 系列 MCU 的固件适配与目标定义
- **自定义飞控板移植**：[ShanGlor/INAV-Blackpill-Flight-Controller](https://github.com/ShanGlor/INAV-Blackpill-Flight-Controller) — STM32F411 黑药丸飞控移植
- **OSD（屏幕显示系统）**：[ShikOfTheRa/scarab-osd](https://github.com/ShikOfTheRa/scarab-osd) — 支持多种飞控的 OSD 固件 ⭐ 400+

---

### 📡 5. 通信协议与外设集成

- **MSP 协议（MultiWii Serial Protocol）**：飞控与配置器/地面站通信核心协议
- **CRSF/ELRS 接收机支持**：ExpressLRS 低延迟遥控协议集成
- **DJI 数字图传集成**：DJI FPV 系统与 Betaflight 的对接方案
- **GPS 救援（GPS Rescue）**：失控返航功能的算法实现

---

### 🧠 6. AI / 机器学习在飞控中的应用

- 基于黑盒数据的 **PID 自动调参**（神经网络方案）
- **强化学习**飞控策略训练（结合 gym-pybullet-drones）
- 飞行数据异常检测与故障预测

---

## 📌 三、学习路线建议

```
入门阶段
  └─ 了解 Betaflight 固件功能与配置工具使用
  └─ 学习 FPV 基础硬件组装与调参

进阶阶段
  └─ 阅读 betaflight/betaflight 源码（从 src/main/fc/ 开始）
  └─ 使用 PID-Analyzer 分析黑盒日志，理解频率响应
  └─ 研究 DShot 协议与电调通信原理

深入研究
  └─ 修改/移植固件到自定义飞控板
  └─ 研究 RPM 滤波、动态 Notch 等高级滤波算法
  └─ 基于仿真平台（gym-pybullet-drones）做控制算法研究
```

---

## 📌 四、社区资源

- 🌐 **官方网站**：[betaflight.com](https://betaflight.com)
- 💬 **官方 Discord**：Betaflight 官方 Discord 服务器（活跃开发者社区）
- 📖 **官方文档**：[Betaflight Wiki](https://betaflight.com/docs/wiki)
- 🐛 **Issue 追踪**：[GitHub Issues](https://github.com/betaflight/betaflight/issues)
- 🔖 **最新版本**：[Releases](https://github.com/betaflight/betaflight/releases)（跟踪最新固件发布）

---

> 📝 **总结**：GitHub 上关于 Betaflight 最全面的研究专题涵盖 **固件架构分析**、**PID 调参工具**、**黑盒日志可视化**、**硬件移植**、**仿真与 AI 控制** 五大方向。官方仓库 `betaflight/betaflight`（Stars 数量持续增长）是最核心的研究入口，结合 `PID-Analyzer`、`gym-pybullet-drones` 等工具可以完成从实飞调参到仿真研究的完整链路。

<!---
Hanlb88888/Hanlb88888 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
