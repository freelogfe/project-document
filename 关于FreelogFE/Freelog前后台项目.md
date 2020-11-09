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

#### 节点渲染架构图
![](http://freelog-image.oss-cn-shenzhen.aliyuncs.com/%E8%8A%82%E7%82%B9%E6%B8%B2%E6%9F%93%E5%9B%BE.png)

#### 节点渲染工作流程
![](http://freelog-image.oss-cn-shenzhen.aliyuncs.com/Freelog%E8%8A%82%E7%82%B9%E5%B7%A5%E4%BD%9C%E6%B5%81%E7%A8%8B.jpg)
