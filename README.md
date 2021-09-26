# 友情链接（模版）

https://geneasy.github.io/links

此友情链接页面是使用 [GenEasy](https://github.com/geneasy/geneasy) 文档生成工具 + [WebStack](https://github.com/WebStackPage/WebStackPage.github.io) 模版创建的静态页面，托管在 GitHub Pages 服务器上面。

当修改 `links.yml` 文件里的内容时，**GitHub Actions** 会自动更新 HTML 文件。不需要服务器，不需要数据库。

## 如何在我的网站里加入这个友情链接页面？

第一步：fork 这个项目

第二部：进入 Settings > Pages, 启用 GitHub Pages 功能。分支选择 `gh-pages`。

第三部：访问你的 GitHub Pages 域名，看看是否正常显示。`https://你的用户名.github.io/links`

第四部：

4.1 如果你的网站是托管在 GitHub Pages 上面，配置已经结束

4.2 如果你的网站部署在自己的服务器，需要添加一段 proxy 代码。

以下是 nginx 代码示例

```
location /links/ {
    proxy_pass      https://你的用户名.github.io/links/index.html;
    proxy_intercept_errors on;

    # allow GitHub to pass caching headers instead of using our own
    expires off;
    proxy_set_header   Host                   你的用户名.github.io;
    proxy_set_header   X-Host                 你的用户名.github.io;
}
```

访问你的网站，确认是否成功。`https://你的域名/links/`

4.3 如果你的网站是托管在 Vercel, Netlify 等静态页面托管平台，需要添加部署到这些平台的 GitHub Action。

```yml
name: Build and Deploy
on:
  push:
    branches:
      - gh-pages
jobs: ...
```

访问你的网站，确认是否成功。`https://你的域名/links/`

## Tip: 如何修改 `links.yml`

### 方法 1

把项目下载到本地，修改提交。

### 方法 2

把现在 GitHub repository 的 URL 里的 `github.com` 改成 `github.dev`，会进入 web 版的 VS Code。在 web 版的 VS Code 里修改提交。

### 方法 3

在 GitHub 点击 [`links.yml`](links.yml) 文件，然后点击编辑按钮。修改提交。

## Tip: 如何在本地修改数据，查看效果

1. clone 项目到本地
2. 安装 `geneasy`
```sh
npm i -g geneasy
```
3. 执行下面命令生成 `index.html`
```sh
geneasy -t index.hbs -o public/index.html links.yml
```
4. 执行 `geneasy server` 命令启动 web 服务器，访问 `http://127.0.0.1:8080` (端口看终端日志输出内容)

## 需要帮助？

如果遇到问题，需要帮助，请添加 [issue](https://github.com/geneasy/links/issues)。

## License

Copyright (c) 2021 [Pipecraft][my-url]. Licensed under the [MIT license][license-url].

## >\_

[![Pipecraft](https://img.shields.io/badge/https://-pipecraft.net-brightgreen)](https://www.pipecraft.net)
[![PZWD](https://img.shields.io/badge/https://-pzwd.net-brightgreen)](https://pzwd.net)

[my-url]: https://www.pipecraft.net
[license-url]: LICENSE
