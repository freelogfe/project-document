
## Freelog项目
### console.freelog.com管理后台项目
1. 功能：
    - 创建资源，发行资源
    - 添加发行策略、合同解析与执行、管理合同
    - 创建节点
2. 技术框架：Vue.js + Vue-router + vue-i18n + Vuex + Element-UI + axios 
3. 部分技术模块：
    - vue-codemirror: 基于codemirror实现web版代码编辑器；
    - vue-quill-editor: 基于 Quill、适用于 Vue 的富文本编辑器
    - crypto-js: 加密库
    - NProgress: “进度条”
    - cropper.js: 图片裁剪器（JavaScript image cropper）
4. 项目url:
    - 测试环境：http://console.testfreelog.com
    - 生产花镜：https://console.freelog.com

> 现在该项目已改为react + ts

> github仓库地址：
- 旧地址：https://github.com/freelogfe/freelogfe-web-repos/tree/master/packages/console.freelog.com
- 新地址：https://github.com/freelogfe/freelogfe-web-repos/tree/master/packages/console

### www.freelog.com管理后台项目
1. 功能：
    - 用户个人信息管理
    - 资金账户管理
    - 用户合约管理
2. 技术框架：Vue.js + Vue-router + vue-i18n + Vuex + Element-UI + axios 
3. 项目url:
    - 测试环境：http://www.testfreelog.com
    - 生产花镜：https://www.freelog.com

> github仓库地址：https://github.com/freelogfe/freelogfe-web-repos/tree/master/packages/www.freelog.com

### node.freelog.com前台项目
1. 功能：
    - 节点主题渲染
    - 节点主题异常场景处理
    - widget（即插件）加载、JS沙盒加载；
    - 提供Freelog Query Interface(简称QI)
    - Freelog资源授权签约UI
    - Freelog登录
    - 提供Freelog资源授权异常处理事件
2. 技术栈：Vue.js + vue-i18n + Element UI + axios + ts
3. 如何使用：项目打包后将部署至OSS，以供Freelog节点渲染服务调用。

> github仓库地址：https://github.com/freelogfe/freelogfe-web-repos/tree/master/packages/node.freelog.com

## Freelog 前端服务
### Freelog前端中间层服务
1. 技术栈：egg.js
2. 功能：
    - 为前端提供API：
    - 接口聚合、二次封装
    - 请求转发
