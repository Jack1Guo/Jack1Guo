# Install and configure Ubuntu distribution of WSL2.AndConnect to wsl2 through vscode's remote plug-in[^notice]



[^notice]: Because of a message in QQ Group that WSL is preferred,I bring my old laptop with Windows10.And install Ubuntu on it.

## Enable WSL and install Ubuntu

* Open the windows subsystem for Linux![截屏2022-09-12 09.45.06](https://tva1.sinaimg.cn/large/e6c9d24ely1h63ldtmo8cj21ra0u0q8k.jpg)

* Download the Linux kernel update package on [Download URL](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)
* Install Ubuntu in the windows app store![截屏2022-09-12 09.50.56](https://tva1.sinaimg.cn/large/e6c9d24ely1h63ldme3m2j214b0u041g.jpg)

* Enable the virtual machine function before installing WSL 2
* Set WSL 2 as the default version ![IMG_1250 2](/Users/guorunhang/Desktop/%E6%9C%AA%E5%91%BD%E5%90%8D%E6%96%87%E4%BB%B6%E5%A4%B9%202/IMG_1250%202.png)![]()

* Install Ubuntu 20.04 in the windows software store
* Open Ubuntu and enter username and password
* Since the default software source of Ubuntu is foreign, sometimes the download software may be blocked in the future, and it needs to be replaced with the domestic alicloud source![](https://tva1.sinaimg.cn/large/e6c9d24ely1h63m1sasj1j21rm0kudlr.jpg)
* Update and upgrade software

![](/Users/guorunhang/Desktop/%E6%9C%AA%E5%91%BD%E5%90%8D%E6%96%87%E4%BB%B6%E5%A4%B9%202/IMG_1243.png)

* Install desktop environment
* Install systemctl
* Install remote control software xrdp![](https://tva1.sinaimg.cn/large/e6c9d24ely1h63m57e54ej21400u0dqh.jpg)

![IMG_1251](https://tva1.sinaimg.cn/large/e6c9d24ely1h63m5h1vzvj21400u0gw0.jpg)

* Change port from 3389 to 3390 (Because port 3389 has been occupied)

In fact, run this command.Ternmail will give warning.

* Configure to start the session, otherwise the remote desktop login will flash back after entering the password

![截屏2022-09-12 10.32.53](https://tva1.sinaimg.cn/large/e6c9d24ely1h63m9gdyy8j21rm0kudpv.jpg)

* Run mstsc and enter localhost:3390
* Get in Ubuntu Successfully!![IMG_1256](https://tva1.sinaimg.cn/large/e6c9d24ely1h63mbry9zmj21400u078q.jpg)
* Finally, change system language to Chinese.![](https://tva1.sinaimg.cn/large/e6c9d24ely1h63mbwwmg2j21400u0jwi.jpg)

## Connect to wsl2 through vscode's remote plug-in

* Install Remote-WSL,Remote-SSH,Remote-Containers
* Use Ctrl+Shift+P to configure host config
* Enter command “>Remote-WSL: New Window using Distro”
* Successfully connect！![](https://tva1.sinaimg.cn/large/e6c9d24egy1h63mweps94j21400u0grg.jpg)