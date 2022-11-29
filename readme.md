第一步、远程登录Hostwinds VPS
购买好Hostwinds的VPS之后，系统会给我们发送一封邮件，邮件里面我们需要用到VPS的ip地址、端口号、还有管理员的账号和密码。![请添加图片描述](https://img-blog.csdnimg.cn/ae445f22074446b5b76105b6eb2db2c4.png)
然后下载LInux远程登录工具：Xshell，下载地址：http://yun.pinzixing.com/f/29610147-531662372-1ef1e8
2.登录到vps
![请添加图片描述](https://img-blog.csdnimg.cn/34a83f2c5f804c0ea3c1e2ba11799f1b.jpeg)
3. 在Linux系统下安装V2Ray
登录 Linux VPS 以后将下面的V2ray 一键安装脚本代码复制，在登录窗口鼠标右键>粘贴：
注意:ctrl+v 粘贴命令在xshell里面是没用的
> #bash <(curl -s -L https://git.io/v2ray.sh)

![请添加图片描述](https://img-blog.csdnimg.cn/1d41c105311d49c1b326689609ba7e17.png)
如果提示curl：command not found，那是因为你的VPS没装Curl
centos 安装Curl方法，在Linux命令行下执行一下命令:
> yum update -y && yum install curl -y

ubuntu/debian 系统安装Curl 方法，在Linux命令下执行以下命令：
> apt-get update -y && apt-get install curl -y

安装好curl 之后就能安装前面的V2ray 一键安装脚本了

命令执行没问题会出现下面的提示，我们输入1 按回车键
![请添加图片描述](https://img-blog.csdnimg.cn/d64c7066feb745b497e11d319a2147d6.png)
![请添加图片描述](https://img-blog.csdnimg.cn/f61bab21551b4b559990a5434f9982e1.png)
选择V2ray的传输协议，也是按照默认TCP即可，按键盘上的回车继续
下面会继续让我们选择V2ray的端口、是否开启广告拦截、是否配置shadowsocks,我们一律按默认的配置，全部按回车键确认。
![请添加图片描述](https://img-blog.csdnimg.cn/94fce938b9734a4e9c63fd107277ea58.png)
接着系统会提示我们再次确认我们刚才的配置信息，确认配置信息没问题我们直接Enter回车键。
![请添加图片描述](https://img-blog.csdnimg.cn/10ebfbf3d7b143ac8f1c7d94d547f167.png)
然后屏幕上会自动弹出一堆安装信息，系统会自动进行安装V2ray,最后如果出现以下界面，说明安装成功。
![请添加图片描述](https://img-blog.csdnimg.cn/ad0faf7a0ec541d0b26deca7604a7448.png)
我们需要记住上面的信息，一会配置本地V2rayN客户端要用。
# 优化V2Ray
前面的步骤全部弄完我们还需要优化V2Ray，我这里安装的是hostwinds的Centos 7，系统内核支持开启BBR，所以我执行v2ray bbr这个命令系统会有以下提示，如果你是使用其他商家的 VPS 并且是按照此教程流程来安装 V2Ray 的话，就正常执行v2ray bbr命令，按提示操作即可。![请添加图片描述](https://img-blog.csdnimg.cn/02ad072ae7ea483a96b93c7570ae70f2.png)
只是还想再啰嗦一下，如果你是使用国际大厂的 VPS，并且是按照此教程流程来安装 V2Ray 的话，请自行在安全组 (防火墙) 开放端口和 UDP 协议 (如果你要使用含有 mKCP 的传输协议)
# 在本地计算机安装V2ray客户端
上面的所有步骤弄完，然后在本地计算机上面安装一下V2ray客户端就可以科学上网了，手机端上网的话也需要先配置好电脑端。
 V2Ray Windows 客户端主要有两个，一个是 v2ray-core（v2ray 核心，官方客户端），另一个是 v2rayN（基于 v2ray-core 的开一个 GUI 可视化客户端），其中前者 v2ray-core 可以单独使用，而 v2rayN 则是基于 v2ray-core 的一个辅助可视化工具
之前v2ray客户端需要下载两个文件，然后合并方可运行，现在只需要下载一个文件即可。
#### 1、下载v2rayN客户端
V2Ray Win客户端名称为v2rayN，手机客户端名称为v2rayNG
github下载：https://github.com/2dust/v2rayN/releases（找到v2rayN-Core.zip下载）
[csdn资源下载处【url】](https://download.csdn.net/download/weixin_42892543/86946860)
#### 2、配置v2rayN客户端（电脑）
将下载的文件解压到当前文件夹，点击v2rayN-Core文件夹下面的v2rayN.exe启动。
接着在任务栏托盘找到 V2RayN 图标并双击它可以打开V2rayN客户端。


打开客户端 左上角 选择“服务器”》“添加VMess服务器”，添加好前面获取的服务器ip、端口、用户id、额外id和加密方式，加密方式选择auto，其他信息对应前面获取的信息进行填写。
![请添加图片描述](https://img-blog.csdnimg.cn/eda1510383204da9a4e88b2518209ae1.png)
点击确定，v2ray主界面的服务器列表会便有了我们刚才添加的记录，状态栏会显示V2Ray 4.42.2 started。我这里用的最新版本的V2ray，2022年1月12日的 4.42.2版本
![请添加图片描述](https://img-blog.csdnimg.cn/0d34629ba3ba4a708b15efac4233e83d.png)
#### 3.开启V2rayN全局代理启动科学上网
注意：这里和老版本的V2rayN不一样，老版本是选择 “Http代理”》“开启Http代理，并自动配置系统代理（全局模式）”
新版软件菜单中多出了一个“路由”的选项，默认是选择的“绕过大陆”，按照默认即可。![请添加图片描述](https://img-blog.csdnimg.cn/6e706185b8194d93838047cccd90894d.png)
然后在任务栏托盘找到 V2RayN 图标并鼠标右键，选择“系统代理”》“自动配置系统代理”（如下图），设置完了以后，任务栏托盘的V2rayN图标会变红，这样设置完毕以后，我们即可科学上网。![请添加图片描述](https://img-blog.csdnimg.cn/909b80baffac4751ab61fbe9c69f65c9.png)
 **郑重提醒：科学上网仅供学习之用，不要从事任何非法活动。**
