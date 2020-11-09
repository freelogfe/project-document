## 全局变量

### window.\_\_auth_info\_\_

|属性|类型|描述| 
|--|--|--|
| window.`__auth_info__`.`__auth_node_id__` | String | 节点ID |
| window.`__auth_info__`.`__auth_node_name__` | String | 节点名称 |
| window.`__auth_info__`.`__auth_user_id__` | String | 用户ID |
| window.`__auth_info__`.`__page_build_entity_id` | String | 主题的实体ID |
| window.`__auth_info__`.`__page_build_sub_releases` | Array | 主题依赖信息集合 |
| window.`__auth_info__`.`__auth_error_info__` | Object | 主题授权错误信息 |


### window.FreelogApp
| 属性 | 类型 | 描述 |
|--|--|--|
|window.FreelogApp.QI | Object | 查询接口对象 |
|window.FreelogApp.Env | Object | Freelog环境参数 |
|window.FreelogApp.on | Function | 事件绑定（监听）函数 |
|window.FreelogApp.once | Function | 事件绑定（监听）函数，只触发一次 |
|window.FreelogApp.trigger | Function | 事件触发函数 |
|window.FreelogApp.off | Function | 事件解绑函数 |
|window.FreelogApp.loadMicroApp | Function | 加载微应用 |
|window.FreelogApp.registerMicroApps | Function | 注册微应用 |

### window.FreelogApp.Env
| 属性 | 类型 | 描述 |
|--|--|--|
|window.FreelogApp.Env.isTest | Boolean | 是否为测试环境 |
|window.FreelogApp.Env.isMobile | Boolean | 是否为移动端 |leaguage
|window.FreelogApp.Env.leaguage | String | 语言环境 |
|window.FreelogApp.Env.nodeId | String | 节点id |
|window.FreelogApp.Env.mainDomain | String | 当前节点的一级域名 |
|window.FreelogApp.Env.qiOrigin | String | QI服务的origin |


