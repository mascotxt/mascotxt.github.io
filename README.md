# Mascott Homepage 🐙

一个黑灰色、响应式、适合手机 / iPad / Windows / MacBook 的个人主页。

## 技术

- Vue 3
- Vite
- TypeScript
- 原生 CSS
- GitHub Pages

## 本地运行

需要 Node.js 18+。

```bash
npm install
npm run dev
```

然后打开终端显示的本地地址。

## 构建

```bash
npm run build
```

生成：

```text
dist/
```

## GitHub Pages

### 方法 A：GitHub Actions（推荐）

把项目推送到 GitHub 后：

1. 打开 GitHub 仓库。
2. Settings → Pages。
3. Source 选择 `GitHub Actions`。
4. 添加一个 Node/Vite 的 GitHub Actions workflow。
5. 使用 `npm ci`、`npm run build` 并发布 `dist`。

### 方法 B：gh-pages

先安装依赖：

```bash
npm install
```

然后：

```bash
npm run deploy
```

它会把 `dist` 发布到 `gh-pages` 分支。

GitHub Pages 地址通常是：

```text
https://你的GitHub用户名.github.io/仓库名/
```

如果仓库名称就是：

```text
你的GitHub用户名.github.io
```

则可以直接使用：

```text
https://你的GitHub用户名.github.io/
```

## 注意

当前 Digital Twin 是前端演示版，回答来自本地预设数据，并没有连接真正的 AI API。

当前 Feedback 也是前端演示提交，不会自动保存到数据库。

如果以后接入真实 AI 或反馈数据库，请把 API Key 放在服务器端，不要放在 Vue 前端代码中。