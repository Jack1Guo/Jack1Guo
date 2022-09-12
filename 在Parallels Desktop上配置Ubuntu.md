# Install and configure Ubuntu 20.04  distribution in Parallel Desktop.    [^Model]

[^Model]: The model of my laptop is MacBook,which system is macOS.And it restricts the environment to install the version of Ubuntu. ↩

## Download Ubuntu on Parallels Desktop

* Download dmg file on https://parallels.cn/products/desktop/download/
* Register 

* Install Ubuntu Linux![1](https://tva1.sinaimg.cn/large/e6c9d24egy1h63n6iqg1gj21dt0u0juz.jpg)A long wait

* Finally,we enter the system successfully!![截屏2022-09-11 11.59.32](https://tva1.sinaimg.cn/large/e6c9d24egy1h63n786f76j21c00u0q5b.jpg)

## Configure secret free remote server login based on SSH key

* Use command `ssh-keygen` at the terminal.Then keep pressing enter,you can get the pubilc and private key files.![截屏2022-09-11 12.08.24](https://tva1.sinaimg.cn/large/e6c9d24egy1h63n78thgtj212j0u078e.jpg)
* Add public key in authorized_keys.In fact the file authorized_keys is not exist.We need to create it.Then change its permissions, or we couldn't edit it.![截屏2022-09-11 14.42.26](https://tva1.sinaimg.cn/large/e6c9d24egy1h63n7g2a64j215w050q3r.jpg)
* Do the same step on my MacBook.![截屏2022-09-11 14.50.52](https://tva1.sinaimg.cn/large/e6c9d24egy1h63n7ru2ilj20t603wdgg.jpg)
* Add the id_rsa.pub to authorized_keys.Copy the MacBook's to Ubuntu.![截屏2022-09-11 14.54.08](https://tva1.sinaimg.cn/large/e6c9d24egy1h63n8dxv7xj21060u0ai2.jpg)

* Use command ifconfig look up the Ubuntu's ip.

* Link it by command ssh parallels@192.168.1.111

  But!!! There is something error!!![截屏2022-09-11 14.59.54](https://tva1.sinaimg.cn/large/e6c9d24egy1h63n8s9qaxj20qa01wt90.jpg)

And I look it up at CSDN.It gives me two ways.

(1)Increase the number of SSH terminal connections.But it doesn't work!

(2)Change the users‘ ip. Successfully!But it needs password.

### ![截屏2022-09-11 15.16.03](https://tva1.sinaimg.cn/large/e6c9d24egy1h63n90t95yj20zc0jsjvl.jpg)Principle of secret free login based on SSH key

![IMG_1261](https://tva1.sinaimg.cn/large/e6c9d24ely1h63mflffk0j21400u0tm7.jpg)
