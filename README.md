# FanHub · 桌面版

私域粉丝进度管理工具（Windows 桌面版）。和「拉群小助手」是**两份互不影响的独立工具**，可以同时装在电脑上。

## 下载

- **下载页**：https://cvrtgbp2dn-code.github.io/fanhub/
- **所有版本**：https://github.com/cvrtgbp2dn-code/fanhub/releases
- **云端名单库**：https://github.com/cvrtgbp2dn-code/fanhub-roster

## 自动更新

程序本体是一个 HTML 文件，**首次安装后不需要再下安装包**：

- 每次启动会静默检查 `app/version.json`
- 有新版就自动下载 `app/index.html`（约 290 KB，秒完成）并替换本地缓存
- 断网时用本地缓存，不影响使用

> 所以以后升级工具，只需要替换 `app/index.html` + 改一下 `app/version.json` 的版本号。

## 目录

| 路径 | 说明 |
|---|---|
| `index.html` | 下载页 |
| `app/index.html` | 程序本体（自动更新的目标） |
| `app/version.json` | 版本号，用来比对是否需要更新 |
| `app/icon-*.png` `app/icon.ico` | 图标 |

## 数据

全部数据存在用户本机（Electron 的 localStorage / IndexedDB），不上传任何服务器。
换电脑用「数据备份 → 导出/恢复」。

存储键名一律以 `fanhub_` 开头（老工具是 `lq_helper_`），IndexedDB 库名 `fanhub_roster` ——
**两边完全隔离，同一个浏览器里也不会互相抢数据**。

## 名单库留空时是什么行为

云端名单库还没上传东西时，客户端 `rosterActive()` 会是 false → **一律视为「在库」**，
不会把所有数据标成「不在库」。把 CSV 传到 `fanhub-roster` 的 `source/` 后自动生效。
