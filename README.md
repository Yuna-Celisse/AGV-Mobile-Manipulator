# AGV-Mobile-Manipulator

基于 **ROS 2 与 STM32F407VGT6** 的移动操作机器人毕业设计工程，规划采用四轮麦克纳姆底盘、Z 轴垂直升降、X 轴水平伸缩及末端夹爪，实现移动导航与取放作业。

> 当前阶段：工程目录初始化。仓库已建立资料、硬件、软件、仿真、实验、文档与论文目录，尚未包含可编译的 STM32 工程、可运行的 ROS 2 软件包或经过验证的机器人实现。

## 设计目标与职责划分

- **底盘**：全向移动、轮速闭环、编码器采集与里程计。
- **取放机构**：X/Z 双轴运动、回零、限位与夹爪动作。
- **STM32**：规划承担底层实时控制、状态采集、故障处理及上位机通信。
- **ROS 2 上位机**：规划承担机器人描述、定位导航、感知、任务调度和协同控制。
- **实验与论文**：保存原始数据、处理脚本、参数、结果图表与设计决策，形成可追溯的毕业设计记录。

ROS 2/Ubuntu 版本、通信方式、引脚分配、电机与驱动器型号、机械尺寸和性能指标均待选型与验证。

## 工程目录

```text
AGV-Mobile-Manipulator/
├── 00.References/
│   ├── Datasheets/
│   ├── Standards/
│   ├── Papers/
│   ├── ROS2-Docs/
│   └── Research-Notes/
├── 01.Hardware/
│   ├── Mechanical/
│   │   ├── Chassis/
│   │   ├── Z-Axis/
│   │   ├── X-Axis/
│   │   ├── Gripper/
│   │   ├── Assembly/
│   │   ├── Drawings/
│   │   └── Calculations/
│   ├── Electronics/
│   │   ├── STM32-Controller/
│   │   ├── Motor-Drivers/
│   │   ├── Linear-Actuators/
│   │   ├── Power-System/
│   │   ├── Safety-Circuit/
│   │   └── Wiring/
│   └── BOM/
├── 02.Software/
│   ├── Firmware/STM32F407/
│   │   ├── Core/
│   │   ├── Drivers/
│   │   ├── Middlewares/
│   │   └── App/
│   │       ├── Motor/
│   │       ├── Encoder/
│   │       ├── Kinematics/
│   │       ├── Odometry/
│   │       ├── LinearAxis/
│   │       ├── Safety/
│   │       └── Protocol/
│   ├── ROS2/agv_ws/src/
│   │   ├── agv_description/
│   │   ├── agv_bringup/
│   │   ├── agv_hardware/
│   │   ├── agv_control/
│   │   ├── agv_navigation/
│   │   ├── agv_localization/
│   │   ├── agv_manipulator/
│   │   ├── agv_perception/
│   │   ├── agv_interfaces/
│   │   └── agv_task_manager/
│   ├── Algorithms/
│   │   ├── Kinematics/
│   │   ├── Cooperative-Control/
│   │   ├── Visual-Servoing/
│   │   └── Trajectory-Planning/
│   └── Tools/
│       ├── Calibration/
│       ├── Serial-Debug/
│       └── Data-Analysis/
├── 03.Simulation/
│   ├── Gazebo/
│   │   ├── Worlds/
│   │   └── Models/
│   ├── MATLAB/
│   └── Experiments/
├── 04.Tests/
│   ├── Motor-PID/
│   ├── Chassis-Odometry/
│   ├── Navigation/
│   ├── Linear-Axis/
│   ├── Cooperative-Control/
│   ├── Pick-and-Place/
│   └── Datasets/
├── 05.Documents/
│   ├── Requirements/
│   ├── Architecture/
│   ├── Interface-Specifications/
│   ├── Design-Decisions/
│   ├── Development-Logs/
│   └── User-Manual/
├── 06.Thesis/
│   ├── Proposal/
│   ├── Literature-Review/
│   ├── Thesis-Draft/
│   ├── Figures/
│   ├── References/
│   └── Defense/
├── 07.Project-Management/
│   ├── Milestones/
│   ├── Tasks/
│   └── Budget/
├── README.md
├── .gitignore
└── LICENSE
```

