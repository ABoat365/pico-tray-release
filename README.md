# PicoTray

**[简体中文](#简体中文) · [English](#english)**

[![release](https://img.shields.io/github/v/release/ABoat365/pico-tray-release?display_name=tag&style=flat-square)](https://github.com/ABoat365/pico-tray-release/releases/latest) [![GitHub downloads](https://img.shields.io/github/downloads/ABoat365/pico-tray-release/total?label=GitHub%20downloads&style=flat-square)](https://github.com/ABoat365/pico-tray-release/releases) [![latest release](https://img.shields.io/github/downloads/ABoat365/pico-tray-release/latest/total?label=latest%20release&style=flat-square)](https://github.com/ABoat365/pico-tray-release/releases/latest)  
[![platform](https://img.shields.io/badge/platform-Windows%2010%201809%2B%20%7C%2011-0078D4?style=flat-square&logo=windows11&logoColor=white)](https://github.com/ABoat365/pico-tray-release/releases/latest) [![license](https://img.shields.io/badge/license-proprietary-lightgrey?style=flat-square)](LICENSE)

Windows 任务栏上的网速 / CPU / 内存监视器，外加屏幕亮度调节、「端口 → 进程」速查和「磁盘禁用 / 启用」开关。
A tiny Windows taskbar monitor for network speed, CPU and memory — plus brightness control, a port-to-process lookup and a one-click disk disable / enable switch.

> 本仓库**只放安装包和 `version.json`**，源码不公开。
> This repository holds **only installers and `version.json`**; the source code is not public.

> 日本語 UI に対応しています。詳しくは [English](#english) をご覧ください。  
> 한국어 UI를 지원합니다. 자세한 내용은 [English](#english)에서 확인하세요.

---

## 简体中文

### 这是什么

在任务栏通知区左侧显示四个数字，占一块 170~190 像素宽的位置：

```
↑: 1.2 KB/s   CPU: 12 %
↓: 3.4 MB/s   内存: 45 %
```

- **两行显示**：每列上下两项，横向占位只有单行时的一半；可切回单行
- **只统计一块网卡**：自动选（已连接网卡里流量最大的那块），也可手动指定
- **屏幕亮度**：每块显示器一条滑杆，拖动即时生效；**笔记本内置屏也支持**
- **端口 → 进程**：列出监听中的 TCP / UDP 端口及对应进程，可直接结束进程
- **磁盘禁用 / 启用**：平时不用的机械盘一键禁用 —— 盘立刻停转，并从资源管理器、磁盘管理和
  任务管理器里彻底消失，不再被后台程序唤醒；要用时一键启用，自己起转、盘符和分区都回来
  （切换盘的状态要管理员权限，每次弹一次 UAC；卸载本程序时会自动把禁用过的盘放回）
- **左键单击可自选面板**：默认打开亮度，也可改成端口→进程或磁盘禁用/启用
- **可隐藏托盘图标**：设置里勾上后通知区不再有图标；任务栏读数左键照样开面板、右键照样弹菜单
- **19 种语言**：简中 / 繁中 / English / 日本語 / 한국어 / Deutsch / Français / Español / Português / Русский /
  Italiano / हिन्दी / Bahasa Indonesia / Polski / Nederlands / Türkçe / বাংলা / ไทย / Tiếng Việt
- 只有文字、没有背景块；深浅色自动切黑字 / 白字；支持副屏和竖向任务栏

| | |
|---|---|
| 系统 | Windows 10 1809+ / Windows 11，64 位 |
| 体积 | exe 277 KB，安装包 2.1 MB |
| 占用 | 私有提交 7.7 MB（任务管理器「内存」列显示 5.1 MB），空闲 CPU 约 0.1% |
| 依赖 | 无（不依赖 VC 运行时 / MFC / .NET） |
| 许可 | 闭源专有，免费使用，见 [LICENSE](LICENSE) |

### 下载与安装

- Gitee：<https://gitee.com/muhe/pico-tray-release/releases>
- GitHub：<https://github.com/ABoat365/pico-tray-release/releases>
- 问题反馈：<https://github.com/ABoat365/pico-tray-release/issues>

下载 `PicoTray-<版本>-setup.exe` 双击安装。默认装到 `%LocalAppData%\Programs\PicoTray`，
**不需要管理员密码**；要给整台机器安装用 `setup.exe /ALLUSERS`。

程序内置更新：右键菜单「检查更新」，或启动 15 秒后自动查一次。更新源可在设置里选
（自动 / Gitee / GitHub）。

> 没有购买代码签名证书，第一次运行 Windows SmartScreen 会拦一下 —— 点「更多信息」→「仍要运行」即可。
> 程序自己下载的更新不带"下载标记"，不会触发这个提示。

### 关于 version.json

程序检查更新读的就是仓库根目录这个文件（GitHub 优先，8 秒不通换 Gitee）：

```json
{
  "version": "1.0.0",
  "url": "https://github.com/…|https://gitee.com/…",
  "sha256": "…64 位小写 hex…",
  "size": 2107675,
  "notes": "简短更新说明"
}
```

`url` 可以放多条镜像（`|` 分隔）；`sha256` 是安装包哈希，下载完会核对，不一致就删掉并提示失败。
文件由源码仓库的 `tools/release.py` 生成，不手写。

---

## English

### What it is

Four numbers sitting to the left of the notification area, about 170–190 px wide:

```
↑: 1.2 KB/s   CPU: 12 %
↓: 3.4 MB/s   Mem: 45 %
```

- **Two-row layout** by default — half the width of a single row, switchable in settings
- **Single adapter** only: auto-picks the busiest connected one, or pin a specific adapter
- **Brightness**: one slider per monitor, applied live — **works on laptop internal panels too**
- **Port → process**: lists listening TCP / UDP ports with their owning process, can kill it
- **Disable / enable a disk**: put an idle mechanical drive to sleep with one click — it spins down
  right away and disappears from Explorer, Disk Management and Task Manager, so nothing wakes it up
  again; enabling spins it back up and restores its drive letters and partitions (each toggle asks
  for administrator rights once; uninstalling the app turns any disk it disabled back on)
- **Pick what a left click opens**: brightness by default, or port → process, or the disk panel
- **Optional tray icon**: hide the notification-area icon in Settings; the taskbar readout still
  opens your panel on left click and the menu on right click
- **19 UI languages**: Chinese (Simplified / Traditional), English, Japanese, Korean, German, French, Spanish,
  Portuguese, Russian, Italian, Hindi, Indonesian, Polish, Dutch, Turkish, Bengali, Thai, Vietnamese
- Text only (no background block), auto black/white text, secondary monitors and vertical taskbars supported

| | |
|---|---|
| OS | Windows 10 1809+ / Windows 11, x64 |
| Size | 277 KB exe, 2.1 MB installer |
| Footprint | 7.7 MB private commit (5.1 MB in Task Manager), ~0.1% idle CPU |
| Dependencies | none (no VC runtime / MFC / .NET) |
| License | proprietary, free to use — see [LICENSE](LICENSE) |

### Download & install

- Gitee: <https://gitee.com/muhe/pico-tray-release/releases>
- GitHub: <https://github.com/ABoat365/pico-tray-release/releases>
- Issues: <https://github.com/ABoat365/pico-tray-release/issues>

Download `PicoTray-<version>-setup.exe` and run it. Installs per-user to
`%LocalAppData%\Programs\PicoTray` — **no admin password needed**. Use `setup.exe /ALLUSERS`
to install for every user on the machine.

Built-in updater: "Check for updates" in the tray menu, or automatically 15 seconds after
startup. The update source (Auto / Gitee / GitHub) is selectable in Settings.

> The binaries are not code-signed, so SmartScreen will warn you the first time you run the
> installer from a browser — click **More info → Run anyway**. Updates downloaded by the app
> itself carry no mark-of-the-web and do not trigger that prompt.

### version.json

The updater reads this file from the repository root (GitHub first, Gitee as fallback after 8 s):

```json
{
  "version": "1.0.0",
  "url": "https://github.com/…|https://gitee.com/…",
  "sha256": "…64 lowercase hex chars…",
  "size": 2107675,
  "notes": "short release note"
}
```

`url` may contain several mirrors separated by `|`. `sha256` is verified after download; a
mismatch deletes the file and reports a failure. The file is generated by `tools/release.py`
in the (private) source repository — it is never written by hand.
