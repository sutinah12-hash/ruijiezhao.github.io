# 个人主页部署修复说明

## 问题原因

1. `_config.yml` 被改成了 `minimal` 主题，但项目仍是 **al-folio**（`Gemfile`、`index.md` 的 `layout: home` 等），导致 `bundle exec jekyll build` 失败。
2. 仓库名是 `ruijiezhao.github.io`（项目站），访问地址应为  
   **https://sutinah12-hash.github.io/ruijiezhao.github.io/**  
   需要 `baseurl: /ruijiezhao.github.io`，不能留空。
3. `Check for broken links on site` 工作流把 `baseurl` 强行设为 `""`，与真实路径不一致。
4. 简历 PDF 链接指向不存在的文件，链接检查会报错。

## 已修改文件

- `_config.yml`：恢复 al-folio 配置，填写赵睿洁信息
- `Gemfile`：移除错误的 `jekyll-remote-theme`
- `_data/socials.yml`、`_data/repositories.yml`
- `.github/workflows/broken-links-site.yml`
- `index.md`、`.lycheeignore`

## 上传到 GitHub

在本地有 Git 登录 `sutinah12-hash` 账号后执行：

```bash
cd /data/ssd0/w61/zhaoruijie/ruijiezhao.github.io-main
git add -A
git commit -m "fix: restore al-folio config and fix Pages deploy"
git push origin main
```

或在 GitHub 网页上把修改后的文件逐个上传覆盖。

## GitHub Pages 设置

仓库 **Settings → Pages**：

- Source: **Deploy from a branch**
- Branch: **gh-pages** / **root**（由 Deploy site 工作流自动推送）

首次推送后等 **Deploy site** 变绿，再访问：

https://sutinah12-hash.github.io/ruijiezhao.github.io/

## 可选：更简洁的网址

若希望主页为 `https://sutinah12-hash.github.io/`（无子路径），需将仓库**重命名**为 `sutinah12-hash.github.io`，并把 `_config.yml` 中 `baseurl` 改为 `""`。

## 上传简历后

1. 将 PDF 放到 `assets/pdf/CV_Ruijie_Zhao.pdf`
2. 在 `_data/socials.yml` 设置 `cv_pdf: /assets/pdf/CV_Ruijie_Zhao.pdf`
3. 在 `index.md` 中取消简历下载链接的注释
