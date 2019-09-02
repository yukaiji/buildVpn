# 近期很多ip和端口被墙，请大家多多尝试，不要删除之后立刻新建服务器，容易导致分配删掉的ip
### Vultr页面UI变了，但是丝毫不影响流程，这里就先不更新图片了，一样的不影响

# buildVpn 如果有什么问题，可以给我发邮件 yukaiji@hotmail.com
## 本文仅供学习参考
### 图文教程搭建一个vpn访问墙外的世界

### 准备工作：有支付宝账户，有一个可用邮箱，有10美元。

### 前言：首先我们选择Vultr供应商来购买海外VPS服务器，具有12个地区可以选择，当然也可以选择其他的供应商，但是Vultr的优点在于，所有服务器创建成功后开始计费，并且是按照小时来计费的，如果你删除掉服务器将不再计费。众所周知，目前国内的VPN打击特别严厉，很多VPN已经被封掉了，我们购买的海外服务器也有可能是被墙掉IP或者用一段时间被墙的。所以Vultr可以随时创建一个新的服务器（会分配一个新的ip），删除掉原有的。

### 创建账户及购买VPS服务器

第一步：登录vultr官网注册一个账户，只需要一个邮箱和密码即可。然后到你注册的邮箱中去验证你的账户。
官网链接(https://www.vultr.com/?ref=7348872)        这个链接就是普通的推荐链接
官网推广链接(https://www.vultr.com/?ref=7800747-4F) 这个链接是官网一个推荐链接，有50刀体验金
![第一步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101419422.jpg)

第二步：登录你的账户，然后在如图所示地方进行充值。这里我们用支付宝扫码支付比较方便，充值成功后，可以再右上角看到你的账户余额。

![第二步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101506198.jpg)

第三步：购买VPS服务器。在Servers标签中看到，我们目前还没有服务器，这时选择右上角的加号新添加一个服务器。

![第三步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101543991.jpg)

我们首先选择服务器所在地区，这里我们选择NewYork纽约，一般来说选择日本、纽约、洛杉矶、硅谷都还可以（全看人品）。

![第四步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101558312.jpg)

其次我们选择服务器的系统版本。这里注意选择CentOS6 ，默认是7由于防火墙等原因可能会影响接下来的操作。

![第五步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101612917.jpg)

最后，我们选择每个月2.5刀，500G带宽的就可以了。

![第六步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101629749.jpg)

其他的不需要选择，如果需要使用IPv6就在第四部选择。这里我们不选择，默认使用IPv4，最下面我们选择Depliy Now 新建服务器。

![第七步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101643841.jpg)

到目前为止我们就已经成功的创建了一个海外服务器。但是这个服务器是否可用，有没有被墙掉呢？当服务器安装完成之后，我们来测试一下。

![第八步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101656506.jpg)

我们可以看到已经在运行的服务器ip为  45.63.7.251 ，接下来就测试一下是否能够连接。
Win： win + R快捷键或者在开始菜单-附件-运行，调出运行窗口，输入cmd，然后输入ping  45.63.7.251 可以看到是否被墙。（多ping几次）
Mac + Linux：直接在命令行窗口输入ping  45.63.7.251 （按ctrl + c 退出）
或者通过网站ping检测，如果全是超时代表被墙了。http://ping.chinaz.com/

![第九步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101706991.jpg)

这里可以看到刚刚新建的服务器是被墙掉的。无法访问，这时就再新建一个服务器，然后在ping。如果同一个地区多次无法ping通，就换一个地区试试，这里推荐日本。（每次新建服务器，按小时首付0.01刀，删除后不计费，十次也才不到一块钱）

如图，我再次新建了一个服务器，这回可以ping通，说明没有被墙。就是延时高一点，延时与你的网络和当前的时间段，使用的人数有关。

![第九步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101717865.jpg)

![第十步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101733164.jpg)

这时我们把之前被墙掉的服务器删除就可以了。新建可用的服务器已经全部完成了。

![第十一步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101748789.jpg)

点击详情可以看到服务器的用户名和密码

![第十二步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101802763.jpg)

![第十三步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101812373.jpg)

接下来我们就可以搭建VPN了。距离成功已经很近了。

首先如果我们是Windows系统需要下载一个软件（Mac 或 Linux不需要），Xshell或者SecureCRT。这里我用的是SecureCRT。
填写你的IP地址，用户名为root，点击链接，点击接受保存，输入你的密码，成功连接。

![第十四步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101823784.jpg)
![第十五步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101836775.jpg)

其次要设置编码格式，不然一会的中文会显示乱码。菜单栏 选项-会话选项-外观-字符编码-UTF8-确认。
关闭软件，重新连接（直接双击IP就可以了）。

![第十六步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101848327.jpg)

然后复制下面的一键部署管理脚本，粘贴到窗口中（鼠标右键一下即可粘贴）

CentOS6/Debian6/Ubuntu14 ShadowsocksR一键部署管理脚本(可以把下面命令按行拆开分步执行)：

wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh

chmod +x shadowsocksR.sh

./shadowsocksR.sh 2>&1 | tee shadowsocksR.log

### 主脚本安装SSR：
第一步：设定密码，default 为默认密码

![第十六-1步](https://github.com/yukaiji/buildVpn/blob/master/image/new2.png)

第二步：设定端口，default 为随机生成默认端口
![第十六-2步](https://github.com/yukaiji/buildVpn/blob/master/image/new3.png)

第三步：设定加密方式，default 为默认加密方式
![第十六-3步](https://github.com/yukaiji/buildVpn/blob/master/image/new4.png)

第四步：设协议，default 为默认协议
![第十六-4步](https://github.com/yukaiji/buildVpn/blob/master/image/new1.png)

第五步：设定混淆方式，default 为默认混淆
![第十六-5步](https://github.com/yukaiji/buildVpn/blob/master/image/new5.png)

第六步：安任意键，回车开始进行安装，安装完成后自动启动
![第十六-6步](https://github.com/yukaiji/buildVpn/blob/master/image/new7.png)

最终：安装完成，展示你所设置的内容，可以按照链接信息进行连接(最近较严有可能被墙或者端口被封)
![第十六-7步](https://github.com/yukaiji/buildVpn/blob/master/image/new6.png)

安装过后如果想要修改，运行如下相关命令

启动：/etc/init.d/shadowsocks start

停止：/etc/init.d/shadowsocks stop

重启：/etc/init.d/shadowsocks restart

状态：/etc/init.d/shadowsocks status

配置文件路径：/etc/shadowsocks.json  修改文件用vi 或者 vim命令，使用方法百度

日志文件路径：/var/log/shadowsocks.log 

安装路径：/usr/local/shadowsocks/shadowsoks

卸载./shadowsocksR.sh uninstall

备用脚本（上面的脚步不可用再输入这个）：

wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh

如果在输入命令式提示wget:command not found，则表示没有wget工具，先输入下面指令进行安装，然后再部署管理脚本
yum -y install wget

### 备用脚本安装SSR：（如果此时链接断了，重连后输入./ssr.sh 就可以进入下面安装操作，以后修改时也输入./ssr.sh）
第一步：选择1 

![第十七步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101902154.jpg)

第二步：直接默认即可。（理论上说是可以随便的，1 - 65535）

![第十八步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101913385.jpg)

第三步：设置密码

![第十九步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101927773.jpg)

第四步：加密方式，选择aes-128-cfb就可以

![第二十步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101937845.jpg)

第五步：协议插件，为了使SS也能够使用，这里选择origin

![第二十一步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101948387.jpg)

第六步：选择混淆plain

![第二十二步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307101957836.jpg)

第七步：设置连接数量，默认回车即可。然后开始进行安装。

![第二十三步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102008416.jpg)

如果遇到输入项，问y还是n时，输入y 回车确认。

![第二十四步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102018140.jpg)

### 到此安装就完成了。可以通过客户端进行链接翻墙上网了。

![第二十五步](https://github.com/yukaiji/buildVpn/blob/master/image/2018030710205260.jpg)



### 为了能够提高上网速度，YouTube从480 体验为1080。我们接下来进行安装加速软件（速锐、BBR两者选其一，不可共存）。

### BBR加速（如果需要速锐，跳过此段）

BBR加速特别简单，复制下面脚本代码即可。
谷歌BBR加速脚本：

第一个指令：wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh

第二个指令：chmod +x bbr.sh

第三个指令：./bbr.sh

1、遇到停顿按回车即可。然后继续安装。（多等一会）

![第二十六步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102104748.jpg)

2、安装完成后问你是否重启，这里输入y，回车。

![第二十七步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102114503.jpg)

3、重新连接后，输入 lsmod | grep bbr 查看BBR是否启动，可以看到已经启动了。

![第二十八步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102126665.jpg)




### 速锐加速
1、首先输入
uname -a 查看内核为

2、然后输入
cat /etc/redhat-release  查看系统版本

3、下载CentOS 6.6版本的内核（速锐支持6.6版本的）
wget http://ftp.scientificlinux.org/linux/scientific/6.6/x86_64/updates/security/kernel-2.6.32-504.3.3.el6.x86_64.rpm

4、安装内核
rpm -ivh kernel-2.6.32-504.3.3.el6.x86_64.rpm --force

5、重启服务器
reboot

6、安装速锐
wget -N --no-check-certificate https://raw.githubusercontent.com/91yun/serverspeeder/master/serverspeeder-all.sh && bash serverspeeder-all.sh

这时正常情况速锐就已经安装完成并且启动了。

![第二十九步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102140531.jpg)

service serverSpeeder status     查看速锐的状态
service serverSpeeder start | stop | restart  停止暂停重启锐速


### 到此为止，通过BBR或速锐加速的VPN服务器已经全部搭建完成了。

### 接下来使用SSR或者SS客户端连接即可

MAC：https://github.com/shadowsocksr-backup/ShadowsocksX-NG/releases
WIN：https://github.com/shadowsocksr-backup/shadowsocksr-csharp/releases
IPHONE：FirstWingy、potatso lite  （商店里有，实在找不到可以弄个美国APPLEID，什么都能下）

以iphone为例：首先右上角加号，添加服务器配置信息。

![第三十步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102153178.jpg)

然后：填写一开始安装时的信息,保存。如果忘了记得 ./ssr.sh  选择5 查看连接信息

![第三十一步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102204995.jpg)

这时你可以愉快的翻墙上网了。

![第三十二步](https://github.com/yukaiji/buildVpn/blob/master/image/20180307102258394.jpg)
