 <h1 align="center">
   <br>
   🍅
   <br>
   番茄钟 · Tomato Clock
   <br>
 </h1>
 
 <p align="center">
   一款极简的番茄钟计时器应用，纯前端、零依赖，开箱即用。
 </p>
 
 <p align="center">
   <img src="https://img.shields.io/badge/纯前端-无后端-blue" alt="纯前端">
   <img src="https://img.shields.io/badge/零依赖-单HTML文件-brightgreen" alt="零依赖">
   <img src="https://img.shields.io/badge/离线可用-开启即用-orange" alt="离线可用">
 </p>
 
 ---
 
 ## 功能特性
 
 - **🍅 番茄工作法** — 25 分钟专注工作，5 分钟短休息，15 分钟长休息，每 4 个番茄一轮循环
 - **⏱ 精准计时** — 基于 `Date.now()` 差值计算，`requestAnimationFrame` 驱动，页面隐藏自动暂停，恢复自动校正
 - **📋 历史记录** — 每次专注或休息完成自动记录，刷新不丢失（`localStorage` 持久化）
 - **🗑 记录管理** — 支持逐条删除历史记录，也支持一键清空所有记录
 - **🔔 双重通知** — Web Audio API 合成音效 + 系统通知（可互相兜底）
 - **⌨ 键盘快捷键** — 空格键启动/暂停，`R` 重置，`S` 跳过，`H` 打开历史记录
 - **🌙 深色主题** — 深色 UI + 玻璃质感设计，阶段切换时主题色平滑过渡
 - **📱 响应式** — 桌面与移动端自适应布局
 
 ## 快速开始
 
 直接在浏览器中打开 `index.html` 即可使用，无需任何构建工具或服务器。
 
 ```bash
 git clone https://github.com/fffran/tomato-clock.git
 cd tomato-clock
 start index.html   # Windows
 # 或直接用浏览器打开 index.html
 ```
 
 也可以直接用浏览器打开文件，完全离线可用。
 
 ## 使用说明
 
 ### 基础操作
 
 | 操作 | 方式 |
 |---|---|
 | 开始 / 暂停 | 点击中央圆形按钮 或 按 `空格键` |
 | 重置 | 点击 ↺ 按钮 或 按 `R` |
 | 跳过当前阶段 | 点击 ⏭ 按钮 或 按 `S` |
 | 查看历史记录 | 点击 🕐 按钮 或 按 `H` |
 | 删除单条记录 | 历史面板中，鼠标悬停记录后点击 ✕ |
 | 清除所有记录 | 历史面板中点击「清除所有记录」按钮 |
 
 ### 工作流程
 
 1. 点击 **开始** 进入 25 分钟专注模式
 2. 专注结束后自动进入短休息（5 分钟）或长休息（15 分钟，每 4 个番茄后）
 3. 休息结束后自动进入下一个专注周期
 4. 可在历史记录面板查看今日和总计的完成数量
 
 ## 技术栈
 
 - **HTML + CSS + JavaScript** — 单 HTML 文件，CSS 和 JS 全部内嵌
 - **CSS 自定义属性** — 主题色、发光色通过 `--phase-color` 等变量驱动
 - **SVG 环形进度** — `stroke-dasharray` / `stroke-dashoffset` 实现动画进度环
 - **Web Audio API** — 合成音效，不依赖外部音频文件
 - **Notification API** — 系统桌面通知
 - **localStorage** — 状态持久化（计时状态 + 历史记录）
 - **requestAnimationFrame** — 高效动画循环，页面隐藏自动暂停
 
 ## 状态管理
 
 计时器引擎采用三态状态机：
 
 ```
 idle ──→ running ──→ paused
  ↑          │           │
  └──────────┴───────────┘
       (完成/重置)
 ```
 
 - **idle** — 空闲状态，等待用户开始
 - **running** — 运行中，`requestAnimationFrame` 驱动 tick 循环
 - **paused** — 暂停状态，保留已消耗时间
 
 所有状态转移走函数调用，不直接突变。刷新页面时从 `localStorage` 恢复完整状态。
 
 ## 项目结构
 
 ```
 tomato-clock/
 ├── index.html   # 完整的应用（CSS + HTML + JS 全部内嵌）
 ├── README.md    # 本文件
 └── .gitignore
 ```
 
 整个应用仅一个 HTML 文件，无需安装依赖。
 
 ## 许可证
 
 MIT
