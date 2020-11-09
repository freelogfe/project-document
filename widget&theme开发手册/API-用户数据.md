## 用户数据

### 用户数据获取 `window.FreelogApp.QI.getUserNodeData(params: {fields: string;})`

```js
// 获取key为keyPadSettings的用户数据
window.FreelogApp.QI.getUserNodeData({ fields: 'keyPadSettings' })
  .then(data => {})
```

### 用户数据存储 `window.FreelogApp.QI.setUserNodeData(data: {removeFields: string[]; appendOrReplaceObject: object;})`

```js
// 重置key为keyPadSettings的用户数据
window.FreelogApp.QI.setUserNodeData({ 
  appendOrReplaceObject: { 
    'keyPadSettings': {
      12: 'Up',
      13: 'Down',
      14: 'Left',
      15: 'Right',
    }
  } 
})

// 新增key为chapterInfo的用户数据
window.FreelogApp.QI.setUserNodeData({ 
  appendOrReplaceObject: { 
    'chapterInfo': {
      'intro': '罚款方式激发了卡升级法兰克福将阿拉山口放假啊发觉啊斯洛伐克'
    }
  } 
})

// 删除key为keyPadSettings的用户数据
window.FreelogApp.QI.setUserNodeData({ removeFields: 'keyPadSettings' })
```


