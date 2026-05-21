# Spring AI Portal - 人工智能应用中心

一个基于 Vue 3 + TypeScript + Vite 构建的现代化 AI 应用门户，集成了多种智能对话场景，包括通用聊天、PDF 文档问答、智能客服和游戏化互动等功能。

## 项目概述

Spring AI Portal 是一个功能丰富的前端应用，旨在为用户提供多样化的 AI 交互体验。项目采用现代化的技术栈和设计理念，支持深色/浅色主题切换、响应式布局，并提供流畅的用户体验。

### 核心特性

- **多模态 AI 聊天**：支持文本、图片、音频、视频等多种媒体类型的对话
- **PDF 文档智能问答**：上传 PDF 文档并与之对话，实现知识库检索
- **智能客服系统**：模拟课程咨询场景，支持预约功能
- **哄哄模拟器游戏**：游戏化的情感互动练习，包含原谅值机制
- **深色/浅色主题**：基于 VueUse 的主题切换功能
- **流式响应**：实时显示 AI 回复内容，提升用户体验
- **Markdown 渲染**：支持代码高亮、表格、列表等富文本格式
- **聊天记录管理**：保存和管理多个对话会话

## 技术栈

### 前端框架
- **Vue 3.4+**：采用 Composition API 和 `<script setup>` 语法
- **TypeScript 5.7+**：类型安全的 JavaScript 超集
- **Vite 6.1+**：下一代前端构建工具

### 状态管理与路由
- **Pinia 3.0+**：Vue 官方推荐的状态管理库
- **Vue Router 4.2+**：官方路由管理器，支持懒加载

### UI 组件与工具
- **Naive UI 2.41+**：Vue 3 组件库
- **Heroicons Vue 2.2+**：精美的 SVG 图标库
- **VueUse 12.7+**：实用的 Composition API 工具集

### 文档处理
- **PDFTron WebViewer 11.3+**：专业的 PDF 查看和处理库
- **Marked 15.0+**：Markdown 解析器
- **DOMPurify 3.2+**：HTML 净化器，防止 XSS 攻击

### 代码高亮
- **Highlight.js 11.11+**：语法高亮库，支持多种编程语言

### 样式处理
- **SCSS/Sass 1.85+**：CSS 预处理器
- **CSS Variables**：动态主题切换

### 开发工具
- **vue-tsc 2.2+**：Vue 项目的 TypeScript 检查
- **vite-plugin-vue-devtools**：Vue DevTools 集成

## 项目结构

```
spring-ai-protal/
├── public/                    # 静态资源目录
│   ├── favicon.ico           # 网站图标
│   └── pdf.worker.js         # PDF 处理 Worker
├── src/                      # 源代码目录
│   ├── assets/               # 静态资源
│   │   ├── base.css         # 基础样式
│   │   ├── logo.svg         # Logo 图标
│   │   └── main.css         # 全局样式
│   ├── components/           # 可复用组件
│   │   ├── ChatMessage.vue  # 聊天消息组件
│   │   ├── PDFViewer.vue    # PDF 查看器组件
│   │   ├── HelloWorld.vue   # 示例组件
│   │   ├── TheWelcome.vue   # 欢迎页面组件
│   │   ├── WelcomeItem.vue  # 欢迎项组件
│   │   └── icons/           # 图标组件目录
│   ├── router/              # 路由配置
│   │   ├── index.js         # JavaScript 路由（未使用）
│   │   └── index.ts         # TypeScript 路由配置
│   ├── services/            # API 服务层
│   │   └── api.js           # 后端 API 接口封装
│   ├── stores/              # Pinia 状态管理
│   │   └── counter.ts       # 示例 Store
│   ├── utils/               # 工具函数
│   │   └── pdfStorage.js    # PDF 存储工具
│   ├── views/               # 页面视图组件
│   │   ├── Home.vue         # 应用中心首页
│   │   ├── HomeView.vue     # 默认首页
│   │   ├── AboutView.vue    # 关于页面
│   │   ├── AIChat.vue       # AI 聊天页面
│   │   ├── ChatPDF.vue      # PDF 对话页面
│   │   ├── CustomerService.vue  # 智能客服页面
│   │   ├── GameChat.vue     # 哄哄模拟器游戏页面
│   │   └── ComfortSimulator.vue  # 安慰模拟器（占位）
│   ├── App.vue              # 根组件
│   ├── main.js              # JavaScript 入口（未使用）
│   └── main.ts              # TypeScript 入口文件
├── env.d.ts                 # TypeScript 环境声明
├── index.html               # HTML 模板
├── package.json             # 项目依赖配置
├── tsconfig.json            # TypeScript 配置
├── tsconfig.app.json        # 应用 TS 配置
├── tsconfig.node.json       # Node TS 配置
├── vite.config.ts           # Vite 配置文件
└── README.md                # 项目说明文档
```

