# [Tutorial] Set SSH SERVER

- **Metadata** : `type: Tutorial` `scope: Linux` 
- **Techs Need** : `Linux` 
- **Status** : `ongoing`

## â¨ You should already know

> Operation in  Linux

ð©âð» ð¨âð»

## â¨ About the wiki

- `Situation:`  We need to connect to Linux server by command
- `Target:`  build SSH Server ON Linux Server
- `Index:`

| Sub title | decription | memo |
| ------ | ------ | ------ |
| setup script| - | - |


## â¨  Sections


### **setup script**
> run this script

<br/>

#### ð Install SSH
```
è¦å®è£ ssh server, ä»¥ä¸å©è¡æä»¤é½å¯ä»¥
# apt-get install ssh
# apt-get install openssh-server
```


#### ð Update SSH Config
```
å®è£å¾å¯ä»¥ä¿®æ¹ä¸äº ssh çè¨­å®, å¦port, å¯ç¢¼èªè­, rootç»å¥ç­
# vim /etc/ssh/sshd_config
Port 22
PasswordAuthentication yes
PermitRootLogin yes 

æ´æ¹å®å­æªå¾è¨å¾éåæå
# /etc/init.d/ssh restart
```


