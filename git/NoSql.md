[toc]

#GitHub使用

##安装Git客户端
----
[Git安装教程](http://jingyan.baidu.com/article/7f766dafba84f04101e1d0b0.html)
###克隆项目
    安装完之后，在电脑新建一个文件夹，右键会出现Git Gui、Git Bash。在建好的文件夹里面右键Git bash 就出现命令行，可以输入支持git 的命令行了。
    回到github，看别人的项目如果觉得好可以fork到自己github账户下,比如说weibao这个项目，点击forkGitHub自动跳转到二级域名
```html
https://www.github/youname/weibaopro
```
![](leanote://file/getImage?fileId=567b6203ab64416467005fbb)

选择HTTPS复制上面的链接，这个链接就是以后经常用的链接，在建好的文件夹里面右键Git bash 就出现命令行：我们输入：
    
```linux
    git clone 刚才复制的链接.git
    
    git clone https://github.com/pkwenda/weibaopro.git
```
然后我们看到项目已经下载好了在刚才新建的文件夹会找到weibao这个文件夹
    
###上传文件到github的方法
---
####第一步：创建Github新账户
    
---
####第二步：新建仓库
    
---
    newgithub
    
####第三部：填写名称
简介（可选），勾选Initialize this repository with a README选项，这是自动创建REAMDE.md文件，省的你再创建。

---
####第四步：打开Git

Shell，输入以下命令生成密钥来验证身份
```linux   
    ssh-keygen -C 'your@email.address' -t rsa
```
连续三个回车之后会在windows当前用户目录下生成.ssh文件夹，和linux一样。
    把文件夹下的id_rsa.pub文件内容全部复制。(文件夹的位置按回车之后会告诉你)
    然后打开github账户设置，如图：
    
![](leanote://file/getImage?fileId=567b78baab64416467006071)

进入之后点击左侧的SSH KEYS，然后在title随便输入，key栏粘贴刚才的密钥。（注意：填写RSA_pub的，他是公共秘钥）
    
---
####第五步：测试公钥
在Git Shell下输入命令测试刚才的公钥是否认证正确。
```linux
    ssh -T git@github.com
```    
正确结果会显示：
```linux    
    Warning:Permanently added 'github.com,207.97.227.239' (RSA) to the list of known hosts.
    　　Hi Flowerowl! You've successfully authenticated, but GitHub does not provide shell access.
    warning 
```
不用理会。
 ---   
####第六步：clone respository
clone刚才新建的repository 到本地，输入命令：
```linux    
    git clone https://github.com/Flowerowl/stumansys.git
```    
   这时会在目录下生成：.git文件，.gitignore,.README.md
 ---
####第七步：将想上传的代码目录拷贝到此文件夹下：
即，刚才的本地库（你在打开GIt bash的时候默认在哪里打开就在哪里建立，也可以用dos命令 cd    cd..进入文件夹）
    
---
####   第八步：切换到Git bash 命令行下，输入命令：
    
    git init
    git commit -m 'stumansys'
    git remote add origin https://github.com/Flowerowl/stumansys.git
    git push origin master
*如果执行git remote add origin
    
    https://github.com/Flowerowl/stumansys.git
*出现错误：
    
    　　fatal: remote origin already exists
则执行以下语句：
    
    　　git remote rm origin
再往后执行
```linux
git remote add origin https://github.com/Flowerowl/stumansys.git 
```
即可。
    
*在执行git push origin master时，报错：
    
    　　error:failed to push som refs to.......
则执行以下语句：
    
    git pull origin master
先把远程服务器github上面的文件拉先来，再push 上去。
    
    cmd
    
最后，你可以去项目页面查看了~~代码上传成功！
##Myeclipse GIt插件安装和使用
###安装egit插件
解压压缩文件，把文件内的xml文件删除，在Myeclipse\dropins文件夹下新建egit文件夹：把features、plugins两个文件夹和artifacts.jar、content.jar两个jar包扔到里面去，重启Myeclipse。下面简单安装之后就可以在windows ——》 preference ——》搜索到git了，另外Myeclipse2015自带git插件无需下载！
###配置git
1、Preference-->General-->Network Connections
将Active Provider:改成Direct  Apply
2、Preference-->General-->Network Connections->SSH2
选择SSH2 home （就是安装Git的时候我们按回车生成的.ssh文件夹内的秘钥）我们Browse 选择刚才那个.ssh文件夹
Private keys:选择 id_rsa文件即可
3、点击Genneral右侧的Key Mannagement,选择Load Existing Key选择 id_rsa文件。   --》Apply
###使用Git插件
####建立本地库
随便点击个项目，为了方便管理尽量和github资源库名字一样
右键->team->share project点击
选择Git
点击create：在本地建立一个本地资源库
选择路径，填写项目名，勾选下面的项目，Finnish
再次右键项目->team我们发现和上次不一样了，好，先commit一下，去本地资源库发现提交成功。

---
####得到github ssh地址
但是我们最终是要向github传的，所以回到github，进入你的主页，刚才刚创建的资源库，上次我们说的获取https地址那步，我们点小三角，选择ssh地址，copy

---

####push项目到github
右键项目--team--remote---push
url正确的格式是：
ssh://git@github.com/应户名/资源库名.git
ssh://git@github.com/pkwenda/weibaopro.git
下面的两个自动生成，
！！注意github.com后面是'/'不是':'
自己进行修改即可
user用默认的git就可以，因为ssh2已经填写了公钥
NEXT

---
点击Source ref选择【marster brunsh】
Destination ref自动生成【marster brunsh】

点击Add All Branches spec...
点击Add All Tags Spec..
下面会出两个框，全部选上
Finish
然后会告诉你成功，并提示你刚才commit时候写的注释。
OK
 

