# Hi, I'm yyl 👋

**具身智能 / 机器人算法方向**。做的是从"合成数据 → 策略训练 → 判据化评测 → 真机部署"的完整闭环，
靠**可复现的数字**说话，而不是靠 demo 视频。

> 一句话：**ROS2 我会搭、IL 我做全套且把判据做对、RL 我做完了并诚实判负、VLA 我把语言真正接进了策略（到 one-hot 这一级）。**

---

## 🚀 主要项目

### [so-arm101-lang-act（python-for-mujoco-SDG）](https://github.com/yyl873/python-for-mujoco-SDG)
零 ROS 的纯 MuJoCo 仿真管线：真物理抓取 → 批量合成数据 → **语言条件 ACT** → **反事实配对评测** → 真机 ROS2 bringup。

| 成果 | 数字 |
|---|---|
| 语言条件策略（留出场景，76 rollout） | follow_acc **100%（40/40）**、配对全对 **15/38**、ITT **52.6%** |
| 反例：指令与场景共线的旧数据 | 落点 **1 箱A / 38 箱B**、配对全对 **0/38**（"语言未被使用"） |
| 真机 A/B（12 次/臂，只差"训练数据有没有仿真"） | 抓取 **1/12 → 9/12**，Fisher **p=0.0028** |
| RL：残差 SAC（3 奖励 × 3 seed） | 洁净口径 **26.7% → 13.3%**（判负，根因=奖励被钻空子） |

`MuJoCo` · `ACT / 行为克隆` · `语言条件` · `域随机化` · `lerobot 数据集` · `ROS2 / MoveIt2` · `统计判据`

### [embodied-eval-kit](https://github.com/yyl873/embodied-eval-kit)
具身策略评测的最小工具包（**零依赖**）：Wilson / Fisher / McNemar、洁净判据、反事实配对聚合、三态回执。
CI 全绿（3.10 / 3.12 / 3.13），数值能复算项目里的真实结论（`wilson(40,40)=0.9124`、`fisher=0.0028`）。

---

## 🧭 我关注的问题

- **怎么判断一个策略"真的行"**：预注册判据、区间估计、配对反事实、阴性对照、失败分类
- **仿真到真机**：仿真数据是"正则项"不是"数据量"（实测跨域轨迹差 25.8°）、接触真实性闸门
- **负结果也是结果**：宁可写清"它学会了压得更深"，也不报一个假的成功率提升

## 🛠 技能栈

`Python` · `PyTorch` · `MuJoCo` · `lerobot` · `ROS2 / MoveIt2 / ros2_control` · `URDF/xacro` ·
`Linux` · `Git` · `GitHub Actions` · `PyAV/OpenCV` · 统计检验（Wilson / 二项 / Fisher / McNemar）

<table>
<tr><td>实验设计与评测</td><td>★★★</td><td>仿真与物理</td><td>★★★</td><td>数据工程</td><td>★★★</td></tr>
<tr><td>ROS2 工程</td><td>★★☆</td><td>IL / ACT</td><td>★★☆</td><td>RL（SAC 残差）</td><td>★★☆</td></tr>
<tr><td>VLA / 语言条件</td><td>★★☆</td><td>部署加速</td><td>★☆☆</td><td></td><td></td></tr>
</table>


<sub>两个仓库都是可克隆可跑：主仓 `make check` / 主仓 `make tables` 能复算 README 里每一个数字；kit 仓 CI 每次推送自动跑测试。</sub>
