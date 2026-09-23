# MD 双栏排版工具

上传 Markdown 文档，自动排版为 **A4 · 双栏 · 宋体 · 上下左右 3cm 边距 · 底部居中页码**，一键导出 PDF。

纯前端实现（单个 `index.html`），无需服务器、无需联网安装任何东西，可直接部署到 GitHub Pages。

## 本地使用

直接双击打开 `index.html`（推荐 Chrome / Edge 浏览器），或在本目录启动一个静态服务：

```bash
cd md-print-tool
python3 -m http.server 8080
# 浏览器打开 http://localhost:8080
```

## 导出 PDF 的正确姿势

1. 上传 `.md` 文件（或拖到页面任意位置），等待自动分页完成
2. 点击右上角「导出 PDF」
3. 打印对话框中设置：
   - 目标打印机：**另存为 PDF**
   - 纸张：**A4**
   - 边距：**无**
   - 缩放：**100%（默认）**
   - 选项：勾选**背景图形**；**不要**勾选"页眉和页脚"（页码已由工具生成）

## 部署到 GitHub Pages

```bash
git init
git add index.html sample.md README.md
git commit -m "MD 双栏排版工具"
git remote add origin git@github.com:<你的用户名>/md-print-tool.git
git push -u origin main
```

然后到仓库 **Settings → Pages → Build and deployment**，Source 选 `Deploy from a branch`，分支选 `main`、目录选 `/ (root)`，保存。一两分钟后访问：

```
https://<你的用户名>.github.io/md-print-tool/
```

## 说明

- 分页引擎使用 [Paged.js](https://pagedjs.org/)（CDN 加载），负责把内容切成一页一页并生成页码
- Markdown 解析器为内置轻量实现，支持标题、列表、表格、代码块、引用、图片、粗斜体等常用语法
- 文档中的图片需使用可访问的 URL（本地相对路径图片无法随 md 文件一起上传）
- 若 CDN 无法访问导致分页失败，会自动降级为普通流式排版，此时可在打印对话框勾选"页眉和页脚"用浏览器自带页码
