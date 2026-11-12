# 瞎jb系列 · 两个 48 周训练器

**48 周 × 每天 30 分钟，零基础，一个人也能练下去。**
两个单文件网页应用：**瞎jb画**（人物画）和**瞎jb唱**（唱歌）。打开就用，不用注册、不用安装、不联网也能练，记录只存在你自己的浏览器里。

<p align="center">
  <img src="docs/draw-today.png" width="49%" alt="瞎jb画 · 今日练习">
  <img src="docs/sing-today.png" width="49%" alt="瞎jb唱 · 今日练习">
</p>

**中文** | [English](README.en.md)

[![单文件](https://img.shields.io/badge/单文件-离线可用-1F6F6A)](#)
[![无依赖](https://img.shields.io/badge/依赖-零-1F6F6A)](#)
[![数据](https://img.shields.io/badge/记录-只存本机-B5651D)](#数据与备份)

| 应用 | 练什么 | 直接打开 |
| --- | --- | --- |
| **瞎jb画** | 48 周人物画：线条、结构、人体、表情、场景，最后能画一张有情绪的画 | **[draw.html](https://qxs9678.github.io/0033/draw.html)** |
| **瞎jb唱** | 48 周唱歌：呼吸、发声、音准、咬字、表达，录音回听 | **[sing.html](https://qxs9678.github.io/0033/sing.html)** |

---

## 它解决什么问题

零基础的人不缺教程，缺的是「今天练什么、练多久、练完算不算过」。这两个应用把 336 天切成每周 7 天、每天 30 分钟的三段：热身 → 主课 → 复盘。每天打开只有一件事要做，做完打勾，进度条会自己往前走。

- **每天 30 分钟**：5′ 热身 + 20′ 主课 + 5′ 复盘，计时器内置，另有速写/节拍器模式。
- **每周一个目标**：48 周分三阶段（基础 → 人体/声音 → 表达），每 4 周一个交付日。
- **参考拆解**：画的部分内置参考搜索词和拆解台，可以叠参考、看局部、切三值。
- **作品墙**：只存 12 个交付日的照片，不逼你每天拍。
- **数据只在本机**：`localStorage` + `IndexedDB`，没有账号、没有服务器，导出一个 JSON 就是全部备份。

<p align="center">
  <img src="docs/draw-overview.png" width="49%" alt="48 周总览">
  <img src="docs/draw-ref.png" width="49%" alt="速查手册">
</p>

## 怎么开始

1. 打开 [draw.html](https://qxs9678.github.io/0033/draw.html) 或 [sing.html](https://qxs9678.github.io/0033/sing.html)。
2. 点「开始画 / 开始练」，跟着当天的参考做 30 分钟。
3. 做完打勾；每周第 7 天写复盘。
4. 手机浏览器「添加到主屏幕」，当 App 用。

> 也可以把仓库里的 `draw.html` / `sing.html` 下载到本地双击打开，完全离线。
> 但 `file://` 和线上 `https://` 是两份独立的数据，选一个入口后别换。
> 录音、校音需要 HTTPS（Pages 自带）；局域网 http 或本地 `file://` 拿不到麦克风。

## 数据与备份

两个应用的数据格式不同，**不能互相导入**。

**瞎jb画**

- 打卡、日期、笔记、复盘、状态、关口、参考链接：`localStorage`（`drawplan:*`）
- 作品照片：`IndexedDB`（`drawplan-works`），压缩后的 JPEG
- 备份：页面内「导出记录」→ 一个 JSON，记录和作品都在里面；换设备用「导入记录」恢复
- 每 4 周一个交付日，作品墙只存 12 个交付日的照片（约 1–2 MB）

**瞎jb唱**

- 打卡、笔记、复盘、练习卡、歌词、设置：`localStorage`（`singplan48:*`）
- 录音：`IndexedDB`（`singplan48` / 表 `takes`）
- 备份：页面内「备份」→ 含录音的 zip；换设备用同一入口恢复

## 换网址 = 换数据

浏览器的本地数据按**网址（源）**隔离：

- 本地 `file://` 打开、GitHub Pages 的 `https://` 打开，是两份独立数据；
- 换 Pages 地址、换域名，旧记录不会自动出现；
- 同一域名下换路径（例如 `/0033/` → `/0033/sing.html`）不算换源，记录照旧；
- 迁移方式只有一种：在旧地址「导出」，到新地址「导入」。

所以不要把同一个人的记录一半放 `file://`、一半放 Pages；确定一个入口后一直用它，并定期导出。

## 源码

成品 HTML 由工作区里的 Python 脚本生成（`build_draw_tracker.py` / `build_v3.py`），仓库里只放构建后的单文件成品。模板、课程数据、构建脚本不随仓库发布。

## 说明

- 唱歌的曲目只作为练功素材，不内置歌词（版权原因，由使用者自行粘贴）。
- 绘画的参考搜索词是英文，Pinterest / Google 图片需要联网；页面本身离线可用。
- 更新记录见 [CHANGELOG.md](CHANGELOG.md)。

## License

[MIT](LICENSE)
