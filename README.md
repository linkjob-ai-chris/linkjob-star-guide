# Linkjob AI STAR Guide - Render 部署包

包含完整文章网页、原 PDF 和 Markdown。正文和 PDF 中的 Linkjob AI 链接均指向 https://www.linkjob.ai/ 。

## 通过 GitHub 网页上传，无需命令行

1. 先在电脑上解压本 ZIP。
2. 在 GitHub 新建专用仓库，例如 `linkjob-star-guide`。可使用 Public 仓库；若用 Private，需在 Render 授权访问。
3. 在仓库网页选择 **Add file > Upload files**，将解压后看到的 **public 文件夹、render.yaml、README.md** 一起拖进去。
4. 提交更改（Commit changes）。不要直接上传 ZIP，也不要把外层解压文件夹一起嵌套进去。
5. 上传后确认仓库根目录能直接看到 public 文件夹，里面能看到 index.html。
6. 回到 https://dashboard.render.com/static/new ，连接 GitHub，选择刚创建的仓库。
7. 使用下面的配置创建 Static Site。

## 表单配置

| 字段 | 填写内容 |
| --- | --- |
| Name | linkjob-star-guide（被占用时换一个名字） |
| Branch | main，或仓库实际默认分支 |
| Root Directory | 留空 |
| Build Command | echo "Static site ready" |
| Publish Directory | public |
| Environment Variable（可选） | SKIP_INSTALL_DEPS=true |

点击 Create Static Site / Deploy Static Site，等待部署成功。最终网址以 Render 控制台显示的 `*.onrender.com` 生产网址为准。
本包为纯静态网站，无须 Node 服务、数据库、npm install 或 npm run build。使用 Static Site 类型。

`render.yaml` 是可选的 Blueprint 配置；如果通过 New > Blueprint 连接仓库，Render 可从该文件读取配置。
通过 Static Site 表单创建时，请手动填写上表，不要假设表单会自动读取 render.yaml。

## 验证

- 首页应直接展示全文。
- 点击文章正文中的 Linkjob AI，应打开 https://www.linkjob.ai/ 。
- PDF、Markdown 下载入口应正常。
- PDF 内的 Linkjob AI 应保留可点击外链。
- robots.txt 允许抓取；首页未设置 noindex 或 nofollow。404 错误页设置 noindex。
- 这些配置不等于已被 Google 收录，收录需上线后另外核验。

## 关于已有网址

Render 的部署来源是代码仓库。已发布的 Cloudflare Pages、Lovable 或 MiniMax 网页网址不能当作 Git 仓库 URL 输入。
如果之前的平台提供 GitHub 同步，可以连接对应仓库；本项目已有完整源码文件，无需重新抓取网站。

官方参考：
- https://render.com/docs/static-sites
- https://render.com/docs/your-first-deploy
- https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository
