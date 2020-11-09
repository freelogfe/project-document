
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

```js
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


