
## Freelog事件

| 事件名称 | 事件参数 | 事件说明 | 
| -- | -- | -- |
| HANDLE_INVALID_RESPONSE | { response }, callback | 处理errcode不等于0的响应结果 |
| HANDLE_INVALID_AUTH | { response }, callback  | 处理授权不通过的响应结果 |
| SHOW_SIGN_DIALOG | { presentableList, callback  } | 唤起资源签约弹窗 |
| GO_TO_LOGIN | {}, callback  | 触发后：跳转登陆页面 |
| NOTIFY_NODE | { msg }, callback  | 通知节点 |
| REPORT_ERROR | { error }, callback  | 上报错误 |

### 事件触发函数：window.FreelogApp.trigger(eventName[, options][, callback])

- 示例1: 请求presentable资源数据详情时，errocde不等于0

```js
window.FreelogApp.QI.fetchPresentableResourceData('5b5827622d800900294ab2cf')
  .then(res => {
    if(res.errcode === 0){
      // do something
    }else{
      window.FreelogApp.trigger('HANDLE_INVALID_RESPONSE', { response: res }, function callback() {
        // event done
      })
    }
  })
```

- 示例2: 唤起资源签约弹窗

```js
// 单个资源签约
window.FreelogApp.QI.fetchPresentableInfo('5b5827622d800900294ab2cf')
  .then(res => {
    if(res.errcode === 0){
      window.FreelogApp.trigger(
        'SHOW_SIGN_DIALOG', 
        { presentableList: [res] }, 
        function callback() {
          // event done
        }
      )
    }
  })

// 列表显示：多个资源签约
window.FreelogApp.QI.fetchPresentablesList()
  .then(res => {
    if(res.errcode === 0){
      window.FreelogApp.trigger(
        'SHOW_SIGN_DIALOG', 
        { presentableList: res.data }, 
        function callback() {
          // event done
        }
      )
    }
  })
```

- 示例3: 跳转登陆页面 

```js
window.FreelogApp.trigger('GO_TO_LOGIN', function callback() {})
```
