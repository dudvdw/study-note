// nvm run order
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion


## Node 版本管理

1. nvm管理
查看可以安装的node版本(官方所有能用版本)
nvm ls-remote

查看所有可以安装的LTS版本（长期支持版）
nvm ls-remote --lts

安装指定版本的 node
nvm install v9.5.0

v 后面是想要安装的版本号
查看已安装的node
nvm ls

切换 node 版本
nvm use v6.9.0

设定默认的node版本
nvm alias default v6.9.0
nvm use default

打开新的终端，用nvm current查看当前版本显示

删除指定版本的 node
nvm uninstall v9.5.0
此过程会花费一点时间

安装最新稳定版本


nvm install stable

Reference: https://segmentfault.com/a/1190000019097425


2. n 管理
全局安装 n
sudo npm install -g n
安装最新稳定版 node
sudo n stable
安装最新版本 node
sudo n latest
删除某个版本
n rm 10.13.0 
使用 n 切换版本
n   --回车
    node/10.13.0
  ο node/10.15.3
    node/11.0.0
    node/11.8.0
    node/12.2.0
# 按上下键选择版本后，回车
查看node版本
node -v
以指定的版本来执行脚本
n use 10.13.0  test.js

Reference：https://www.jianshu.com/p/a2ee8f61a8ca


使用n命令切换全局node版本 
n 12.13.0
nvm切换全局不好用，可切换当前执行环境node版本
nvm use v17.3.0


## npm 无法发包
npm login登录输入正确的username, password


## npm的tag
我们可以通过 npm dist-tag ls [<pkg>] 来查看一个包的tag，一般来说我们至少会有三种类型的标签
* latest：最后版本，npm install的就是这个
* beta：测试版本，一般内测使用，需要指定版本号install，例如3.1.0-beta.0
* next: 先行版本，npm install foo@next安装，例如3.0.2-alpha.0


如果我们需要发布一个测试版本，在发布的时候需要执行
npm publish --tag beta


如果你直接执行npm publish，那么即使你的版本号是-beta.n，默认会打上latest的标签，别人install的时候也会下载到。这个时候需要我们只要改一下tag：

// 不小心发错了
latest: 1.0.1-beta.0

// 将1.0.1-beta.0设置为beta
npm dist-tag add my-package@1.0.1-beta.0 beta
npm dist-tag add my-package@1.0.0 latest


https://juejin.im/post/5d09054f51882563194b302c

// 发布第一个稳定版本
npm publish

// 修改文件继续发布第二个版本
npm version patch

// 继续修改文件发布一个prerelease版本
npm version prerelease
npm publish —tag -beta

// npm info查看版本信息

https://blog.csdn.net/liangklfang/article/details/68947786