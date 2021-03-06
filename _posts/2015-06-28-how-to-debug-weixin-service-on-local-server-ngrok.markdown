---
layout: post
title:  "利用内网穿透实现微信开发的本地化调试-ngrok篇"
date:   2015-06-28 17:51:27
categories: jekyll update
---
# ngrok介绍
* ngrok官网：[https://ngrok.com/][ngrok]
* ngrok是一个内网穿透工具，通过它可以实现“安全地在公网访问你的本地网络服务”，例如实现本地环境中运行的我们自己微信服务器与公网上的腾讯微信服务器交互。

# tunnel介绍
* 官网：http://www.tunnel.mobi/
* tunnel相当于ngrok的墙内版，ngrok虽然已经实现了内网穿透功能，但很不幸，由于墙的存在，在天朝几乎不能使用。tunnel让墙内的人也可以享受ngrok的功能。
* tunnel需要搭配ngrok的程序，启动时加载tunnel的配置文件。
* 注意事项：ngrok最新版已经不支持加载配置文件了，不过用以前的版本还是可以的，这里用的是ngrok 1.7版（见附件）。

# 操作步骤
* 下载文件：我已经将ngrok1.7和tunnel配置文件打包好。
* 解压ngrok压缩包，进入ngrok.exe所在的文件夹，SHIFT+右键——在此处打开命令提示符。
* 运行启动命令。
运行客户端时，请添加-config以载入配置文件。
例如
`ngrok -config ngrok.cfg -subdomain example 8080`
意为将本地的8080端口链接到example.tunnel.mobi上
我的命令是：
`ngrok -config ngrok.cfg -subdomain weixinqiqi 80`
* 成功提示如下
{% highlight sh %}
ngrok
Tunnel Status                 online
Version                       1.7/1.7
Forwarding                    http://weixinqiqi.tunnel.mobi -> 127.0.0.1:80
Forwarding                    https://weixinqiqi.tunnel.mobi -> 127.0.0.1:80
Web Interface                 127.0.0.1:4040
# Conn                        16
Avg Conn Time                 38017.47ms
{% endhighlight %}    
    
* 外网访问[http://weixinqiqi.tunnel.mobi][weixinqiqi]上的应用，检查是否可以访问

# 注意事项：
* 此方法是否可用，取决于tunnel服务器状态，至少我在使用的期间（2015年1月~2015年6月）基本满足使用需求。
* tunnel的服务器可能会偶尔出现不稳定、超时的现象。

# 附件：
[ngrok+tunnel套件][ngrok1.7download]


[ngrok]:       https://ngrok.com/
[weixinqiqi]:  http://weixinqiqi.tunnel.mobi
[ngrok1.7download]:      http://pan.baidu.com/s/1i3q0QhR
