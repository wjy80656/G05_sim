# GalaxeaVLA G0.5 模型仿真复现与 LIBERO 任务验证

本项目用于记录基于 **OpenGalaxea GalaxeaVLA G0.5 视觉语言动作模型（Vision-Language-Action Model）** 的仿真复现实验过程。

项目基于官方 GalaxeaVLA 实现，在 **LIBERO 机器人操作仿真环境** 中完成 G0.5 模型部署、推理验证以及任务 Rollout 测试，并保存实验过程截图、运行日志和结果文件。

项目目标：

- 完成 G0.5 模型环境部署
- 加载官方预训练权重
- 在 LIBERO 仿真环境执行机器人操作任务
- 验证模型视觉语言动作推理能力
- 记录 Rollout 运行过程和实验结果


---

## 1. 项目来源

官方项目：

- GalaxeaVLA:
  https://github.com/OpenGalaxea/GalaxeaVLA

仿真环境：

- LIBERO Robot Manipulation Benchmark


---

## 2. 实验环境

### 硬件环境

| 项目 | 配置 |
| --- | --- |
| 计算平台 | NVIDIA GPU 云服务器 |
| GPU | NVIDIA GeForce RTX 4090 |
| 显存 | 24GB |
| CPU | Intel Xeon Platinum 8358P |
| CPU线程数 | 128 |

### 软件环境

| 项目 | 配置 |
| --- | --- |
| 操作系统 | Ubuntu 24.04.1 LTS |
| Python | 3.10.16 |
| PyTorch | 2.7.1+cu128 |
| CUDA | 12.8 |
| 模型框架 | GalaxeaVLA |
| 模型版本 | G0.5 |
| 仿真平台 | LIBERO |


---

## 3. 实验任务

本实验采用 LIBERO 仿真环境中的 `libero_goal` 任务套件进行验证。

实验配置：


任务套件：
libero_goal

机器人类型：
libero simulated robot

任务数量：
10

每任务测试次数：
1

并行推理数量：
5



测试任务包括：

- 打开柜子抽屉
- 放置物体到指定位置
- 厨房环境交互任务
- 物体抓取与组合操作


示例任务：


open the middle drawer of the cabinet

put the bowl on the stove

put the cream cheese in the bowl

turn on the stove



---

## 4. 模型推理流程

G0.5 根据视觉观测和自然语言任务指令生成机器人动作，实现闭环控制。


整体流程：


视觉观测 RGB Image
|
v
GalaxeaVLA G0.5 模型
|
v
动作序列预测
|
v
机器人控制执行
|
v
LIBERO 仿真环境反馈
|
v
下一步推理



---

## 5. 实验结果

本次实验完成 G0.5 在 LIBERO 环境中的 Rollout 验证。


实验结果：


任务套件：
libero_goal

测试任务数量：
10

总推理次数：
300

总成功次数：
29



详细结果文件：


results/
├── libero_goal_result.json
└── evaluation_summary.md



---


模型代码和预训练权重来源于 OpenGalaxea 官方项目。

感谢 OpenGalaxea 团队开源 GalaxeaVLA，以及 LIBERO 项目提供机器人操作仿真基准。
