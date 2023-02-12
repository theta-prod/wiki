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

#### 📝 New SSH Key
1. 用 ssh-keygen 產生公私鑰
2. 把公鑰內容貼到 server 上對應帳號的 ~/.ssh/authorized_keys 這個檔案裡面（可以用 scp）


#### 📝 Update SSH Config

1. 
```
# vim /etc/ssh/sshd_config
PubkeyAuthentication yes
AuthorizedKeysFile .ssh/authorized_keys
PermitRootLogin no
PermitEmptyPasswords no
PasswordAuthentication no
```
2. 

```
chmod 600 ~/.ssh/authorized_keys
chmod 700 ~/.ssh
```

3.
```
sudo systemctl restart sshd
```



