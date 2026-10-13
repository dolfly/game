# AGENTS.md

本仓库为 Claude Opus 5.5 单句提示词 one-shot 生成实测：三个可玩的 3D 网页游戏（Three.js），每个游戏一个目录，esbuild 打包内联为单文件 HTML 直接部署。

## 目录结构

- `pelican-bike/` —— 鹈鹕骑自行车（海岸公路休闲骑行）
- `cf-transport-ship/` —— 穿越火线·运输船（FPS 团队枪战）
- `qq-speed/` —— QQ 飞车（竞速漂移）

三个游戏结构对称：`src/`（多模块 JS 源码）+ `build.mjs`（esbuild 构建脚本）+ `package.json`。

## 常用命令

进入任一游戏目录：

```bash
npm install      # 安装依赖（three、esbuild 等）
node build.mjs   # 打包内联，产物输出到 dist/index.html
```

`qq-speed/` 额外支持 Cloudflare Pages 部署：

```bash
npm run preview  # wrangler dev 本地预览
npm run deploy   # wrangler deploy 部署
```

## 约定

- 仓库只保存源码，`node_modules/`、`dist/` 不入库（见 `.gitignore`）。
- 三个游戏的源码与 README 均为模型一次性生成、零人工改动。修改时保持单文件 HTML 内联、无外部素材依赖的约束——纹理、动画、音效均由代码程序化生成，不要引入图片/音频/字体等外部资源。
- 新增游戏沿用 `src/ + build.mjs + package.json` 的目录结构。