3. 容器镜像服务
    - 测试环境：[fe-micro-server](https://cr.console.aliyun.com/repository/cn-shenzhen/freelog-test/fe-micro-server/details)（仓库名称），freelog-test（命名空间）
    - 生产环境：[fe-micro-server](https://cr.console.aliyun.com/repository/cn-shenzhen/freelog/fe-micro-server/details)（仓库名称），freelog（命名空间）
4. 容器服务：集群freelog-k8s/工作负载
    - 生产环境：[qi-freelog-gateway](https://cs.console.aliyun.com/index2#/k8s/cluster/cb8d5e354395446bdad8e129aeab54302/v2/workload/deployment/detail/development/qi-freelog-gateway/pods?type=deployment&clusterType=ManagedKubernetes&profile=&state=running&regionId=cn-shenzhen&ns=development&region=cn-shenzhen)（服务名称），development（命名空间）
    - 正式环境：[qi-freelog-gateway](https://cs.console.aliyun.com/index2#/k8s/cluster/cb8d5e354395446bdad8e129aeab54302/v2/workload/deployment/detail/production/qi-freelog-gateway/pods?type=deployment&clusterType=ManagedKubernetes&profile=&state=running&regionId=cn-shenzhen&ns=production&region=cn-shenzhen)（服务名称），production（命名空间）
5. 域名：
    - 测试环境：qi.testfreelog.com
    - 生产环境：qi.freelog.com

> github仓库地址：https://github.com/freelogfe/micro-server

### Freelog节点渲染
1. 技术栈：midway.js
2. 功能：
    - 节点访问授权查询
    - 节点主题异常处理
    - 获取节点主题与节点授权（依赖）配置，并直出在页面
3. 容器镜像服务
    - 测试环境：[freelog-node-render](https://cr.console.aliyun.com/repository/cn-shenzhen/freelog-test/freelog-node-render/details)（仓库名称），freelog-test（命名空间）
    - 生产环境：[freelog-node-render](https://cr.console.aliyun.com/repository/cn-shenzhen/freelog/freelog-node-render/details)（仓库名称），freelog（命名空间）
4. 容器服务：集群freelog-k8s/工作负载
    - 测试环境：[freelog-node-web](https://cs.console.aliyun.com/index2#/k8s/cluster/cb8d5e354395446bdad8e129aeab54302/v2/workload/deployment/detail/development/freelog-node-web/pods?type=deployment&clusterType=ManagedKubernetes&profile=&state=running&regionId=cn-shenzhen&ns=development&region=cn-shenzhen)（服务名称），development（命名空间）
    - 生产环境：[freelog-node-web](https://cs.console.aliyun.com/index2#/k8s/cluster/cb8d5e354395446bdad8e129aeab54302/v2/workload/deployment/detail/production/freelog-node-web/pods?type=deployment&clusterType=ManagedKubernetes&profile=&state=running&regionId=cn-shenzhen&ns=production&region=cn-shenzhen)（服务名称），production（命名空间）
5. 域名：
    - 测试环境：xxx.testfreelog.com（如：f-docs.testfreelog.com）
    - 生产环境: xxx.freelog.com（如：f-docs.freelog.com）

> github仓库地址：https://github.com/freelogfe/freelog-node-web

### Freelog内部文案（ii8n）管理服务
1. 技术栈：midway.js、nodegit
2. 功能：使开发、设计和产品可通过界面共同管理不同仓库项目的文案
3. 容器镜像服务
    - 测试环境：[freelog-i18n-test-service](https://cr.console.aliyun.com/repository/cn-shenzhen/freelog-test/freelog-i18n-test-service/details)（仓库名称），freelog-test（命名空间）
4. 容器服务：集群freelog-k8s/工作负载
    - 测试环境：[freelog-i18n-ts-service](https://cs.console.aliyun.com/index2#/k8s/cluster/cb8d5e354395446bdad8e129aeab54302/v2/workload/deployment/detail/development/freelog-i18n-ts-service/pods?type=deployment&clusterType=ManagedKubernetes&profile=&state=running&ns=development&region=cn-shenzhen)（服务名称），development（命名空间）
5. 域名：
    - 测试环境：i18n-ts.testfreelog.com

> github仓库地址：https://github.com/freelogfe/freelog-i18n-service

### Freelog数据上报服务
1. 采集性能数据
2. 容器镜像服务
    - 测试环境：[freelog-report-service](https://cr.console.aliyun.com/repository/cn-shenzhen/freelog-test/freelog-report-service/details)（仓库名称），freelog-test（命名空间）
3. 容器服务：集群freelog-k8s/工作负载
    - 测试环境：[freelog-report-service](https://cs.console.aliyun.com/index2#/k8s/cluster/cb8d5e354395446bdad8e129aeab54302/v2/workload/deployment/detail/development/freelog-report-service/pods?type=deployment&clusterType=ManagedKubernetes&profile=&state=running&ns=development&region=cn-shenzhen)（服务名称），development（命名空间）
4. 域名：
    - 测试环境：report.testfreelog.com

> github仓库地址：https://github.com/freelogfe/freelog-report-service

## 其他Freelog模块
- [@freelog/freelog-report](https://github.com/freelogfe/freelogfe-web-repos/tree/dev/packages/%40freelog/freelog-report)：性能数据打点与上报
- [@freelog/freelog-markdown-parser](https://github.com/freelogfe/freelogfe-lib-repos/tree/master/packages/freelog-markdown-parser)：MD文件Web编译、加载MD文件的Freelog资源
- [@freelog/freelog-ui-contract](https://github.com/freelogfe/freelogfe-web-repos/tree/dev/packages/%40freelog/freelog-ui-contract)：基于vue实现Freelog资源授权签约UI
- [@freelog/freelog-ui-login](https://github.com/freelogfe/freelogfe-web-repos/tree/dev/packages/%40freelog/freelog-ui-login): 基于vue实现Freelog用户登录UI
- [@freelog/freelog-policy-lang](https://github.com/freelogfe/freelogfe-web-repos/tree/dev/packages/%40freelog/freelog-policy-lang): freelog策略语言编译、格式化、美化
- [@freelog/nmr_translator](https://github.com/freelogfe/nmr_translator): 测试节点映射规则


## Freelog Widgets
> github仓库地址：https://github.com/freelogfe/freelogfe-widget-repos/tree/master/packages

> freelog主题示例节点：http://console.testfreelog.com/main/node-examples

### freelog-alpha-aside
左侧导航栏，支持侧栏弹出与收缩。

### freelog-alpha-blog
博客插件

> 示例节点地址：https://f-blog.freelog.com/#/

### freelog-alpha-comics
漫画插件，响应式布局，支持移动端

> 示例节点地址：https://f-comics.freelog.com/#/

### freelog-alpha-markdownviewer(旧版)
markdown阅读插件，支持渲染freelog  resource。

### freelog-widget-document2(新版)
新版markdown阅读插件，支持渲染freelog  resource。

> 示例节点地址：https://f-markdown.freelog.com/

### freelog-music-player(旧版-Deprecated)
### freelog-alpha-music
听音乐插件

> 示例节点地址：https://f-music.freelog.com/#/

### freelog-alpha-reader
书籍（小说）阅读插件

> 示例节点地址：https://f-novel.freelog.com/#/

### freelog-alpha-reveal
web版ppt插件

> 示例节点地址：https://p-slides.freelog.com/

### freelog-alpha-video
视频播放插件

> 示例节点地址：https://f-video.freelog.com/#/

### freelog-pagebuild-presentation
freelog主题（或插件）资源展示插件

> 示例节点地址：https://f-presentations.freelog.com/

### freelog-single-jsnes
web版红白机插件，可自定义配置按键

> 示例节点地址：https://f-nes.freelog.com/

### freelog-waterfall-picture
图片瀑布流插件，图片资源展示

> 示例节点地址：https://f-images.freelog.com/#/

### freelog-widget-docs（旧版）
markdown文档插件

### freelog-widget-document (新版)
新版markdown文档插件，可配置左侧导航目录

> 示例节点地址：https://f-docs.freelog.com/#

### freelog-video-player
视频播放插件

### freelog-i18n-management
freelog项目i18n管理插件，须配合`Freelog内部文案（ii8n）管理服务`使用。

> 示例节点地址：http://f-i18n.testfreelog.com



## Freelog工具
### [@freelog/freelog-ci](https://github.com/freelogfe/freelogfe-lib-repos/tree/master/packages/freelog-ci)
项目本地编译、构建及部署

### [@freelog/freelog-cli](https://github.com/freelogfe/freelogfe-lib-repos/tree/master/packages/%40freelog/cli)
widget开发脚手架，用于快速创建widget开发项目

### [@freelog/cli-service](https://github.com/freelogfe/freelogfe-lib-repos/tree/master/packages/%40freelog/cli-service)
widget本地开发服务

### [@freelog/freelog-component-template](https://github.com/freelogfe/freelog-widget-template)
widget开发模版

### [@freelog/freelog-scripts](https://github.com/freelogfe/freelogfe-lib-repos/tree/master/packages/%40freelog/cli-scripts)
theme、widget资源发布

### [xproxy](https://www.npmjs.com/package/xproxy)
基于node.js实现的本地代理工具

> freelog内部使用的代理配置

```
const path = require('path')
const CWD = process.cwd()

const [ CONSOLE_PORT, WWW_PORT, NODE_PORT, WIDGET_PORT, DEFAULT_PORT ] = [ "8880", "9880", "9888", "9180", "9880" ]

function getPort(urlObject) {
  return urlObject.protocol === 'https:' ? '443' : '880'
}

function getPortByPath(staticPath) {
  if(/console/.test(staticPath)) {
    return CONSOLE_PORT
  }else if(/www/.test(staticPath)){
    return WWW_PORT
  }else if(/pagebuild/.test(staticPath)) {
    return NODE_PORT
  }else {
    return DEFAULT_PORT
  }
}í

module.exports = {
  root: CWD,
  urls: [
    {
      // freelog资源映射
      rule: /5efc2e425ceb260020f97753\/data\?nodeId=80000057&nodeType=formal/,
      target: function() {
        return `~/FrontEnd/freelogfe/freelog-docs/widget&theme开发手册/节点数据获取.md`
      }, 
      headers: function (ctx) {
        ctx.set('access-control-allow-origin', ctx.req.headers.origin || '*')
        ctx.set('Access-Control-allow-Headers', 'Content-Type')
        ctx.set('freelog-entity-nid', '5ea7f1ef0e7c')
        ctx.set('freelog-resource-type', 'markdown')
        ctx.set('freelog-sub-dependencies','W3siaWQiOiI1ZDQyOWM3ZTBkYmRhNTAwMmE3YjY0ZDIiLCJuYW1lIjoiY2h0ZXMvaW1hZ2UwMSIsInR5cGUiOiJyZWxlYXNlIiwicmVzb3VyY2VUeXBlIjoiaW1hZ2UifSx7ImlkIjoiNWQ0MjljYTYwZGJkYTUwMDJhN2I2NGQ3IiwibmFtZSI6ImNodGVzL2ltYWdlIiwidHlwZSI6InJlbGVhc2UiLCJyZXNvdXJjZVR5cGUiOiJpbWFnZSJ9LHsiaWQiOiI1ZDQyOWNkNjBkYmRhNTAwMmE3YjY0ZGMiLCJuYW1lIjoiY2h0ZXMvaW1hZ2UwMiIsInR5cGUiOiJyZWxlYXNlIiwicmVzb3VyY2VUeXBlIjoiaW1hZ2UifSx7ImlkIjoiNWQ0MjlkMTAwZGJkYTUwMDJhN2I2NGUxIiwibmFtZSI6ImNodGVzL2ltYWdlMDMiLCJ0eXBlIjoicmVsZWFzZSIsInJlc291cmNlVHlwZSI6ImltYWdlIn0seyJpZCI6IjVkNDI5ZDNhMGRiZGE1MDAyYTdiNjRlNiIsIm5hbWUiOiJjaHRlcy9pbWFnZTA0IiwidHlwZSI6InJlbGVhc2UiLCJyZXNvdXJjZVR5cGUiOiJpbWFnZSJ9XQ==')
        ctx.set('access-control-expose-headers', 'freelog-resource-type,freelog-sub-resource-auth-token,freelog-sub-resourceids,freelog-meta,freelog-sub-dependencies,freelog-entity-nid')
      }
    },
    {
      // 上报服务
      rule: /\/v1\/report\/(.+)/,
      target: function (urlPath, match, urlObject) {
        return 'http://127.0.0.1:7112$'
      },
    },
    {
      // i18n管理服务
      rule: /\/v1\/(i18nKeyInfos|trackedRepositories|i18nRepository)/,
      // target: '~/workplace/mock/404'
      target: function (urlPath, match, urlObject) {
        const host = urlObject.host
        if (urlObject.protocol === 'https:') {
          return 'http://127.0.0.1:7111$'
        } else {
          return 'http://127.0.0.1:7111$'
        }
        
      },
    },
    {
      // 前端节点渲染服务
      rule: /\/(nodeRender)\/?(.+)/,
      target: function(url, match, urlObject) {
        return `http://127.0.0.1:7002$`
      }
    },
    {
      // 中间层服务
      rule: /\/(v1)\/(.+)/,
      target: function (urlPath, match, urlObject) {
        if (urlObject.protocol === 'https:') {
          return 'http://127.0.0.1:7001$'
        } else {
          return 'http://127.0.0.1:7001$'
        }
      },
      headers: function (ctx) {
        ctx.set('Access-Control-Allow-Origin', ctx.req.headers.origin || '*')
        ctx.set('Access-Control-Expose-Headers', 'freelog-resource-type,freelog-sub-resource-auth-token,freelog-sub-releases,freelog-meta,freelog-sub-dependencies,freelog-entity-nid')
      }
    },
    {
      // 前台项目映射
      rule: /^(.*)$/,
      target: function (urlPath, match, urlObject) {
        const mArr = urlObject.host.match(/([\w-]+)\.(test)?freelog\.com/)
        if(mArr !== null) {
          let targetUrl = ''
          let isJs = path.extname(urlPath) === '.js'
          let isCss = path.extname(urlPath) === '.css'
          switch (mArr[1]) {
            case 'www': {
              targetUrl = `http://127.0.0.1:${WWW_PORT}${urlPath}`
              break
            }
            case 'console': {
              targetUrl = `http://127.0.0.1:${CONSOLE_PORT}${urlPath}`
              break
            }
            case 'static': {
              const port = getPortByPath(urlPath)
              if(isJs) {
                console.log('Static -', urlPath)
                if(/freelog-common/.test(urlPath)) {
                  targetUrl = `http://127.0.0.1:${NODE_PORT}/freelog-common.js`
                }else {
                  urlPath = `/${urlPath.replace(/\.\w+\./, '.')}`
                  targetUrl = `http://127.0.0.1:${port}${urlPath}`
                }
              }
              if(isCss) {
                urlPath = urlPath.replace(/(\/?console)|(\/?www)|(\/?pagebuild)/, '')
                targetUrl = `http://127.0.0.1:${port}${urlPath}`
              }
              break
            }
            case 't.local': 
            case 'local': {
              targetUrl = `http://127.0.0.1:${WIDGET_PORT}${urlPath}`
              break
            }
            default: {
              targetUrl = `http://127.0.0.1:${DEFAULT_PORT}${urlPath}`
            }
          }
          return targetUrl
        }
        return path.join(CWD, urlPath)
      },
      headers: function (ctx) {
        ctx.set('access-control-allow-origin', ctx.req.headers.origin || '*')
      }
    }
  ]
}


```


