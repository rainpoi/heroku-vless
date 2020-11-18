# VLESS Heroku

## 概述

用于在 Heroku 上部署 vless+websocket+tls  vless 性能更加优秀，占用资源更少。

## 镜像

经测试本镜像不会因为大量占用资源而被封号。

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/cyao2q/heroku-vless/tree/main)

## 注意

Address: yourAppName.herokuapp.com   
Port: 443   
id: Your entered id   
Flow: xtls-rprx-direct   
encryption: none   
Transport: ws   
TLS: tls      

## 流量中转

可以使用cloudflare的workers来`中转流量`，配置为：  

addEventListener(  
    "fetch",event => {  
        let url=new URL(event.request.url);  
        url.hostname="xx.xxxx.xx";//你的heroku域名    
        let request=new Request(url,event.request);  
        event. respondWith(  
            fetch(request)  
        )  
    }  
)
