# 协调决策引擎 · 作品集站点

## 文件结构

```
site/
├── index.html              控制台首页（入口，部署时保持此文件名不变）
├── modules/                 业务模块
│   ├── meeting-board.html       场景一：会议协调看板 v2
│   └── leader-queue.html        场景二：领导时间申请队列
├── hub/                      体系枢纽
│   └── escalation-inbox.html    统一升级仲裁收件箱
├── diagrams/                 架构与流程图
│   ├── meeting-flow.svg          会议协调决策流程图
│   └── engine-architecture.svg   六层引擎架构图
└── docs/
    └── case-study.md          完整案例文档
```

## 部署方法

**Netlify**：将整个 `site` 文件夹拖拽上传到 https://app.netlify.com 即可，无需改动任何文件。

**GitHub Pages**：将 `site` 文件夹内的所有内容（不是 site 文件夹本身，是里面的内容）上传到仓库根目录，
在仓库 Settings → Pages 中开启 "Deploy from a branch"，分支选 main，目录选 / (root)。

## 后续新增模块

按同一套引擎接入新工作流时，建议：

1. 新原型文件放入 `modules/` 目录，命名建议用英文短横线命名（如 `expense-approval.html`）；
2. 如涉及新的架构图/流程图，放入 `diagrams/`；
3. 案例文档更新写入 `docs/case-study.md`，或按模块拆分为 `docs/模块名.md`；
4. 在 `index.html` 的"业务模块"区块中，把原来的"待接入"占位卡替换为新模块的链接卡片。
