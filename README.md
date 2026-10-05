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

**方式 A · PicGo（日常，推荐）**：拖图进 PicGo → 自动上传到本仓库 → 剪贴板里得到 jsDelivr 链接。上传后本地仓库要 `git pull` 同步一次（PicGo 是通过 API 直接提交到 GitHub 的）。

**方式 B · git push（批量）**：把文件放进对应目录 → `git add . && git commit -m "add xxx" && git push`。

无论哪种方式，**本地这份仓库就是备份**，别删。