空目录通过 `.gitkeep` 纳入 Git，加入实际内容后可删除对应占位文件。`STM32F407.ioc` 应在明确芯片、时钟、引脚和外设配置后由 STM32CubeMX 生成，因此初始化阶段不创建空白 `.ioc` 文件。

## 目录使用约定

| 目录 | 内容与组织方式 |
| --- | --- |
| `00.References` | 手册、标准索引、论文及阅读笔记；记录来源、版本与访问日期，仅提交允许再分发的资料 |
| `01.Hardware` | 机械与电气设计源文件、工程图、计算、线束及 BOM；源文件与导出交付文件分开保存 |
| `02.Software` | STM32 固件、ROS 2 工作空间、算法研究与调试工具 |
| `03.Simulation` | Gazebo 场景与模型、MATLAB 模型、仿真配置和结果 |
| `04.Tests` | 实验方案、原始数据、处理结果与复现说明；每次实验记录日期、软硬件版本和参数 |
| `05.Documents` | 需求、系统架构、接口协议、设计决策、开发日志和操作手册 |
| `06.Thesis` | 开题、文献综述、论文草稿、插图、参考文献与答辩材料 |
| `07.Project-Management` | 里程碑、任务跟踪、采购预算与实际支出 |

## ROS 2 模块规划

以下目录目前只是占位，尚未生成 `package.xml`、构建配置或节点。

| 软件包 | 规划职责 |
| --- | --- |
| `agv_description` | URDF/Xacro、连杆关节、可视化与碰撞模型 |
| `agv_bringup` | 系统启动入口与统一配置 |
| `agv_hardware` | STM32 通信与硬件接口适配 |
| `agv_control` | 底盘、双轴机构控制配置 |
| `agv_navigation` | 导航参数、地图与导航启动 |
| `agv_localization` | 编码器、IMU 等定位信息融合 |
| `agv_manipulator` | X/Z 双轴与夹爪控制 |
| `agv_perception` | 目标识别、视觉测量与感知处理 |
| `agv_interfaces` | 公共消息、服务和动作定义 |
| `agv_task_manager` | 导航与取放任务状态机 |

## 开发起点

1. 在 `05.Documents/Requirements/` 明确载荷、速度、行程、定位精度与取放流程。
2. 在 `05.Documents/Architecture/` 确定系统架构、软件版本与硬件选型。
3. 在 `05.Documents/Interface-Specifications/` 定义引脚映射、通信帧、单位、坐标系、超时和故障状态。
4. 使用 STM32CubeMX 生成 `02.Software/Firmware/STM32F407/STM32F407.ioc` 及底层工程，将自定义逻辑放入 `App/`；生成文件中的调用保留在 USER CODE 区域。
5. 在指定 ROS 2 环境下逐个创建软件包，补齐依赖、构建配置、启动文件和模块说明后再构建运行。
6. 从轮速闭环、底盘里程计和双轴回零验证开始，逐步开展导航与整机取放实验。

## 版本管理

- 提交设计源文件、必要配置、文档和可复现实验的小型数据；构建产物、缓存、临时文件和凭据由 `.gitignore` 排除。
- 大型 CAD、视频、rosbag 和数据集按需使用 Git LFS 或外部存储，在对应目录记录获取方式及版本。
- 在 `05.Documents/Design-Decisions/` 记录重要选型理由，在 `Development-Logs/` 记录开发与验证结果。
- 第三方驱动、库、模型与参考资料保留各自许可证和版权声明。

## 参考与许可

目录规划参考用户提供的[项目讨论](https://chatgpt.com/share/6ae9cfac-beb0-83ee-a9de-f1212176ca9d)，具体方案以后续设计文档和实验验证为准。

本项目采用 [Apache License 2.0](LICENSE)。第三方材料遵循其各自许可。
