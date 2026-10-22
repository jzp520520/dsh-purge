# 本 Fork 说明 / Fork Notice

本仓库是 **[jzp520520/dsh-purge](https://github.com/jzp520520/dsh-purge)**，
fork 自 **[mmparko/dsh-purge](https://github.com/mmparko/dsh-purge)**（上游原项目
[YuJunZhiXue/dsh-purge](https://github.com/YuJunZhiXue/dsh-purge) 的**全量镜像**）。

> 原仓库 `YuJunZhiXue/dsh-purge` 已于 **2026-10-21 下架（HTTP 404）**。
> 本 fork 是下架前完整快照的直接副本，用于自用存档与安装。

---

## 一、署名 / Attribution（MIT 要求，原样保留）

| 项 | 内容 |
| --- | --- |
| 原项目 | **dsh-purge — DeepSeek Harness 破甲** |
| 原作者 | **YuJunZhiXue**（[@YuJunZhiXue](https://github.com/YuJunZhiXue)） |
| 原仓库 | <https://github.com/YuJunZhiXue/dsh-purge>（已 404） |
| 镜像者 | [@mmparko](https://github.com/mmparko) — 全量镜像，含 26 个 PR ref 转 tag |
| 原许可证 | MIT（`LICENSE` 原样保留，未做任何改动） |

本项目的名称、思路、代码、提示词的一切权利与署名均归原作者。
本 fork 不主张任何原创性，只做存档与自用安装。

---

## 二、快照内容

| 项目 | 内容 |
| --- | --- |
| `master` | 上游 `6c1d638` + 镜像者两条 docs commit + 本 fork 的 3 条自持 commit |
| 分支 | `master`、`fix/restart-sticky`、`upstream-archive` |
| Tag | **100 个**：`v1.1.1` – `v1.1.71`（含 `-beta.N`）+ 26 个 `archive/pr-*-{head,merge}` + `upstream-snapshot-6c1d638` |
| 提交数 | 395+ |
| Issue/PR 存档 | `upstream-archive` 分支：91 issue + 24 PR + 135 条评论的完整 JSON |

核验方式：

```bash
git clone https://github.com/jzp520520/dsh-purge.git
cd dsh-purge
git tag | wc -l          # 100
git branch -a             # master / fix/restart-sticky / upstream-archive
git log --oneline -3
```

---

## 三、本 fork 相对镜像源的改动（仅 3 处，全部为"更新源自持"）

上游删库后，`lib/update.js` 里硬编码的 `REPO = "YuJunZhiXue/dsh-purge"`
会让插件自更新永久 404。本 fork 把更新源指回自己：

| 文件 | 改动 |
| --- | --- |
| `lib/update.js` | `REPO` → `jzp520520/dsh-purge`；新增 `UPSTREAM_REPO` 常量作原文保留 |
| `package.json` | `repository` / `homepage` / `bugs` / `dsh.install.{tarball,zip,git}` → 本 fork；新增 `upstreamRepository` 记录原始地址 |
| `lib/redteam/ui.js` | `githubRepoOf()` 的兜底返回值 → 本 fork |

**业务代码、提示词、补丁逻辑、redteam 预设一个字节都没动。**

---

## 四、安装 / 升级

```bash
# 方式 A：git 装（推荐，能自更新）
git clone https://github.com/jzp520520/dsh-purge.git "$env:USERPROFILE\.dsh\plugins\dsh-purge"

# 方式 B：tarball
dsh plugin --profile desktop add https://github.com/jzp520520/dsh-purge/archive/refs/heads/master.tar.gz
```

版本对照：

| 本地已装 | 上游最后版本 | 差距 |
| --- | --- | --- |
| 1.1.69（sha `e581245`，2026-10-11） | **1.1.71**（sha `5e75726`，2026-10-13） | 12 commits，21 文件，+999 / −777 行 |

`v1.1.69 → v1.1.71` 主要修复：`#86 steer` 误伤、升级自锁、启用失败、asar 解包、identity 重写。

---

## 五、与上游的差异声明

上游 README 在备份时已写明：**项目暂停更新**，作者因工作安排暂停维护、不再发版、
暂不收 issue / PR。该状态与「违规商用公示」章节一并完整保留在
`README.md` / `README.zh-CN.md` 中，本 fork 不修改其中任何字符。

全部权利归原作者 YuJunZhiXue。原项目的非盈利条款同样沿用：
**不得用于卖课、卖插件、卖 token、倒卖等收费行为。**
