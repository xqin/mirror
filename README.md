MIRROR
---

## 功能

反向代理 `http://npm.taobao.org/mirrors` 中的文件, 并利用 `nginx` 的 `proxy_store` 功能将文件缓存至本地, 以加快再次使用时的下载速度.


## 部署

```
# 启动服务
docker-compose up -d
```

## 测试


替换下面的 `localhost` 为服务部署后的真实域名或者IP地址.

> 注意路径后面的内容不要修改(不要尝试在后面增加 `/` 或者删除 `/`).

```
export SASS_BINARY_SITE=http://localhost/node-sass
export PHANTOMJS_CDNURL=http://localhost/phantomjs
export CHROMEDRIVER_CDNURL=http://localhost/chromedriver
export ELECTRON_MIRROR=http://localhost/electron/
export npm_config_node_sqlite3_binary_host_mirror=http://localhost/
export PUPPETEER_DOWNLOAD_HOST=http://localhost
export SENTRYCLI_CDNURL=http://localhost/sentry-cli
export npm_config_canvas_binary_host_mirror=http://localhost/node-canvas-prebuilt
```

或者项目目录中创建 `.npmrc` 文件, 内容如下:

```
sass_binary_site=http://localhost/node-sass
phantomjs_cdnurl=http://localhost/phantomjs
chromedriver_cdnurl=http://localhost/chromedriver
electron_mirror=http://localhost/electron/
node_sqlite3_binary_host_mirror=http://localhost/
puppeteer_download_host=http://localhost
sentrycli_cdnurl=http://localhost/sentry-cli
canvas_binary_host_mirror=http://localhost/node-canvas-prebuilt
```


命令行中执行上面的命令配置相关的环境变量或者项目中创建相应的文件后, 执行下面的命令, 进行测试:

```
npm install -dd node-sass \
  phantomjs \
  chromedriver \
  electron \
  sqlite3 \
  puppeteer \
  @sentry/cli \
  canvas
```