## 核心模块详解

### 1. 应用中心 (Home.vue)

应用的主入口页面，展示所有可用的 AI 应用模块：

- **AI 聊天**：多模态对话机器人，支持图片、音频、视频
- **哄哄模拟器**：游戏化的情感互动练习
- **智能客服**：24小时在线的课程咨询师
- **ChatPDF**：PDF 文档智能问答

采用响应式卡片布局，支持 1/2/4 列自适应显示。

### 2. AI 聊天模块 (AIChat.vue)

功能最全面的聊天界面，支持：

**文件上传功能**
- 支持图片、音频、视频文件
- 文件大小限制：图片 10MB、音频 10MB、视频 150MB
- 最多同时上传 3 个文件
- 音频/视频时长限制（音频 3 分钟、视频 40 秒）
- 拖拽上传支持

**聊天管理**
- 左侧边栏显示聊天历史
- 创建新对话
- 切换不同对话会话
- 自动保存聊天记录

**消息展示**
- 流式响应显示
- Markdown 格式支持
- 代码块高亮
- 消息复制功能

**技术特点**
- 自动调整输入框高度
- 智能滚动到底部
- 响应式布局（移动端隐藏侧边栏）

### 3. PDF 对话模块 (ChatPDF.vue)

实现与 PDF 文档的智能对话：

**PDF 上传**
- 点击上传或拖拽上传
- 上传进度显示
- 文件类型验证（仅 PDF）

**分屏显示**
- 左侧：PDF 文档预览（使用 iframe 嵌入）
- 右侧：对话界面
- 支持响应式布局（移动端垂直排列）

**对话功能**
- 基于 chatId 关联 PDF 和对话历史
- 流式响应显示
- Markdown 渲染
- 历史记录管理

**资源管理**
- 完善的资源清理机制
- Blob URL 管理
- 路由切换时自动释放资源

### 4. 智能客服模块 (CustomerService.vue)

模拟课程咨询场景：

**客服形象**
- 显示客服头像和名称（"小黑 - 程序员智能客服"）
- 专业的聊天界面

**对话功能**
- 流式响应
- Markdown 支持
- 聊天记录管理

**预约功能**
- 自动识别预约信息
- 弹窗显示预约详情
- 支持 Markdown 格式的预约信息

**自动问候**
- 新建对话时自动发送问候语

### 5. 哄哄模拟器游戏 (GameChat.vue)

游戏化的情感互动练习：

**游戏机制**
- 原谅值系统（0-100%）
- 对话轮次限制（最多 10 轮）
- 胜利条件：原谅值达到 100%
- 失败条件：原谅值降到 0 或轮次用完

**游戏界面**
- 原谅值进度条（颜色随数值变化）
- 对话轮次显示
- 游戏结果展示
- 重新开始功能

**交互设计**
- 自定义生气原因输入
- 实时原谅值更新
- 心跳动画效果（原谅值满时）

### 6. 聊天消息组件 (ChatMessage.vue)

通用的消息展示组件：

**功能特性**
- 用户/AI 消息区分显示
- Markdown 渲染
- 代码块高亮（Highlight.js）
- 思考块特殊显示（`<think>` 标签）
- 消息复制功能
- 代码块独立复制按钮

**样式设计**
- 不同的气泡样式（用户右对齐，AI 左对齐）
- 悬停显示复制按钮
- 深色/浅色主题适配
- 平滑的进入动画

**安全处理**
- DOMPurify 净化 HTML
- 防止 XSS 攻击

### 7. PDF 查看器组件 (PDFViewer.vue)

PDF 文档预览组件：

**实现方式**
- 使用 iframe 嵌入 PDF
- Blob URL 管理
- 主题适配（深色/浅色模式）

**生命周期管理**
- 组件挂载时初始化
- 文件变化时重新加载
- 组件卸载时清理资源

### 8. API 服务层 (services/api.js)

统一的后端接口封装：

**接口方法**
- `sendMessage()`：发送通用聊天消息（支持 FormData）
- `sendGameMessage()`：发送游戏消息
- `sendServiceMessage()`：发送客服消息
- `sendPdfMessage()`：发送 PDF 问答消息
- `getChatHistory()`：获取聊天历史列表
- `getChatMessages()`：获取特定对话的消息

**技术特点**
- 流式响应处理（返回 ReadableStream）
- 统一的错误处理
- 超时控制（PDF 消息 30 秒）
- URL 参数编码

## 后端 API 接口

前端需要与运行在 `http://localhost:8080` 的后端服务通信：

### 通用聊天
- **POST** `/springAi/chat?chatId={chatId}` - 发送聊天消息（支持 FormData）

