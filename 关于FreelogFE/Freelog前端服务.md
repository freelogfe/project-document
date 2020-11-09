
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