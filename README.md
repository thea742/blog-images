# blog-images · 博客图床仓库

这个仓库是 `qingyuanblog` 博客的**公开图片仓库**（必须 Public，jsDelivr 才能读取）。
本地位置：`D:/M_Soft/Project/my-personal-blog/Pictures/`，与博客项目同级。

## 引用地址规则

上传后在博客里这样引用（把文件路径换成实际的）：

```
https://cdn.jsdelivr.net/gh/thea742/blog-images@main/images/covers/chapter-01.webp
https://cdn.jsdelivr.net/gh/thea742/blog-images@main/images/posts/chapter-06/xxx.webp
```

国内访问慢或失败时，把 `cdn.jsdelivr.net` 换成 `gcore.jsdelivr.net` 或 `fastly.jsdelivr.net`（同一份文件，不同 CDN 入口）。

## 目录结构

```
images/
├─ covers/        封面图（chapter-01.webp ...）
└─ posts/         正文配图（按文章 slug 建子目录）
```

## 规则（必须遵守）

1. **文件名一旦上传，永不再改内容** —— jsDelivr 对 `@main` 分支 URL 缓存 12 小时，覆盖同名文件读者看到的还是旧图。改图 = 换新文件名（可加日期后缀 `chapter-01-20261005.webp`）。
2. **全小写 + 连字符**，不用中文、不用空格。
3. **原图不放这里** —— 原图备份在 `picture/blog-originals/`，这里只放压缩后的发布版（封面 ≤200KB，正文图 ≤80KB）。
4. **每张图上传后，博客里记一行来源**（可选但推荐）。

## 两种上传方式

**方式 A · 命令行脚本（推荐，已实测可用）**：在博客项目里跑

```powershell
node scripts/upload-to-github.mjs ./图.webp --dir images/covers --name chapter-01.webp
```

自动拿 `gh auth token`，上传完直接打印 jsDelivr 链接。重名会拒绝（防止覆盖）。

**方式 B · PicGo（可选，可视化）**：拖图进 PicGo → 自动上传到本仓库 → 剪贴板得到链接。
配置：仓库 `thea742/blog-images`、分支 `main`、存储路径 `images/`、
自定义域名 `https://cdn.jsdelivr.net/gh/thea742/blog-images@main`，token 用 `gh auth token` 取。
> 部分机器上 PicGo 会因 Electron 被系统安全策略拦截而启动失败（详见博客 `docs/图床与PicGo.md`），
> 这时就用方式 A，功能一样。

无论哪种方式，**上传后本地 `git pull` 一次**保持备份同步，别删本地这份。

无论哪种方式，**本地这份仓库就是备份**，别删。
