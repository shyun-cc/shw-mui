# shw-mui 文档站

设计讨论稿；业务方案尚未确认或实现。站点源文件位于本目录，与未来业务工程独立。

## 工具基线

沿用 [OINK 官方 starter](https://github.com/pgsty/oink-starter) 的 Go 1.27.3、Hugo Extended 0.168.0、OINK v1.5.1（`go.mod` / `go.sum` 固定）。无需 Node.js、npm 或外部 Sass。保留上游 LibSass 弃用警告，不使用 `--panicOnWarning`。

## 预览和构建

从仓库根目录执行：

```sh
cd docs
go mod download github.com/pgsty/oink
hugo server --baseURL http://localhost:1313/shw-mui/ --appendPort=false
# 生产构建，默认含 /shw-mui/ 子路径
hugo --cleanDestinationDir --gc --minify --environment production --printPathWarnings
```

生成目录 `public/`、`resources/`、缓存与锁文件已忽略；不要提交二进制或构建产物。

## 评审与发布

`.github/workflows/docs-pages.yml` 对文档 PR 执行构建；只有 `main` 上的合并或手动运行才具备部署条件。构建使用 `hugo.yaml` 中的项目 base URL，兼容 `/shw-mui/` 子路径；若将来改用自定义域名，须同步修改该配置。工作流只授予部署任务所需的 Pages 与 OIDC 权限，不需要新增仓库秘密。

维护者在确认公开内容及合并 PR 后，需自行在 Settings → Pages 选择 GitHub Actions（如果尚未配置）。本变更不修改仓库设置、可见性或保护规则，不自动合并。计划地址为 `https://shyun-cc.github.io/shw-mui/`；准备工作流或本地构建成功均不等于该地址已上线。

首次部署后检查首页、讨论目录和深层页面的导航、样式、搜索与移动端显示。修改只应包含可公开内容，不放入私人聊天、内部标识或秘密。

## 本轮验证记录

使用上述固定版本完成生产构建（退出码 0），生成 20 个 Hugo 页面，其中 14 个 HTML 文件。检查 443 个本地链接和资源引用，均保留项目子路径且目标存在；九个讨论章节及搜索产物均存在。仅出现官方基线已说明的 LibSass 弃用警告。线上部署及浏览器交互验收尚未执行。
