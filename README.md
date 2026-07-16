# 协调决策引擎 · 作品集站点

## 文件结构

```
site/
├── index.html                        控制台首页（入口，部署时保持此文件名不变）
├── modules/                          业务模块（决策引擎，接入统一升级仲裁收件箱）
│   ├── meeting-board.html                会议协调看板 v2
│   ├── leader-queue.html                 领导时间申请队列
│   ├── budget-ledger.html                经费管理台账
│   ├── mentor-onboarding.html            新员工与导师管理
│   ├── info-collection.html              信息收集与反馈看板（含培训课程反馈）
│   ├── schedule-management.html          经理日程管理
│   ├── birthday-care.html                员工生日关怀（轻量自动化模块）
│   └── training-knowledge.html           培训活动与知识管理（独立工具，不接入引擎）
├── hub/                               体系枢纽
│   └── escalation-inbox.html             统一升级仲裁收件箱（汇总以上 7 个引擎模块的升级事项）
├── diagrams/                          架构与流程图
│   ├── meeting-flow.svg                  会议协调决策流程图
│   └── engine-architecture.svg           六层引擎架构图
└── docs/
    └── case-study.md                     完整案例文档
```

> 注：`training-knowledge.html` 虽放在 `modules/` 目录下便于部署管理，但它是独立工具，
> 不产生升级仲裁事项、不接入 `escalation-inbox.html`。控制台首页中它被单独归入
> "独立工具" 分区，与其余 7 个决策引擎模块（归入"业务模块"分区）在视觉上区分。

## 部署方法

**Netlify**：将整个 `site` 文件夹拖拽上传到 https://app.netlify.com 即可，无需改动任何文件。

**GitHub Pages**：将 `site` 文件夹内的所有内容（不是 site 文件夹本身，是里面的内容）上传到仓库根目录，
在仓库 Settings → Pages 中开启 "Deploy from a branch"，分支选 main，目录选 / (root)。

## 后续新增模块

按同一套引擎接入新工作流时，建议：

1. 先判断新场景是否真的属于"资源分配/裁决冲突"类问题——如果不是（比如内容生产、纯记录归档类工作），
   参考 `training-knowledge.html` 的做法，做成独立工具，不必强行接入引擎；
2. 确认属于引擎范畴后，新原型文件放入 `modules/` 目录，命名用英文短横线命名（如 `expense-approval.html`）；
3. 新模块产生的升级事项，按统一的 Escalation Item 格式（`source_module` / `urgency` / `summary` /
   `requested_decision` / `candidates` / `deadline` / `resolution`）写入 `hub/escalation-inbox.html`
   的 `items` 数组，并在筛选按钮中加入对应的来源标签；
4. 在 `index.html` 的"业务模块"区块中加入新模块的卡片（`.card-wrap`，`draggable="true"`），
   序号会随拖拽自动重新计算，无需手动编号；
5. 如涉及新的架构图/流程图，放入 `diagrams/`；
6. **务必同步更新本 README 和 `docs/case-study.md`**——这两个文件不会自动更新，
   每次加新模块后需要手动补充说明（本次就是因为漏了这一步，导致 README 结构图长期没同步）。
