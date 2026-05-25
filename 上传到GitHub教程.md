# 如何把个人主页 + 简历上传到 GitHub

仓库地址：https://github.com/sutinah12-hash/ruijiezhao.github.io  
账号：`sutinah12-hash`  
邮箱：`sutinah12@madrasah.kemenag.go.id`

---

## 第一步：准备简历文件（在你自己的 Windows 电脑上）

1. 找到简历：`D:\Users\zhaoruijie\Downloads\简历最终版.pdf`
2. **复制一份**，重命名为：`CV_Ruijie_Zhao.pdf`（英文名，避免 GitHub 中文路径问题）
3. 把 `CV_Ruijie_Zhao.pdf` 放进项目文件夹里的：

   ```
   ruijiezhao.github.io-main\assets\pdf\CV_Ruijie_Zhao.pdf
   ```

   若你用的是超算上的修复包，路径为：

   ```
   /data/ssd0/w61/zhaoruijie/ruijiezhao.github.io-main/assets/pdf/CV_Ruijie_Zhao.pdf
   ```

---

## 方法二（推荐新手）：GitHub 网页上传

不用装 Git，全程在浏览器完成。

### 1. 登录 GitHub

打开 https://github.com/login ，用账号 **sutinah12-hash** 登录。

### 2. 打开你的仓库

https://github.com/sutinah12-hash/ruijiezhao.github.io

### 3. 上传修复后的文件（若本地有整包）

- 点击 **Add file** → **Upload files**
- 把本地 `ruijiezhao.github.io-main` 里**已修改过的文件**拖进去，或逐个上传：
  - `_config.yml`
  - `index.md`
  - `Gemfile`
  - `_data/socials.yml`
  - `_data/repositories.yml`
  - `.github/workflows/broken-links-site.yml`
  - 等（与超算上修复版一致即可）

### 4. 单独上传简历 PDF

1. 进入仓库里的 `assets` → `pdf` 文件夹  
   （没有就先在网页上 **Create new file** 路径填 `assets/pdf/CV_Ruijie_Zhao.pdf`）
2. 点击 **Add file** → **Upload files**
3. 选择你重命名后的 `CV_Ruijie_Zhao.pdf`
4. 页面底部填写提交说明，例如：`add CV pdf`
5. 点击 **Commit changes**

### 5. 开启 Pages（只需检查一次）

1. 仓库 **Settings** → 左侧 **Pages**
2. **Build and deployment** → Source 选 **Deploy from a branch**
3. Branch 选 **gh-pages**，文件夹 **/ (root)**  
   （等 **Actions** 里 **Deploy site** 跑成功后会出现 gh-pages 分支）
4. 保存

### 6. 启用 Actions（若工作流被禁用）

1. 点 **Actions** 标签
2. 若提示启用 workflow，点 **I understand my workflows, go ahead and enable them**

### 7. 等待部署

1. **Actions** → 看 **Deploy site** 是否绿色 ✓
2. 成功后访问：**https://sutinah12-hash.github.io/ruijiezhao.github.io/**

---

## 方法一：Windows 上用 Git（适合以后经常更新）

### 1. 安装 Git

下载：https://git-scm.com/download/win  
安装时可选默认选项。

### 2. 打开 PowerShell，配置身份（只需一次）

```powershell
git config --global user.name "sutinah12-hash"
git config --global user.email "sutinah12@madrasah.kemenag.go.id"
```

### 3. 克隆仓库到本机

```powershell
cd D:\Users\zhaoruijie\Downloads
git clone https://github.com/sutinah12-hash/ruijiezhao.github.io.git
cd ruijiezhao.github.io
```

浏览器会提示登录 GitHub（可用账号密码或 Personal Access Token）。

### 4. 放入简历 + 覆盖修复文件

- 把 `简历最终版.pdf` 复制为：

  `ruijiezhao.github.io\assets\pdf\CV_Ruijie_Zhao.pdf`

- 若超算上有修复好的 `_config.yml` 等，也复制进这个文件夹覆盖原文件。

### 5. 提交并推送

```powershell
git add .
git status
git commit -m "update site config and add CV"
git push origin main
```

推送成功后到 **Actions** 查看 **Deploy site** 是否成功。

---

## 登录 GitHub 推送失败时（Token）

GitHub 已不支持用密码推送，需要 **Personal Access Token**：

1. GitHub 右上角头像 → **Settings**
2. 左侧最下 **Developer settings** → **Personal access tokens** → **Tokens (classic)**
3. **Generate new token (classic)**，勾选 `repo`
4. 复制 token（只显示一次）
5. `git push` 时：
   - 用户名：`sutinah12-hash`
   - 密码：粘贴 **token**（不是登录密码）

---

## 上传后自检清单

| 检查项 | 位置 |
|--------|------|
| Deploy site 成功 | Actions 标签 |
| 主页能打开 | https://sutinah12-hash.github.io/ruijiezhao.github.io/ |
| 简历能下载 | 主页「Download My CV」链接 |
| PDF 路径正确 | 仓库里存在 `assets/pdf/CV_Ruijie_Zhao.pdf` |

---

## 常见问题

**Q：网页是 404？**  
等 Deploy 完成；确认 Pages 用的是 **gh-pages** 分支。

**Q：想改成更短的网址？**  
把仓库改名为 `sutinah12-hash.github.io`，并把 `_config.yml` 里 `baseurl` 改成 `""`。

**Q：Actions 还是红？**  
把 **Deploy site** 失败那一段日志复制发出来再排查。
