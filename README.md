# KRONZ 规格书生成器（手机 H5 版）部署包

本包是**纯静态站点**，无需后端、无需服务器运行环境，可直接拖拽部署到任意支持静态托管的平台。
已内置三套平台的配置文件，按需自动生效：

| 平台 | 自动读取的配置 | 说明 |
|------|--------------|------|
| Vercel（Git 导入） | `vercel.json` | build 命令 `npm run build:web`，产物目录 `dist-mobile` |
| Netlify（拖拽 / Git） | `netlify.toml` + `_redirects` | 发布目录为包根，含 SPA 回退 |
| GitHub Pages | `404.html`（= index.html 副本） | 项目页子路径也能正常加载（资源用相对路径） |

## 目录结构

- `index.html` —— 站点入口，根域名直接打开即手机 H5 版
- `assets/` —— JS / CSS 等静态资源（已用相对路径 `./assets/...` 引用，放任意子路径都能加载）
- `vercel.json` / `netlify.toml` / `_redirects` / `404.html` —— 各平台部署配置（拖拽时一并带上即可）
- `README.md` —— 本说明

---

## 方式一：Netlify 拖拽部署（最快，不用 Git）

1. 打开 https://app.netlify.com/drop
2. 把**整个包文件夹**（含 `index.html`、`assets/`、`netlify.toml` 等）拖到页面中间的虚线框
3. 约 10–30 秒后自动得到 `https://<随机名>.netlify.app` 免费 HTTPS 链接
4. 想换自定义子域名：在 Netlify 后台 Site settings → Domain management 里改

## 方式二：GitHub Pages 拖拽上传（不用本地 Git 命令）

1. 在 GitHub 网页新建（或打开）一个仓库
2. 点仓库里的 **Add file → Upload files**，把包内**所有文件**（index.html、assets/、404.html 等）拖进去，提交
3. 仓库 **Settings → Pages**，Source 选部署分支（如 `main`）/ 根目录（`/root`），保存
4. 约 1–2 分钟后得到 `https://<用户名>.github.io/<仓库名>/`
   - 注：GitHub Pages 项目页在子路径下运行，本包资源已用相对路径，无需额外改动

## 方式三：Vercel Git 导入（可持续、每次 push 自动部署）

1. 把整个仓库（含 `vercel.json`）推到 GitHub
2. 打开 https://vercel.com/new ，导入该仓库，自动读取 `vercel.json`
3. 点 Deploy 后得到 `https://<项目名>.vercel.app`

---

## 使用说明

- 微信内主路径导出 = **长图**：长按图片即可保存 / 转发
- 点「PDF / Word」会弹中文引导「请点右上角 ··· → 在浏览器中打开」，在系统浏览器完成下载
- 系统浏览器下载的 Word 与桌面版**逐字节一致**
- 项目数据存浏览器 IndexedDB，无需注册账号，纯本地保存

## 版本

KRONZ 规格书生成器 v1.3.25 手机 H5 版（与桌面 Word 导出逐字节一致）。
