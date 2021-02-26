title: node版本控制工具nvm
author: 汪秋月
tags: []
categories:
  - 工具
date: 2019-08-14 10:27:00
---
## 安装 nvm

- 安装

```
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash
```

- 验证nvm安装完成

```
command -v nvm
```

如果安装完成，就会显示如下

```
nvm
```

## 查看 nvm 可以安装的 node 版本


- 查看可以安装的版本

```
nvm ls-remote
```

- 查看所有可以安装的LTS版本（长期支持版）

```
nvm ls-remote --lts
```

## 安装指定版本的 node

官方推荐的安装方式 nvm install <版本号>

```
$ nvm install v5.5.0
```

但是推荐使用速度更快的方式：使用淘宝源安装

```
$ NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node nvm install 6
```

默认会安装一个系列中最新的版本

```
$ NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node nvm install 6     
Downloading and installing node v6.10.2...
Downloading https://npm.taobao.org/mirrors/node/v6.10.2/node-v6.10.2-darwin-x64.tar.gz...
######################################################################## 100.0%
Computing checksum with shasum -a 256
Checksums matched!
Now using node v6.10.2 (npm v3.10.10)
Creating default alias: default -> 6 (-> v6.10.2)
```

也可以在最后指定版本号

```
$ NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node nvm install 6.10.2
```
```
$ NVM_NODEJS_ORG_MIRROR=https://npm.taobao.org/mirrors/node nvm install 7.9.0
Downloading and installing node v7.9.0...
Downloading https://npm.taobao.org/mirrors/node/v7.9.0/node-v7.9.0-darwin-x64.tar.gz...
######################################################################## 100.0%
Computing checksum with shasum -a 256
Checksums matched!
Now using node v7.9.0 (npm v4.2.0)
```

## 查看已经安装的 node

查看安装的版本 nvm ls

```
$ nvm ls
        v6.10.2
->       v7.9.0
default -> 6 (-> v6.10.2)
node -> stable (-> v7.9.0) (default)
stable -> 7.9 (-> v7.9.0) (default)
```

也可以通过目录查看

```
/Users/macroot [macroot@macroots-MacBook-Pro] [9:06]
> ls -a ~/.nvm/versions/node
.       ..      v6.10.2 v7.9.0
```

## 切换 node 版本

切换node版本 nvm use <版本号>

切换至指定版本

```
$ nvm use v6.10.2
Now using node v6.10.2 (npm v3.10.10)
```

用node -v确认
```
$ node -v 
v6.10.2
```
## 设定默认的 node 版本

设定默认的node版本 nvm alias default <版本号>
```
$ nvm alias default v6.6.0
default -> v6.6.0
```

打开新的终端，用nvm current查看当前版本显示
```
$ nvm current

v6.6.0
```
## 卸载指定版本的 node

- 用户权限提升

当使用nvm uninstall <node版本号>的时候，通常会被提示：
```
$ nvm uninstall v6.6.0
file is not writable or self-owned: $NVM_DIR/versions/node/v6.6.0/bin/cnpm
Cannot uninstall, incorrect permissions on installation folder.
This is usually caused by running `npm install -g` as root. Run the following commands as root to fix the permissions and then try again.

  chown -R username "$NVM_DIR/versions/node/v6.6.0"
  chmod -R u+w "$NVM_DIR/versions/node/v6.6.0"
```

最后两行的意思是：

第1行：把指定目录的所有者改为 username 所有，这里 username 是用户名，可以改成 $(whoami) 避免输入错误。所以先输入以下命令（使用sudo）：
```
$ sudo chown -R $(whoami) "$NVM_DIR/versions/node/v6.6.0"
```
第2行：u+w中u表示所有者，+表示增加权限，w表示可写入。整句表示对目录所有者增加写入权限。所以再输入（使用sudo）：
```
$ sudo chmod -R u+w "$NVM_DIR/versions/node/v6.6.0"      
```

- 删除指定版本 node

当用户有了权限之后，就可以删除指定版本的 node
```
$ nvm uninstall v6.6.0
Uninstalled node v6.6.0
```














