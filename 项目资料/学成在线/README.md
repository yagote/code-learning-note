# 学成在线项目-整体架构配置笔记

## 1. 项目文档

<ul class="docs">
  <li><a href="#/项目资料/学成在线/Day01-CMS接口开发">Day01-CMS接口开发</a></li>
  <li><a href="#/项目资料/学成在线/Day02-CMS前端开发">Day02-CMS前端开发</a></li>
  <li><a href="#/项目资料/学成在线/Day03-CMS页面管理开发">Day03-CMS页面管理开发</a></li>
  <li><a href="#/项目资料/学成在线/Day04-页面静态化-freemarker">Day04-页面静态化-freemarker</a></li>
  <li><a href="#/项目资料/学成在线/Day05-消息中间件-RabbitMQ">Day05-消息中间件-RabbitMQ</a></li>
  <li><a href="#/项目资料/学成在线/Day06-页面发布-课程管理（RabbitMQ实践）">Day06-页面发布-课程管理（RabbitMQ实践）</a></li>
  <li><a href="#/项目资料/学成在线/Day07-课程管理功能模块">Day07-课程管理功能模块</a></li>
  <li><a href="#/项目资料/学成在线/Day08-课程图片管理&分布式文件系统">Day08-课程图片管理&分布式文件系统</a></li>
  <li><a href="#/项目资料/学成在线/Day09-课程预览&Eureka、Feign、Ribbon使用">Day09-课程预览&Eureka、Feign、Ribbon使用</a></li>
  <li><a href="#/项目资料/学成在线/Day11-搜索服务">Day11-搜索服务</a></li>
  <li><a href="#/项目资料/学成在线/Day16-SpringSecurityOauth2认证方案&JWT研究">Day16-SpringSecurityOauth2认证方案&JWT研究</a></li>
  <li><a href="#/项目资料/学成在线/Day17-用户认证&Zuul网关">Day17-用户认证&Zuul网关</a></li>
  <li><a href="#/项目资料/学成在线/Day18-用户授权">Day18-用户授权</a></li>
</ul>

## 2. 项目git库与分支管理

### 2.1. 项目后端git库

- git库地址：git@github.com:MooNkirA/xc-edu-project-service.git

### 2.2. 项目前端git库

- git库地址：git@github.com:MooNkirA/xc-edu-project-ui.git

### 2.3. 本项目的分支命名规范

- `master`：主分支，永远是可用的、稳定的、可直接发布的版本，不能直接在该分支上开发。只有计划发布的版本功能在develop分支上全部完成，而且测试没有问题了才会合并到master上。
- `develop`：开发主分支，代码永远是最新，所有新功能以这个分支来创建自己的开发分支，该分支只做只合并操作，不能直接在该分支上开发
- `feature-xxx`：功能开发分支，在develop上创建分支，以自己开发功能模块命名，功能测试正常后合并到develop分支

本项目主要分支情况

- master主版本分支
- develop开发分支
- feature-dayxx功能分支，以每天的功能为单位做为分支

## 3. 项目数据库与相关中间件

### 3.1. Nginx

- 本机安装：D:\development\nginx-1.14.2-xc-edu\

### 3.2. mongodb 数据库

#### 3.2.1. 本机部署（已删除）

- ~~本机部署地址：http://localhost:27017~~
- ~~用户所属数据库：admin 用户名：root 密码：123~~

#### 3.2.2. docker版部署（mongoDb 4.0.18）

- 部署地址：http://192.168.12.132:27017
- 用户所属数据库：admin 用户名：root 密码：123

### 3.3. RabbitMQ

- 部署地址（centOS练习虚拟机）：http://192.168.12.132:15672
- 用户名/密码：guest/guest

## 4. 项目各模块配置url与域名

### 4.1. 前端ui模块url与端口

- 本机xc-ui-pc-static-portal 学成网静态门户页面
    - url：http://127.0.0.1:80
    - 映射域名：www.xuecheng.com
- 本机xc-ui-pc-sysmanage CMS前端管理系统
    - url：http://127.0.0.1:11000
- 本机xc-ui-pc-teach 教学管理中心前端系统
    - url：http://127.0.0.1:12000
- 本机xc-ui-pc-leanring 学习中心前端系统
    - url：http://127.0.0.1:13000
    - 映射域名：ucenter.xuecheng.com

### 4.2. 后端服务url与端口

- 本机xc-service-manage-cms CMS管理微服务
    - url：http://127.0.0.1:31001
    - Swagger：http://127.0.0.1:31001/swagger-ui.html
- 本机xc-service-manage-cms-client CMS管理客户端微服务
    - url：http://127.0.0.1:31000
    - Swagger：http://127.0.0.1:31000/swagger-ui.html
- 本机xc-service-manage-course 课程管理微服务
    - url：http://127.0.0.1:31200
    - Swagger：http://127.0.0.1:31200/swagger-ui.html
- 本机xc-service-base-filesystem 文件管理系统服务
    - url：http://127.0.0.1:22100
    - Swagger：http://127.0.0.1:22100/swagger-ui.html
- 本机xc-service-ucenter-auth 用户认证服务
    - url：http://localhost:40400/auth
- 本机xc-service-ucenter 用户中心
    - url：http://127.0.0.1:40300
    - Swagger：http://127.0.0.1:40300/swagger-ui.html
- 本机xc-govern-gateway 网关服务
    - url：http://127.0.0.1:50201/api
- 本机xc-search-service 搜索服务
    - url: http://127.0.0.1:40100

### 4.3. 注册中心Eureka

- 本机eureka01：：http://127.0.0.1:50101
- 本机eureka02：：http://127.0.0.1:50102

### 4.4. 配置hosts文件

```shell
# 学成在线项目配置域名
127.0.0.1  www.xuecheng.com
192.168.12.132  img.xuecheng.com
127.0.0.1  eureka01
127.0.0.1  eureka02
```

## 5. 待处理
### 5.1. 未实现功能

- day03 查看6.待完善功能

### 5.2. 暂存数据
#### 5.2.1. cms_config文档-首页轮播图原数据备份

```json
{
    "_id" : ObjectId("5a791725dd573c3574ee333f"),
    "_class" : "com.xuecheng.framework.domain.cms.CmsConfig",
    "name" : "轮播图",
    "model" : [
        {
            "key" : "banner1",
            "name" : "轮播图1地址",
            "value" : "http://192.168.101.64/group1/M00/00/01/wKhlQFp5wnCAG-kAAATMXxpSaMg864.png"
        },
        {
            "key" : "banner2",
            "name" : "轮播图2地址",
            "value" : "http://192.168.101.64/group1/M00/00/01/wKhlQVp5wqyALcrGAAGUeHA3nvU867.jpg"
        },
        {
            "key" : "banner3",
            "name" : "轮播图3地址",
            "value" : "http://192.168.101.64/group1/M00/00/01/wKhlQFp5wtWAWNY2AAIkOHlpWcs395.jpg"
        }
    ]
}
```

3. 编写模板，在freemarker测试工程中新建模板index_banner.ftl


#### 5.2.2. 文件系统已上传的图片

- group1/M00/00/00/wKgMhF1I8bKAK_sfAABgUAnk0N8760.jpg
- group1/M00/00/00/wKgMhF1GLFWADYpFAAC8U7Yhv9Q90.jpeg
- group1/M00/00/00/wKgMhF1H41mASy-oAABDrkH14Dc231.png
