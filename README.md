# 🍿 Lottery Pro - 网页抽奖终端

[🇨🇳 中文版](#-中文说明) | [🇺🇸 English](#-english-documentation)

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Zero Dependency](https://img.shields.io/badge/Zero_Dependencies-4CAF50?style=for-the-badge)
![Offline Sandbox](https://img.shields.io/badge/100%25_Offline_Sandbox-3498db?style=for-the-badge)
![CSPRNG Secure](https://img.shields.io/badge/Security-CSPRNG_Engine-8e44ad?style=for-the-badge)

Lottery Pro 是一款**纯前端（SPA）、零依赖、开箱即用**的轻量级无服务器抽奖系统。可用于满足各类年会、展会活动及发布会中的抽奖需要，同时提供跨屏同步的多媒体交互体验。

无需繁琐的数据库配置，无需安装任何服务端环境。**下载单个 `HTML` 文件，双击即可运行。**

---

## 🇨🇳 中文说明

### ✨ 核心特性

#### 🛡️ 密码学安全随机引擎
- **摒弃 Math.random()**：底层采用密码学标准的安全随机数发生器 **Web Crypto API (CSPRNG)**，从硬件层面提取高熵随机噪声。
- **拒绝采样算法**：彻底消除大基数下的“取模偏差”，确保每一个人或号码被抽中的概率具备完美的统计学均匀性。
- **安全审计哈希**：每一轮抽奖均会生成独立的安全种子哈希（Seed Hash），并支持随日志导出，满足企业级防篡改的安全审计公证需求。

#### 🖥️ 跨屏大屏同步架构
- **无感双轨同步**：支持一键开启独立的无界面“观众大屏”窗口。控制台的主题切换、语言重载、预设奖项展示均会毫秒级自动同步至大屏，实现后台精细控制、前台纯净展示。
- **自适应弹性布局**：大屏及控制台的抽奖展示区采用动态 Flex/Grid 混合排布。能够完美兼容“2-4字汉字姓名”与“英数混合长工号”，且在多行换行时具备托底防抖设计，视觉效果严丝合缝。

#### 🎭 沉浸式多媒体体验
- **心理学悬念延迟**：运用认知心理学设计，当按下停止键时，摇奖音乐和画面瞬间定格，全场屏息 1.2 秒后，伴随着礼花与胜利音效轰出全屏喜报，最大化烘托现场氛围。
- **三轨独立音频引擎**：系统支持背景音乐（BGM）、摇奖滚动音（Rolling）、中奖喜报音（Success）三轨独立控制。悬停可触发带有呼吸感的无级音量调节（默认采用 `0.618` 黄金比例音量），并自动保存音量偏好。
- **全局拖拽交互网**：
  - 🖼️ 拖入图片 -> 自动作为当前奖品图上屏，并应用智能 WebP 压缩机制。
  - 📄 拖入名单 (`.xlsx`, `.csv`, `.txt`) -> 瞬间拦截、智能分割并静默去重。
  - 🎵 拖入音频 (`.mp3`, `.flac`) -> 无缝热替换当前对应的音轨。

#### ⏪ 状态闭环与防呆安全锁
- **误触安全防护**：内置“仅预设模式”开关。在此模式下，如果导播没有选中右侧的任何奖品页签，系统将直接拦截抽奖指令并弹出提示，告别高压环境下的“手抖抽空”。
- **数据回滚**：支持在历史日志中一键“作废”或“恢复”某一轮记录。点击作废时，被抽中的人员会瞬间重返候选池，且控制台和大屏的奖品名、星级、大图也会瞬间逆向重载，让现场操作具备极高的容错率。
- **自动缓存与快照**：配置变更和抽取操作实时写入浏览器 `LocalStorage`，即使意外断电、刷新网页，进度也能 100% 无损恢复。支持将所有状态打包为单个 `.json` 文件导出，实现跨电脑现场换机接力。

---

### 🚀 极速上手

#### 1. 运行方式
直接使用现代浏览器（推荐 Chrome / Edge）打开单 HTML 文件即可。

#### 2. 名单导入指南
系统支持 **数字区间抽取** 与 **名单模式**。
若要导入名单，请点击 `[📥 导入名单]` 或直接将文件拖入巨大的蓝色摇奖区：
- **Excel (.xlsx / .xls)**：系统严格且**仅解析 Sheet1 的 A列**。⚠️ 请务必删除第一行的表头，以免标题中奖！
- **TXT / CSV**：支持换行、空格、全半角逗号作为分隔符，引擎将进行自动分割与去重。

#### 3. 音频资源自动载入 (可选)
你只需在 HTML 文件的**同一文件夹目录下**放入以下三个文件，系统启动时将**全自动静默加载**：
- `bgm.mp3`：全局循环背景音乐。
- `rolling.mp3`：按下空格键开始滚动时的音效（如心跳加速声）。
- `success.mp3`：停止滚动、开奖弹窗弹出瞬间的音效（如礼花绽放声）。
*(若未放置文件系统依然正常运行，控制台亦支持直接拖拽音频热替换)*。

---

### 📊 数据管理与导出

- **🎨 生成海报**：一键将最近 N 轮的有效中奖记录，生成排版精美、高度自适应的高清 `PNG` 公示海报，方便分发工作群。
- **↓ 导出日志**：将所有历史记录（含有效/作废追踪、奖项明细、硬件哈希种子、余量快照）一键导出为规范的 `CSV` 审计报表。

---

### ⚖️ 安全声明

本终端为纯前端架构（SPA），没有后端服务器，没有网络请求接口。所有运算、随机数生成及本地持久化存储均在您的浏览器本地沙盒中完成，从物理层面杜绝了数据外泄与后台暗箱操作的可能。

---
---

## 🇺🇸 English Documentation

### ✨ Core Features

#### 🛡️ Cryptographically Secure Engine
- **Discard Math.random()**: Powered by the **Web Crypto API (CSPRNG)**, extracting high-entropy random noise from the hardware level.
- **Rejection Sampling**: Completely eliminates modulo bias in large datasets, ensuring every person or number has a mathematically perfect, uniform probability of being drawn.
- **Security Audit Hash**: Every draw generates an independent Seed Hash. This can be exported with the logs to meet enterprise-level anti-tampering and audit requirements.

#### 🖥️ Cross-Screen Sync Architecture
- **Seamless Dual-Track Sync**: Open a clean, UI-free "Audience Screen" window with a single click. Console operations (theme toggles, language switches, prize presets) sync to the audience screen in milliseconds, ensuring fine-grained backend control and pure frontend presentation.
- **Adaptive Elastic Layout**: Both the audience and console screens use a dynamic Flex/Grid layout. It perfectly accommodates short names or long alphanumeric IDs, with an anti-jitter design during multi-line line breaks, ensuring flawless visual stability.

#### 🎭 Immersive Multimedia Experience
- **Psychological Suspense Delay**: Leveraging cognitive psychology, the rolling stops instantly when the key is pressed, freezing the screen for 1.2 seconds. This creates a moment of suspense before blasting the success modal and SFX, maximizing the live atmosphere.
- **Three-Track Independent Audio**: Independent controls for Background Music (BGM), Rolling SFX, and Success SFX. Hovering over the buttons triggers a stepless volume control (defaulting to the `0.618` golden ratio) that auto-saves your preferences.
- **Global Drag-and-Drop Network**:
  - 🖼️ Drag an Image -> Automatically applies as the current prize with smart WebP compression.
  - 📄 Drag a List (`.xlsx`, `.csv`, `.txt`) -> Instantly intercepts, intelligently splits, and silently removes duplicates.
  - 🎵 Drag Audio (`.mp3`, `.flac`) -> Seamlessly hot-swaps the corresponding audio track.

#### ⏪ State Closed-Loop & Failsafes
- **Anti-Mis-touch Security Lock**: Built-in "Preset Only Mode". If the director fails to select a prize tab on the right, the system blocks the draw command and issues a warning, preventing empty draws under high-pressure environments.
- **Causal Data Rollback**: Support for one-click "Invalidate" or "Restore" in the logs. When invalidated, drawn candidates instantly return to the pool, and the prize name, stars, and image are reverse-loaded to both screens, offering extremely high fault tolerance.
- **Auto Cache & Snapshots**: Every setting and draw is written to the browser's `LocalStorage` in real-time. Even after power loss or accidental refresh, progress is 100% restored. You can export all states as a single `.json` file for cross-computer relays.

---

### 🚀 Quick Start

#### 1. How to Run
Simply open the single HTML file using any modern browser (Chrome / Edge recommended).

#### 2. List Import Guide
The system supports **Number Range Mode** and **Custom List Mode**. 
Click `[📥 IMPORT LIST]` or drag a file into the blue drawing area:
- **Excel (.xlsx / .xls)**: The system strictly reads **ONLY Column A of Sheet1**. ⚠️ Please remove the header row to prevent it from being drawn!
- **TXT / CSV**: Supports newlines, spaces, and commas as separators. The engine will automatically split and deduplicate.

#### 3. Auto Audio Loading (Optional)
Place the following three files in the **same directory** as the HTML file, and the system will **silently auto-load** them on startup:
- `bgm.mp3`: Global looping background music.
- `rolling.mp3`: The sound effect while the draw is rolling.
- `success.mp3`: The celebratory sound effect when the result pops up.
*(The system works perfectly without these files, and you can also drag & drop audio into the console to replace them).*

---

### 📊 Data Management & Export

- **🎨 Generate Posters**: One-click generation of beautifully formatted, highly adaptive HD `PNG` posters of recent winners for easy sharing.
- **↓ Export Logs**: Export all histories (including valid/invalid tracks, prize details, hardware hashes, and remaining pool snapshots) as a standard `CSV` audit report.

---

### ⚖️ Security Disclaimer

This terminal is a pure frontend (SPA) architecture. There are no backend servers and no network requests. All computations, random number generation, and data persistence are isolated within your browser's local sandbox, physically eliminating any possibility of data leaks or backstage manipulation.

## 👨‍💻 Author & License
Designed by **T1MESX** | License: MIT
