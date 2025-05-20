# 创业分析平台

本项目是一个多端应用，前端基于 Vue.js + Element UI 框架。后端是一个微服务架构，通过Docker容器化部署将基于Python、Java、Node.js的应用进行集成（包含SpiderFlow爬虫、Superset数据分析、NocoBase数据库、Dify-AI模型）。前后端间通过 Axios 库进行API通信

详细解析可以看https://blog.csdn.net/2301_78856868/article/details/147749386?sharetype=blogdetail&sharerId=147749386&sharerefer=PC&sharesource=2301_78856868&spm=1011.2480.3001.8118

如有问题随时联系我：3506456886@qq.com

## 系统组件

### 后端服务
- **NocoBase**: 低代码平台作为后端数据管理系统
- **爬虫系统**: 基于Spider-Flow的数据爬取组件
- **数据分析**: 基于Superset的数据分析和可视化工具

### AI模型
- **创业分析模型**: 基于Python的创业公司分析和评估模型

### 前端展示
- **Web端**: 基于HTML/CSS/JavaScript的Web前端
- **小程序端**: 微信小程序界面

## 启动方法

### 0. 一键启动
在PowerShell中执行：
```
.\start_all_services.ps1
```
会依次启动NocoBase后端、数据分析服务(Superset)、爬虫系统(Spider-Flow)和AI模型服务，并提供选项启动Web端。


### 1. 启动NocoBase后端
```
cd 后端服务/nocobase
docker-compose up -d
```

### 2. 启动数据分析服务
```
cd 后端服务/数据分析/superset
docker-compose up -d
```

### 3. 启动爬虫系统
```
cd 后端服务/爬虫系统/spider-flow
docker-compose up -d
```

### 4. 构建并启动AI模型
```
cd AI模型/simple_model
docker build -t startup-analysis-model .
docker run -d -p 5000:5000 --name ai-model startup-analysis-model
```

### 5. 访问Web端
启动HTTP服务器并访问
```
cd web端
.\run_server.bat  或运行  powershell -ExecutionPolicy Bypass -File start_server.ps1
```
然后在浏览器中访问 http://localhost:3000

### 6. 开发小程序端
使用微信开发者工具打开 `小程序端/mybricks-app` 目录进行开发与预览

## 系统访问

- **NocoBase管理界面**: http://localhost:8000/
- **Superset数据分析平台**: http://localhost:8088/
- **AI模型API**: http://localhost:5000/
- **Web端**: http://localhost:3000/
- **小程序端**: 通过微信开发者工具预览
