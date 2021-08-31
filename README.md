# Aurora-DriveSyncer

![logo](https://github.com/Aurora-DriveSyncer/Aurora-DriveSyncer/raw/master/img/logo.png)


## 扩展要求

各项目组根据自身情况自行选择扩展要求(对应扩展分)。

* **服务器备份(5-10分)**:搭建服务器，允许用户将指定文件或目录备份到服务器。
* **压缩解压(5-10分)**:通过文件压缩节省备份文件的存储空间
* 打包解包(5-10分):将所有备份文件拼接为一个大文件保存
* 自定义备份(5-10分):允许用户指定仅备份目录树中的部分文件
* **加密备份(5-10分)**:由用户指定密码，将所有备份文件均加密保存
* **增量备份(5-10分)**:每次备份操作仅备份变化文件，以减少负担(主要是网络)
* **实时备份(5-10分)**:自动感知用户文件变化，进行自动备份
* **网盘备份(10-20分)**:将数据备份软件从单机模式扩展为C/S模式(网盘)
* 其它功能:视功能难度讨论加分。

## 开发环境

* 操作系统选择:Linux/Mac/Windows
* 开发语言选择:C++/Java/Go/Dart。若选择脚本语言，小组基础分扣10分。
* 库的使用:对所有扩展功能，如果使用第三方库/代码实现，只能获得最低扩展分。

## 项目取名

Aurora

## 技术架构

* 前端：部署在同步机本地 `localhost:8080`。显示同步状态、修改同步配置等
* 后端：部署在同步机本地 `localhost:18080`，监听文件变化；对文件服务器加密、压缩、传输文件；对前端提供 REST API
* 文件服务器：部署在远端 `localhost:28080`，ftp/webdav

## REST API

1. GET `/api/list/` 获取指定文件夹中的内容及同步状态
2. GET `/api/download/` 从备份服务器下载文件
3. GET `/api/syncing/` 获取正在同步的位置
4. GET & PUT `/api/config/` 显示和修改同步配置

## 前端

三个页面：

1. 登录、修改配置
2. 文件浏览器
3. 查看上传任务

文件浏览器的原型图如下：

![file-explorer](https://github.com/Aurora-DriveSyncer/Aurora-DriveSyncer/raw/master/img/file-explorer.jpg)

## 后端

1. 上述四个 API 以及对应的 swagger
2. ftp/webdav 登录/上传/删除
3. 加密解密
4. 压缩解压
5. 计算 hash
6. 监听文件增/删/移动

