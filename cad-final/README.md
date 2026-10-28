# Balance Bot V6 — CAD 修改文件包

本目录包含 V6 设计的完整 CAD 文件，可直接导入 SolidWorks 编辑和装配。

原始 `.SLDPRT`/`.SLDASM` 文件在仓库根目录（未修改）。**STEP 文件可直接在 SolidWorks 中打开为可编辑实体**（文件 → 打开 → 选 .step → 导入为实体）。

## 目录结构

```
cad-final/
├── README.md                              ← 本文件
├── balance_bot_v6_assembly.step          ← ★ 完整装配体（16 个实体，直接打开即装配）
├── step_parts/                             ← ★ V6 新零件（STEP 格式，可编辑实体）
│   ├── pendulum_assembly.step            ← 重心摆总成（球头+杆+连接座+锚点+M3螺纹）
│   ├── ball_joint_base.step              ← 球铰底座（盖子上，M16 外螺纹凸台）
│   ├── ball_joint_cover.step             ← 球铰盖（M16 内螺纹，可拆卸，调预紧）
│   ├── steel_ball_d20.step               ← 钢球 Ø20mm（M3 贯通孔）
│   ├── base_weight.step                   ← 底部配重 Ø32×6mm
│   ├── guide_ring.step                    ← 防自转导环（含滑动槽）
│   ├── horn_L.step                        ← 左舵机臂（相位 15°）
│   ├── horn_R.step                        ← 右舵机臂（相位 150°）
│   └── link_L.stl / link_R.stl           ← 连杆（两端球铰）
├── parts/                                  ← STL/OBJ（3D 打印用，网格格式）
│   ├── pendulum_assembly.stl/.obj
│   ├── ball_joint_cover.stl/.obj
│   ├── steel_ball_d20.stl/.obj
│   ├── base_weight.stl
│   ├── link_L.stl / link_R.stl
│   └── horn_L.stl / horn_R.stl
├── original_parts/                         ← 原始零件网格（从 SLDPRT 提取）
│   ├── shell.stl                          ← 外壳半球
│   ├── lid.stl                            ← 盖子
│   ├── servo.stl                          ← SG90
│   ├── servo_arm.stl                      ← 原舵机臂
│   ├── link_l.stl / link_r.stl           ← 原连杆
│   └── assembly_original.obj             ← 原装配体
└── assembly/
    └── balance_bot_assembly.stl           ← 整机装配（STL 格式，查看用）
```

## 在 SolidWorks 中使用

### 打开完整装配
1. SolidWorks → 文件 → 打开 → 选 `balance_bot_v6_assembly.step`
2. 导入选项选 **"导入为实体"**（不是曲面）
3. 得到包含 16 个实体的装配体，可直接测量、修改

### 编辑单个零件
1. 打开 `step_parts/xxx.step` 为新零件
2. 可直接加特征（打孔、切割、圆角）
3. 另存为 `.SLDPRT` 加入自己的工程

### 3D 打印
用 `parts/` 下的 STL 文件直接切片打印。

## V6 设计变更汇总

| # | 变更 | 涉及零件 |
|---|---|---|
| 1 | 新增重心摆总成 | `pendulum_assembly.step` |
| 2 | 新增球铰底座+可拆盖 | `ball_joint_base.step` + `ball_joint_cover.step` |
| 3 | 新增钢球 Ø20mm | `steel_ball_d20.step` |
| 4 | 新增底部配重 | `base_weight.step` |
| 5 | 新增防自转导环 | `guide_ring.step` |
| 6 | 右舵机自旋 180° | 装配体中 `servo_right_rotated_180` |
| 7 | 舵机臂更新 | `horn_L.step`(15°) / `horn_R.step`(150°) |
| 8 | 连杆更新 | `link_L.step` / `link_R.step`（V6 尺寸） |

## 关键尺寸表

| 零件 | 关键尺寸 |
|---|---|
| 外壳 | 半球 R50 外 / R48 内，壁厚 2mm |
| 盖子 | Ø95×2mm 平板 |
| 底部配重 | Ø32×6mm，40g（钢/环氧） |
| 球铰底座 | M16×1 外螺纹，总高 5.5mm |
| 球铰盖 | M16×1 内螺纹，总高 5mm，旋入调预紧 |
| 球头 | Ø8mm，球心高出盖面 6mm |
| 摆杆 | Ø3.6mm，球心到钢球中心 36mm |
| 连接座 | 22×22×6mm，距球心 22mm |
| 锚点 | 半径 10mm，方位角 200°/320°，球头 Ø6mm |
| 舵机臂 | 有效半径 15mm，左相位 15°/右相位 150° |
| 连杆 | 两端球铰 Ø5.6mm，长约 19mm |
| 钢球 | Ø20mm，M3×0.5 贯通孔，33.3g |
| 防自转导环 | Ø56×3mm 环，径向滑槽宽 3.2mm |
| 总重 | ~105g |

## 螺纹规格

| 位置 | 规格 | 安装方式 |
|---|---|---|
| 球铰盖 ↔ 底座 | M16×1.0 | 旋入，深度调预紧，加螺纹胶防松 |
| 钢球 ↔ 摆杆 | M3×0.5 | 拧入贯通孔，两端加螺母+螺纹胶 |
| 舵机 ↔ 盖子 | ST2.9 自攻丝 | 4×M2 自攻螺钉 |
| 配重 ↔ 壳体 | — | 环氧AB胶粘接 |

## 装配步骤

1. 底部配重粘入壳体内部最低点
2. 球铰底座安装到盖子中心（胶接或从下方螺母紧固）
3. 左右舵机用自攻丝固定到盖子上方（注意右舵机自旋 180°）
4. 舵机臂装入舵机输出轴（相位：左 15°、右 150°）
5. **旋下球铰盖**，将重心摆球头压入球窝
6. **旋上球铰盖**，调节预紧（手感：能自由摆动但不旷）
7. 钢球拧到摆杆底部 M3 螺纹（加螺纹胶+锁紧螺母）
8. 连杆连接舵机臂球头和摆杆锚点球头
9. 整体装入壳体，盖上盖子
