# [Tutorial] Set SSH SERVER

- **Metadata** : `type: Tutorial` `scope: Linux` 
- **Techs Need** : `Linux` 
- **Status** : `ongoing`

## ✨ You should already know

> Operation in  Linux

👩‍💻 👨‍💻

## ✨ About the wiki

- `Situation:`  We need to connect to Linux server by command
- `Target:`  build SSH Server ON Linux Server
- `Index:`

| Sub title | decription | memo |
| ------ | ------ | ------ |
| setup script| - | - |


## ✨  Sections


### **setup script**
> run this script

<br/>

#### 📝 Install SSH
```
要安裝 ssh server, 以下兩行指令都可以
# apt-get install ssh
# apt-get install openssh-server
```


#### 📝 Update SSH Config
```
安裝後可以修改一些 ssh 的設定, 如port, 密碼認證, root登入等
# vim /etc/ssh/sshd_config
Port 22
PasswordAuthentication yes
PermitRootLogin yes 

更改完存檔後記得重啟服務
# /etc/init.d/ssh restart
```


