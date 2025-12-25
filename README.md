# BilibiliNarrowLayout

![License: MIT](https://img.shields.io/badge/许可证-MIT-green.svg)
![Platform: Tampermonkey](https://img.shields.io/badge/平台-Tampermonkey-orange.svg)
![Version](https://img.shields.io/badge/版本-1.0.1-blue.svg)

**BilibiliNarrowLayout** 是一款专为 B 站（Bilibili）视频播放页设计的布局重构脚本。

它的核心使命是解决：在**分屏办公、小窗口观看、或低分辨率屏幕**下，B 站默认布局侧边栏过于拥挤、顶栏图标互相堆叠导致的体验不佳问题。

---

### ✨ 核心功能

* **📏 动态响应式布局**：
    当浏览器窗口宽度小于 **1000px** 时，脚本会自动触发“窄屏模式”，将右侧推荐列表、直播入口等元素平滑移至评论区下方，实现类似移动端的纵向单列布局。
* **🧼 顶栏极简优化**：
    窄屏模式下自动剔除冗余图标（大会员、消息、动态、收藏、历史、投稿等），**仅保留“首页入口”与“个人头像”**，最大化腾出视口空间。
* **🖼️ 懒加载保护机制**：
    深度适配 B 站原生的图片懒加载逻辑。通过精准控制执行时机，确保在 DOM 元素重组后，视频封面和用户头像依然能正常加载显示。
* **⚡ 零干扰无感切换**：
    实时监听窗口缩放，无需刷新页面即可在“原生布局”与“窄屏布局”之间无缝切换，不影响视频播放。
* **🚫 播放器溢出修复**：
    强制修正播放器容器的 `overflow` 属性，彻底消除由于窗口过窄导致的横向滚动条或页面抖动。

---

### 🚀 安装方式

1.  **准备环境**：确保你的浏览器已安装 [Tampermonkey (篡改猴)](https://www.tampermonkey.net/) 扩展。
2.  **一键安装**：点击下方链接进入 GreasyFork 详情页，点击“安装此脚本”：
    * 👉 [BilibiliNarrowLayout (GreasyFork)](https://greasyfork.org/zh-CN/scripts/560143)

---

### 🛠️ 技术实现

* **运行机制**：脚本设定为 `@run-at document-body` 尽早注入样式，并配合 `window.onload` 状态检查，确保逻辑在页面资源完全就绪后执行。
* **单页应用适配**：利用 `MutationObserver` 监听 DOM 树变化，完美适配 B 站点击关联视频（SPA 无刷新切换）的场景。
* **样式注入**：使用 `GM_addStyle` 封装所有响应式 CSS 逻辑，比直接操作 inline-style 具有更高的渲染性能。

---

### ⚖️ 开源协议

本项目基于 [MIT](LICENSE) 协议开源。

---