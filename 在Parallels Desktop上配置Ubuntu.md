# Install and configure Ubuntu 20.04  distribution in Parallel Desktop.    [^Model]

[^Model]: The model of my laptop is MacBook,which system is macOS.And it restricts the environment to install the version of Ubuntu. ↩

## Download Ubuntu on Parallels Desktop

* Download dmg file on https://parallels.cn/products/desktop/download/
* Register 

* Install Ubuntu Linux

<img src="/Users/guorunhang/Desktop/1.png"  />

* A long wait

* Finally,we enter the system successfully!

![](/Users/guorunhang/Desktop/截屏2022-09-11 11.59.32.png)

## Configure secret free remote server login based on SSH key

* Use command `ssh-keygen` at the terminal.Then keep pressing enter,you can get the pubilc and private key files.
* ![](/Users/guorunhang/Desktop/截屏2022-09-11 12.08.24.png)

* Add public key in authorized_keys.In fact the file authorized_keys is not exist.We need to create it.Then change its permissions, or we couldn't edit it.![](/Users/guorunhang/Desktop/截屏2022-09-11 14.42.26.png)

* Do the same step on my MacBook.![](/Users/guorunhang/Desktop/截屏2022-09-11 14.50.52.png)
* Add the id_rsa.pub to authorized_keys.Copy the MacBook's to Ubuntu.![](/Users/guorunhang/Desktop/截屏2022-09-11 14.46.45.png)

![](/Users/guorunhang/Desktop/截屏2022-09-11 14.54.08.png)

* Use command ifconfig look up the Ubuntu's ip.

* Link it by command ssh parallels@192.168.1.111

  But!!! There is something error!![](/Users/guorunhang/Desktop/截屏2022-09-11 14.59.54.png)

And I look it up at CSDN.It gives me two ways.

(1)Increase the number of SSH terminal connections.But it doesn't work!

(2)Change the users‘ ip. Successfully!But it needs password.![](/Users/guorunhang/Desktop/截屏2022-09-11 15.16.03.png)

### Principle of secret free login based on SSH key

![IMG_1261](https://tva1.sinaimg.cn/large/e6c9d24ely1h63mflffk0j21400u0tm7.jpg)