### 游戏模块
- **GET** `/ai/game?prompt={prompt}&chatId={chatId}` - 发送游戏消息

### 客服模块
- **GET** `/ai/service?prompt={prompt}&chatId={chatId}` - 发送客服消息

### PDF 模块
- **POST** `/ai/pdf/upload/{chatId}` - 上传 PDF 文件
- **GET** `/ai/pdf/chat?prompt={prompt}&chatId={chatId}` - PDF 对话
- **GET** `/ai/pdf/file/{chatId}` - 获取 PDF 文件

### 历史记录
- **GET** `/ai/history/{type}` - 获取聊天历史列表（type: chat/pdf/service）
- **GET** `/ai/history/{type}/{chatId}` - 获取特定对话的消息

## 安装与运行

### 环境要求

- Node.js 18+ 
- npm 9+ 或 yarn 1.22+
- 后端服务运行在 http://localhost:8080

### 安装依赖

```bash
npm install
```

### 开发模式

```bash
npm run dev
```

启动后访问：http://localhost:5173

### 生产构建

```bash
# 类型检查 + 构建
npm run build

# 仅构建
npm run build-only

# 类型检查
npm run type-check
```

### 预览生产版本

```bash
npm run preview
```

## 配置说明

### Vite 配置 (vite.config.ts)

```typescript
export default defineConfig({
  plugins: [
    vue(),
    vueDevTools(),  // Vue DevTools 支持
  ],
  resolve: {
    alias: {
      '@': fileURLToPath(new URL('./src', import.meta.url))  // @ 别名
    },
  },
})
```

### TypeScript 配置

项目使用严格的 TypeScript 配置：
- `tsconfig.json`：主配置文件
- `tsconfig.app.json`：应用代码配置
- `tsconfig.node.json`：Node 环境配置

### 主题配置

使用 CSS 变量实现主题切换：

```css
:root {
  --bg-color: #f5f5f5;
  --text-color: #333;
}

.dark {
  --bg-color: #1a1a1a;
  --text-color: #fff;
}
```

通过 VueUse 的 `useDark()` 和 `useToggle()` 实现主题切换。

## 设计亮点

### 1. 响应式设计

- 桌面端：完整功能展示
- 平板端：自适应布局
- 移动端：隐藏侧边栏，优化触摸操作

### 2. 深色模式

- 全站深色主题支持
- 所有组件完美适配
- 平滑过渡动画
- 自动保存用户偏好

### 3. 流式响应

- 实时显示 AI 回复
- 打字机效果
- 自动滚动到底部
- 优雅的加载状态

### 4. 安全性

- DOMPurify 净化 HTML
- 防止 XSS 攻击
- 文件类型验证
- 文件大小限制

### 5. 性能优化

- 路由懒加载
- 组件按需导入
- 虚拟滚动（待实现）
- 图片懒加载（待实现）

## 开发规范

### 代码风格

- 使用 TypeScript 编写业务逻辑
- 采用 Composition API
- 使用 `<script setup>` 语法
- SCSS 编写样式（scoped）

### 命名规范

- 组件：PascalCase（如 `ChatMessage.vue`）
- 文件：kebab-case 或 PascalCase
- 变量：camelCase
- 常量：UPPER_SNAKE_CASE

### Git 提交规范

建议使用以下前缀：
- `feat:` 新功能
- `fix:` 修复 bug
- `docs:` 文档更新
- `style:` 代码格式调整
- `refactor:` 重构代码
- `test:` 测试相关
- `chore:` 构建/工具链相关

## 常见问题

### 1. 后端连接失败

确保后端服务运行在 `http://localhost:8080`，检查 CORS 配置。

### 2. PDF 无法加载

- 检查文件格式是否为 PDF
- 确认文件大小不超过限制
- 查看浏览器控制台错误信息

### 3. 文件上传失败

- 检查文件类型是否符合要求
- 确认文件大小在限制范围内
- 对于音视频文件，检查时长是否超限

### 4. 主题切换无效

清除浏览器缓存，或尝试硬刷新（Ctrl+F5）。

## 未来规划

- [ ] 添加语音输入功能
- [ ] 实现离线消息缓存
- [ ] 增加更多游戏场景
- [ ] 支持多人协作对话
- [ ] 添加对话导出功能
- [ ] 实现消息搜索
- [ ] 优化移动端体验
- [ ] 添加 PWA 支持

## 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。

## 致谢

- [Vue.js](https://vuejs.org/)
- [Vite](https://vitejs.dev/)
- [Naive UI](https://www.naiveui.com/)
- [VueUse](https://vueuse.org/)
- [Heroicons](https://heroicons.com/)
- [Highlight.js](https://highlightjs.org/)

---

**注意**：本项目需要配合后端 Spring AI 服务使用，请确保后端服务已正确配置并运行。
