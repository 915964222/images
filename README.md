

# 🖼️ 手把手搭建 PicGo + GitHub + jsDelivr 免费图床

![教程](https://img.shields.io/badge/教程-图床搭建-brightgreen) ![难度](https://img.shields.io/badge/难度-⭐⭐-blue) ![耗时](https://img.shields.io/badge/耗时-15分钟-orange)

> 💬 **一句话简介**：白嫖 GitHub 存储 + jsDelivr 全球 CDN 加速，实现「本地一键上传 → 自动复制加速链接」的丝滑写作体验。



---

## 一、创建 GitHub 图床仓库

**Step 1** 🔧 登录 [GitHub](https://github.com)，点击右上角 **`+`** → **New repository**

**Step 2** 🔧 按以下要点填写：

| 设置项 | 填写内容 | 备注 |
|:---:|:---|:---|
| Repository name | `images` | 名称随意 |
| Visibility | **Public** | ⚠️ 必须公开，私有仓库 jsDelivr 无法加速 |
| Add a README file | ✅ 勾选 | 便于后续维护 |

**Step 3** 🔧 点击绿色按钮 **Create repository** 完成创建

---

## 二、生成 GitHub Token

**Step 1** 🔑 依次进入：**头像 → `Settings` → `Developer settings` → `Personal access tokens` → `Tokens (classic)` → `Generate new token (classic)`**

**Step 2** 🔑 按以下要点填写：

| 设置项 | 填写内容 |
|:---:|:---|
| Note | `picgo`（备注随意） |
| Expiration | 按需选择有效期 |
| 权限 | ✅ 勾选 **`repo`**（必须） |

**Step 3** 🔑 点击 **Generate token**，然后——

> ⚠️ **立即复制并妥善保存！Token 只显示这一次，刷新页面后就再也看不到了。**

---

## 三、安装并配置 PicGo

### 3.1 下载安装

前往 [PicGo Releases](https://github.com/Molunerfinn/PicGo/releases) 下载对应系统的安装包：

| 系统 | 安装包 |
|:---:|:---|
| 🪟 Windows | `.exe` |
| 🍎 macOS | `.dmg` |

### 3.2 配置图床

打开 PicGo → **图床设置** → **GitHub 图床**，按下表逐项填写：

| 配置项 | 填写内容 | ⚠️ 关键说明 |
|:---:|:---|:---|
| 设定仓库名 | `你的用户名/仓库名` | 如 `yourname/images` |
| 设定分支名 | `main` | 老仓库可能是 `master` |
| 设定 Token | 粘贴第二步的 Token | |
| 设定存储路径 | `img/` | ⚠️ **末尾斜杠必须带上**，否则目录名会和文件名粘连 |
| 设定自定义域名 | `https://cdn.jsdelivr.net/gh/你的用户名/仓库名@main` | ⚠️ **`@main` 必须带上**，否则报 `Invalid URL` |

填写完成后点击 **确定** → **设为默认图床** ✅

---

## 四、使用与验证

**Step 1** 🚀 打开 PicGo **上传区**，拖入或选择图片上传

**Step 2** 🚀 上传成功后，剪贴板自动复制如下格式的链接：

```text
https://cdn.jsdelivr.net/gh/yourname/images@main/img/xxx.png
```

**Step 3** 🚀 在浏览器打开该链接，图片正常显示即大功告成 🎉

<details>
<summary>📦 推荐的 PicGo 设置（点击展开）</summary>

- ✅ 开启「上传后自动复制 URL」
- ✅ 安装 `rename-file` 插件：自动按时间戳重命名，避免文件名冲突
- ✅ 安装 `web-uploader` 插件：可扩展自定义图床接口

</details>

---

## 五、进阶玩法

<details>
<summary>📝 Typora 联动 —— 写作时自动上传</summary>

偏好设置 → 图像 → 插入图片时选择「上传图片」→ 上传服务选 `PicGo(app)` → 指定 PicGo 安装路径。之后在文中粘贴图片会自动上传并替换为 CDN 链接。

</details>

<details>
<summary>🔄 缓存刷新 —— 更新同名图片后必看</summary>

jsDelivr 有 CDN 缓存，更新同名图片后访问 `https://purge.jsdelivr.net/图片完整URL` 主动刷新缓存。

</details>

<details>
<summary>🌏 备用节点 —— 国内访问不畅时使用</summary>

若 `cdn.jsdelivr.net` 访问不畅，可将自定义域名替换为：

- `https://fastly.jsdelivr.net/gh/用户名/仓库名@main`
- `https://gcore.jsdelivr.net/gh/用户名/仓库名@main`

</details>

---

