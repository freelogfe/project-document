## Query Interface

> freelog 提供的节点数据查询接口，可通过 window.FreelogApp.QI 调用

### window.FreelogApp.QI.fetch(url[, options])

对 window.fetch 的封装，通过 QI.fetch 进行的所有请求都将进行`参数组装`、`授权`和`请求头部补充`等一系列处理

- 参数 - 可参考[fetch](https://github.com/github/fetch)的参数说明

| 属性    | 类型   | 必填 | 说明     |
| ------- | ------ | ---- | -------- |
| url     | String | 是   | 请求 url |
| options | Object | 否   | -        |

- 示例

```javascript  
// 获取presentable详情
window.FreelogApp.QI.fetch(`/v1/presentables/${presentableId}`).then(res => {
  console.log(res);
});

```

### window.FreelogApp.QI.pagingGetPresentables(params)

分页获取节点的 presentable 列表

- 参数 Object object

| 属性                  | 类型   | 必填 | 说明                                                  |
| --------------------- | ------ | ---- | ----------------------------------------------------- |
| nodeId                | Number | 是   | 节点 ID                                               |
| isOnline              | Number | 否   | 是否上线(0:下线 1:上线 2:全部) 默认上线               |
| tags                  | String | 否   | 用户创建 presentable 时设置的自定义标签,多个用","分割 |
| resourceType          | String | 否   | 资源类型                                              |
| page                  | Number | 否   | 页码(默认为 1)                                        |
| pageSize              | Number | 否   | 每页数量 (默认为 10)                                  |
| keywords              | Number | 否   | 搜索关键字,目前支持模糊搜索节点资源名称和资源名称     |
| isLoadingResourceInfo | Number | 否   | 是否加载资源信息,1:是 0:否(默认)                      |

- Response字段说明 Object object

| 属性            | 类型   | 说明                                                  |
| --------------- | ------ | ----------------------------------------------------- |
| presentableId   | String | 节点资源 ID                                           |
| presentableName | String | 节点资源名称                                          |
| resourceId      | String | 方案对应的资源 ID                                     |
| userId          | Number | 创建方案的用户 ID                                     |
| nodeId          | Number | 节点 ID                                               |
| nodeName        | String | 节点名称                                              |
| policy          | Array  | 节点资源策略组 (示例数据仅做参考)                     |
| createDate      | String | 创建日期                                              |
| userDefinedTags | Array  | 用户定义的 tags                                       |
| contracts       | Array  | 当前 presentable 关联的执行合同                       |
| isOnline        | Number | 是否上线 0:否 1:是                                    |
| status          | Number | 状态 1:合同已完备 2:存在可用策略 总状态通过或运算获取 |

- 请求示例

```javascript
//默认请求当前节点第一页的资源（每页10条数据）
window.FreelogApp.QI.pagingGetPresentables().then(res => {
  console.log(res);
});

//请求当前节点资源类型为markdown的节点资源
window.FreelogApp.QI.pagingGetPresentables({
  resourceType: "markdown"
}).then(res => {
  console.log(res);
});
```

- 响应示例

```json
{
  "ret": 0,
  "errcode": 0,
  "msg": "success",
  "data": {
    "page": 1,
    "pageSize": 100,
    "totalItem": 2,
    "dataList": [
      {
        "presentableId": "5da43fcf7359ed0022d53afc",
        "userDefinedTags": [],
        "intro": "",
        "previewImages": [
          "https://image.freelog.com/preview/9ce79795-596c-40c9-8c2f-ec06a0ce61b6.jpg"
        ],
        "isOnline": 1,
        "contractStatus": 2,
        "status": 0,
        "presentableName": "Contra",
        "userId": 50018,
        "resolveReleases": [
          {
            "contracts": [
              {
                "contractId": "5da43fcfd431cd002912d898",
                "policyId": "1695c7481f58acefe31c967598000d53"
              }
            ],
            "releaseId": "5d6731f70f7937002bf43ee4",
            "releaseName": "ww-zh/Contra"
          }
        ],
        "policies": [
          {
            "authorizedObjects": [{ "userType": "GROUP", "users": ["PUBLIC"] }],
            "policyName": "免费策略",
            "status": 1,
            "policyText": "for public:\n  initial:\n    active\n    terminate",
            "policyId": "1695c7481f58acefe31c967598000d53"
          }
        ],
        "nodeId": 80000047,
        "releaseInfo": {
          "releaseId": "5d6731f70f7937002bf43ee4",
          "releaseName": "ww-zh/Contra",
          "resourceType": "nes",
          "version": "0.1.0",
          "previewImages": [
            "https://image.freelog.com/preview/9ce79795-596c-40c9-8c2f-ec06a0ce61b6.jpg"
          ],
          "versions": ["0.1.0"]
        },
        "createDate": "2019-10-14T09:28:47.414Z",
        "updateDate": "2019-11-25T07:01:19.586Z",
        "authResult": {
          "isAuth": true,
          "authCode": 201,
          "data": {},
          "errors": [],
          "freelog-sub-dependencies": "W10=",
          "freelog-entity-nid": "5da43fcf7359"
        }
      },
    ]
  }
}
```

### window.FreelogApp.QI.getPresentable(presentableId) 

获取单个 presentable 的详情

- 参数

| 属性          | 类型   | 必填 | 说明        |
| ------------- | ------ | ---- | ----------- |
| presentableId | String | 是   | 节点发行 ID |

- Response Headers字段说明

| 属性                     | 类型   | 说明                     |
| ------------------------ | ------ | ------------------------ |
| freelog-entity-nid       | String | presentbale 的实体 ID    |
| freelog-sub-dependencies | String | presentbale 的子依赖信息 |

- Response字段说明 Object object

| 属性            | 类型   | 说明                                                  |
| --------------- | ------ | ----------------------------------------------------- |
| presentableId   | String | 节点发行 ID                                           |
| presentableName | String | 节点资源名称                                          |
| resourceId      | String | 方案对应的资源 ID                                     |
| userId          | Number | 创建方案的用户 ID                                     |
| nodeId          | Number | 节点 ID                                               |
| nodeName        | String | 节点名称                                              |
| policy          | Array  | 节点资源策略组 (示例数据仅做参考)                     |
| createDate      | String | 创建日期                                              |
| userDefinedTags | Array  | 用户定义的 tags                                       |
| -- resourceName | String | 资源名称                                              |
| -- resourceType | String | 资源类型                                              |
| contracts       | Array  | 当前 presentable 关联的执行合同                       |
| isOnline        | Number | 是否上线 0:否 1:是                                    |
| status          | Number | 状态 1:合同已完备 2:存在可用策略 总状态通过或运算获取 |

- 请求示例

```javascript

window.FreelogApp.QI.getPresentable("5c1b5d9331d171002c66e6f4").then(res => {
  console.log(res);
});
```

- 响应示例

```json
{
  "ret": 0,
  "errcode": 0,
  "msg": "success",
  "data": {
    "presentableId": "5b0d1ca255d4055cf84bdb73",
    "presentableName": "presentableName",
    "resourceId": "2900eac4e4c8d96649901ac20a245b7bfa68ba8e",
    "userId": 10026,
    "nodeId": 10015,
    "nodeName": "demo",
    "createDate": "2018-05-29T09:25:54.043Z",
    "updateDate": "2018-05-30T08:10:30.236Z",
    "contracts": [
      {
        "resourceId": "2900eac4e4c8d96649901ac20a245b7bfa68ba8e",
        "authSchemeId": "5afb9e67f313cc4d88a3f9a1",
        "policySegmentId": "397c06bd49cb3712437890c9cdf8b222",
        "contractId": "5b0e4d772868266bb8055c1f"
      }
    ],
    "policy": [
      {
        "segmentId": "a68379dd361e74a89a37fce7a8b8d989",
        "policyName": "新的方案1",
        "segmentText": "for public: in <init> : terminate",
        "users": [
          {
            "userType": "group",
            "users": ["public"]
          }
        ],
        "fsmDescription": [
          {
            "currentState": "<init>"
          }
        ],
        "activatedStates": ["<init>"],
        "initialState": "<init>",
        "terminateState": "terminate",
        "status": 0
      }
    ],
    "userDefinedTags": ["tag1", "tag2"],
    "status": 0
  }
}
```

### window.FreelogApp.QI.batchGetPresentables(params)

根据发行 ID 或发行名称批量查询节点 presentable

- 参数 Object object

| 属性         | 类型   | 必填 | 说明                              |
| ------------ | ------ | ---- | --------------------------------- |
| releaseIds   | Number | 否   | 发行 ID，多个 ID 以逗号（,）隔开  |
| releaseNames | String | 否   | 发行名称，多个名称以逗号（,）隔开 |

- Response字段说明 Object object

| 属性            | 类型   | 说明                                                  |
| --------------- | ------ | ----------------------------------------------------- |
| nodeId          | Number | 节点 ID                                               |
| userId          | Number | 创建方案的用户 ID                                     |
| presentableId   | String | 节点资源 ID                                           |
| presentableName | String | 节点资源名称                                          |
| resourceId      | String | 方案对应的资源 ID                                     |
| nodeName        | String | 节点名称                                              |
| createDate      | String | 创建日期                                              |
| policy          | Array  | 节点资源策略组 (示例数据仅做参考)                     |
| userDefinedTags | Array  | 用户定义的 tags                                       |
| contracts       | Array  | 当前 presentable 关联的执行合同                       |
| isOnline        | Number | 是否上线 0:否 1:是                                    |
| status          | Number | 状态 1:合同已完备 2:存在可用策略 总状态通过或运算获取 |

- 请求示例

```javascript
// 根据发行名称
window.FreelogApp.QI.batchGetPresentables({
  releaseNames: [ "ww-zh/歌曲-陈绮贞-距离", "ww-zh/歌曲-郑钧-灰姑娘" ].join(",")
}).then(res => {
  console.log(res);
});
```

- 响应示例

```json
{
  "ret": 0,
  "errcode": 0,
  "msg": "success",
  "data": {
    "dataList": [
      {
        "presentableId": "9cf16950d6344d08f01fd34b1c66359c",
        "presentableName": "陈绮贞-距离",
        "previewImages": [
          "https://image.freelog.com/preview/9261f29b-1711-480b-a4f4-fdb9ae05409b.jpg"
        ],
        "intro": "",
        "isOnline": 1,
        "resourceType": "audio",
        "userDefinedTags": ["new-song"],
        "originInfo": {
          "version": "0.1.0",
          "versions": ["0.1.0"],
          "id": "5da81cce66acb1002b8b7dc0",
          "name": "ww-zh/歌曲-陈绮贞-距离",
          "type": "release"
        },
        "resolveReleases": [],
        "nodeId": 80000050,
        "userId": 50018,
        "updateDate": "2019-11-26T09:58:12.850Z",
        "createDate": "2019-11-26T09:58:12.850Z",
        "releaseInfo": {
          "releaseId": "5da81cce66acb1002b8b7dc0",
          "releaseName": "ww-zh/歌曲-陈绮贞-距离",
          "version": "0.1.0"
        },
        "authResult": {
          "isAuth": true,
          "authCode": 201,
          "data": {},
          "errors": [],
          "freelog-sub-dependencies": "W10=",
          "freelog-entity-nid": "9cf16950d634"
        }
      },
      {
        "presentableId": "b5cdfe9c58890b5f2728369f7b6ba6cd",
        "presentableName": "郑钧-灰姑娘",
        "previewImages": [
          "https://image.freelog.com/preview/0cbd6ff4-d381-4f5b-a39b-e62e9612797f.jpg"
        ],
        "intro": "",
        "isOnline": 1,
        "resourceType": "audio",
        "userDefinedTags": ["new-song"],
        "originInfo": {
          "version": "0.1.0",
          "versions": ["0.1.0"],
          "id": "5db0123876e5c3002bdb52f0",
          "name": "ww-zh/歌曲-郑钧-灰姑娘",
          "type": "release"
        },
        "resolveReleases": [],
        "nodeId": 80000050,
        "userId": 50018,
        "updateDate": "2019-11-26T09:58:12.852Z",
        "createDate": "2019-11-26T09:58:12.852Z",
        "releaseInfo": {
          "releaseId": "5db0123876e5c3002bdb52f0",
          "releaseName": "ww-zh/歌曲-郑钧-灰姑娘",
          "version": "0.1.0"
        },
        "authResult": {
          "isAuth": true,
          "authCode": 201,
          "data": {},
          "errors": [],
          "freelog-sub-dependencies": "W10=",
          "freelog-entity-nid": "b5cdfe9c5889"
        }
      }
    ]
  }
}
```

### window.FreelogApp.QI.getPresentableAuth(presentableId)

获取单个节点发行的授权结果

- 参数 Object object

| 属性          | 类型   | 必填 | 说明        |
| ------------- | ------ | ---- | ----------- |
| presentableId | String | 是   | 节点资源 ID |

- Response Headers字段说明

| 属性                     | 类型   | 说明                         |
| ------------------------ | ------ | ---------------------------- |
| freelog-entity-nid       | String | presentbale 的实体 ID        |
| freelog-sub-dependencies | String | presentbale 的子依赖信息     |
| freelog-resource-type    | String | presentbale 的资源类型       |
| freelog-meta             | String | presentbale 的资源 meta 信息 |

- 请求示例

```javascript
// 如获取节点中（presentableId为5c1b5d9331d171002c66e6f4）的授权结果
window.FreelogApp.QI.getPresentableAuth("5c1b5d9331d171002c66e6f4").then(res => {
  // todo
});
```

- 响应示例

```json
{
  "ret": 0,
  "errcode": 0,
  "msg": "success",
  "data": {
    "isAuth": true,
    "authCode": 201,
    "data": {},
    "errors": [],
    "freelog-sub-dependencies": "W3siaWQiOiI1ZDQyOWM3ZTBkYmRhNTAwMmE3YjY0ZDIiLCJuYW1lIjoiY2h0ZXMvaW1hZ2UwMSIsInR5cGUiOiJyZWxlYXNlIiwicmVzb3VyY2VUeXBlIjoiaW1hZ2UifSx7ImlkIjoiNWQ0MjljYTYwZGJkYTUwMDJhN2I2NGQ3IiwibmFtZSI6ImNodGVzL2ltYWdlIiwidHlwZSI6InJlbGVhc2UiLCJyZXNvdXJjZVR5cGUiOiJpbWFnZSJ9LHsiaWQiOiI1ZDQyOWNkNjBkYmRhNTAwMmE3YjY0ZGMiLCJuYW1lIjoiY2h0ZXMvaW1hZ2UwMiIsInR5cGUiOiJyZWxlYXNlIiwicmVzb3VyY2VUeXBlIjoiaW1hZ2UifSx7ImlkIjoiNWQ0MjlkMTAwZGJkYTUwMDJhN2I2NGUxIiwibmFtZSI6ImNodGVzL2ltYWdlMDMiLCJ0eXBlIjoicmVsZWFzZSIsInJlc291cmNlVHlwZSI6ImltYWdlIn0seyJpZCI6IjVkNDI5ZDNhMGRiZGE1MDAyYTdiNjRlNiIsIm5hbWUiOiJjaHRlcy9pbWFnZTA0IiwidHlwZSI6InJlbGVhc2UiLCJyZXNvdXJjZVR5cGUiOiJpbWFnZSJ9XQ==",
    "freelog-entity-nid": "1450feb3e49e"
  }
}
```

### window.FreelogApp.QI.getPresentableData(presentableId)

获取单个节点发行的数据内容；若资源授权未通过，则获取不成功。

- 参数 Object object

| 属性          | 类型   | 必填 | 说明        |
| ------------- | ------ | ---- | ----------- |
| presentableId | String | 是   | 节点资源 ID |

- Response Headers字段说明

| 属性                     | 类型   | 说明                                             |
| ------------------------ | ------ | ------------------------------------------------ |
| freelog-entity-nid       | String | presentbale 的实体 ID                            |
| freelog-sub-dependencies | String | presentbale 的子依赖信息                         |
| freelog-resource-type    | String | presentbale 的资源类型，授权未通过，不会有该头部 |
| freelog-meta             | String | presentbale 的资源 meta 信息                     |
| freelog-system-meta      | String | presentbale 的资源 meta 信息                     |

- 请求示例

```javascript
// 获取markdown资源的数据内容
window.FreelogApp.QI.getPresentableData("5c1b5d9331d171002c66e6f4").then((response) => {
  if (response.headers.get('freelog-resource-type') != null) {
    // 授权通过，获得markdown资源
    return response.text()
  } else {
    // 授权未通过
    return response.json()
  }
}); 
```

###  window.FreelogApp.QI.getPresentableSubDependData(presentableId, subDependId, entityId)

获取 presentable 的子资源的数据内容；

- 参数 Object object

| 属性          | 类型    | 必填 | 说明               |
| ------------- | ------ | ---- | ------------------ |
| presentableId | String | 是   | 节点发行 ID        |
| subDependId   | String | 是   | 节点发行子依赖 ID  |
| entityId      | String | 是   | 节点发行实体 ID    |

- 请求示例

```javascript
const [ presentableId, subDependId, entityId ] = [
  '1450feb3e49e365d35fe2486f92ddc5a',
  '5d429d100dbda5002a7b64e1',
  '1450feb3e49e'
]
window.FreelogApp.QI.getPresentableSubDependData(presentableId, subDependId, entityId).then(response => {
  // do something
});
```

## window.FreelogApp.QI.resolvePresentableDataUrl(presentableId)

通过presentableId获取presentable数据资源的url；

- 参数 Object object

| 属性 | 类型 | 必填 | 说明 | 
|--|--|--|--|
| presentableId | String | 是 | 节点资源ID | 

- 请求示例

```javascript
// 获取展品资源的url
const url = window.FreelogApp.QI.resolvePresentableDataUrl('1450feb3e49e365d35fe2486f92ddc5a')

```

## window.FreelogApp.QI.resolveSubDependDataUrl(presentableId, subDependId, entityId)

 获取presentable子依赖的数据内容的url；

- 参数 Object object

| 属性 | 类型 | 必填 | 说明 | 
|--|--|--|--|
| presentableId | String | 是   |  节点发行 ID       |
| subDependId   | String | 是   |  节点发行子依赖 ID |
| entityId      | String | 是   |  节点发行实体 ID   |

- 请求示例

```javascript
// 获取子依赖的url
const [ presentableId, subDependId, entityId ] = [
  '1450feb3e49e365d35fe2486f92ddc5a',
  '5d429d100dbda5002a7b64e1',
  '1450feb3e49e'
]
const url = window.FreelogApp.QI.resolveSubDependDataUrl(presentableId, subDependId, entityId)

```

### window.FreelogApp.QI.requireSubDepend(presentableId, subDependId, entityId)

该方法用于加载js、css资源，将`<Head>`标签插入`<script>`or `<link>`标签

- 参数 Object object

| 属性          | 类型   | 必填 | 说明               |
| ------------- | ------ | ---- | ------------------ |
| presentableId | String | 是   |  节点发行 ID       |
| subDependId   | String | 是   |  节点发行子依赖 ID |
| entityId      | String | 是   |  节点发行实体 ID   |

- 请求示例

```javascript
const [ presentableId, subDependId, entityId ] = [
  '5db6dac9ab5297001fa15f0a',
  '5d41380c7236940029e0de08',
  '5db6dac9ab52'
]
window.FreelogApp.QI.requireSubDepend(presentableId, subDependId, entityId)
    .then(() => {
      // 加载成功
    })
    .catch((e) => {
      // 加载失败
    })
```

### window.FreelogApp.QI.getUserInfo()

获取当前用户信息

- 请求示例

```javascript
// 获取用户信息
const userInfo = await window.FreelogApp.QI.getUserInfo()
```

- 响应示例

```json

{
  "email": "790727372@qq.com",
  "mobile": "",
  "headImage": "https://image.freelog.com/headImage/50018",
  "userType": 1,
  "status": 1,
  "username": "ww-zh",
  "userId": 50018,
  "tokenSn": "e7bb9c78b20644bfb789368c3dd14574",
  "createDate": "2019-05-14T07:08:23.539Z"
}

```


