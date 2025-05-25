# 如何在markdown文档写作中插入图片

>  PicGo + Aliyun OSS 插图教程（Typora & VSCode）

## 🖼️ 效果预览

![2025-05-24](https://isedocument.oss-cn-beijing.aliyuncs.com/images/2025-05-24.gif)

- 在 Typora / VSCode 中直接粘贴图片
- 图片会自动上传至阿里云 OSS（对象存储服务）
- Markdown 自动插入外链，支持在网页、GitHub 等平台无障碍展示

## 🛠️ 配置教程

基于markdown编写使用习惯，对于 Typora 用户和 VSCode 用户会有不同的配置方式，可以按照自己的习惯选择一种方法进行配置。

### ✍️ 方式一：Typora 用户（推荐使用 PicGo 应用）

适用于：更偏向可视化界面操作，使用 Typora 写文档的同学

#### 📥 第一步：下载安装 PicGo 应用

1. 前往 GitHub 下载页面：https://github.com/Molunerfinn/PicGo/releases
> 推荐下载稳定版：https://github.com/Molunerfinn/PicGo/releases/tag/v2.3.1
2. 下载对应操作系统版本（Windows/macOS）
![20250524172526](https://isedocument.oss-cn-beijing.aliyuncs.com/images/20250524172526.png)
3. 安装并打开应用

#### ⚙️ 第二步：在 PicGo 应用中配置图床

1. 点击左侧菜单栏中的：
`图床设置 › 阿里云 OSS`

![20250524173233](https://isedocument.oss-cn-beijing.aliyuncs.com/images/20250524173233.png)

2. 并填入如下信息，选择确定并设为默认图床：

| **配置项**       | **内容**                                                |
| ---------------- | ------------------------------------------------------- |
| AccessKey ID     | LTAI5tLPxQXqBkbrPJQUEC8s                                |
| AccessKey Secret | 请与我联系获取                        |
| Area             | oss-cn-beijing                                          |
| Bucket           | isedocument                                             |
| Path             | images/                                    |


3. 最终如图所示：

![20250524173347](https://isedocument.oss-cn-beijing.aliyuncs.com/images/20250524173347.png)

#### ✏️ 第三步：在 Typora 中配置 PicGo

![20250524211051](https://isedocument.oss-cn-beijing.aliyuncs.com/images/20250524211051.png)

配置好后在Typora中粘贴图片后会出现上传图片选项，选择之后会自动将图片上传至阿里云OSS，大功告成。

### ✍️ 方式二：VSCode 用户（推荐使用 PicGo 插件）

#### 📦 第一步：安装 PicGo 插件（而不是应用）

打开 VSCode，进入扩展商店：
- 搜索 PicGo 插件（作者 Spades.S）
- 点击安装

> 这不是 PicGo GUI 应用，而是基于 PicGo-Core 的 VSCode 插件，配置方式也不同。

#### ⚙️ 第二步：在插件中配置图床信息

图床的配置信息和方式一相同。

![20250524211749](https://isedocument.oss-cn-beijing.aliyuncs.com/images/20250524211749.png)

📌 需要注意的是，在 VSCode 中需要额外查看上传快捷键，按照快捷键粘贴图片可以直接上传并返回 url，大功告成。

![20250524212101](https://isedocument.oss-cn-beijing.aliyuncs.com/images/20250524212101.png)

## 原理简述

让我们一步步解构你将使用的工具是如何协同工作的：

#### 1️⃣ Markdown 文档为什么需要图床？

在 Markdown 写作中，插入图片可以有两种方式：
- 使用本地路径（如 ./images/a.png）：不便分享，迁移困难。
- 使用公网链接（如 https://xxx.oss-cn-beijing.aliyuncs.com/xxx.png）：利于共享、跨平台使用。

所以，图床（图片托管服务）就很重要！

#### 2️⃣ PicGo：图片上传的工具人

PicGo 是一个开源的图片上传工具，有两种版本：
- PicGo GUI（图形界面）适合新手
- PicGo-Core（命令行核心）可以被其他工具调用

它的作用是：

你一粘贴图片，它会拦截这个动作 → 上传到设定的图床（比如阿里云 OSS）→ 返回图片 URL → 插入到 Markdown 中

📌 注意：要想实现粘贴图片就拦截上传，需要设置对应的快捷键，不建议直接覆盖 `CTRL + C`

#### 3️⃣ 阿里云 OSS：图片的云家园

OSS（Object Storage Service）是阿里云的文件存储服务，它可以：
- 保存图片文件
- 自动提供公网访问链接
- 根据 Bucket+Path+文件名 生成完整访问路径

比如：
```
https://isedocument.oss-cn-beijing.aliyuncs.com/img/20230523-123456.png
```

#### 4️⃣ Typora / VSCode：写作编辑器与 PicGo 配合

这两个编辑器可以在你粘贴图片或拖动图片时：
- 调用 PicGo（通过插件或配置）
- 自动将图片上传 + 返回链接 + 插入到文档中

整个过程你几乎感觉不到上传操作，全自动！