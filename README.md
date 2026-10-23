# haowenz001/test-demo 单仓看板

这个仓库由控制面自动生成，用来展示 [haowenz001/test-demo](https://github.com/haowenz001/test-demo) 的门禁、PR、Issue 与每日构建状态。

| 用途 | 链接 |
| --- | --- |
| 看板站点 | https://haowenz001.github.io/test-demo-board/ |
| 数据快照 | https://haowenz001.github.io/test-demo-board/data/snapshot.json |
| 源码仓库 | https://github.com/haowenz001/test-demo |

## 数据怎么来

- `board-config.json` 里的 `deployments` 指向源码仓库，采集时按它读取 PR、Issue 和 workflow 运行。
- 定时任务每天 10:17（Asia/Shanghai，UTC 02:17）跑一次；也可以在 Actions 里手动触发 **Collect dashboard data (PAT)**。
- 采集结果写回 `site/`，再由 **Deploy dashboard Pages** 发布到上面的站点。
- 门禁报告来自源码仓库的 `CI` workflow（`scripts/gate/gate.mjs`），以及 build / nightly / e2e / release 各 lane。

## 本地预览

```bash
python3 -m http.server 8000 --directory site
```

看板是 public 的：源码仓必须公开，私有仓库只在本地/内网运行，不要发布到公开 Pages。

## 配置

- 默认分支：`main`
- 归属：`haowenz001`
- 修改 `board-config.json` 里的 `label`、`stale_days`、`branch_lines` 就能调整展示口径，不要删掉 `deployments`。
