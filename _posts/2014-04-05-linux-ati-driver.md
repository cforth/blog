---
layout: default
title: Ubuntu12.04升级后ATI显卡驱动问题
---
{{ page.title }}
----------------

之前我的台式机上的Ubuntu12.04在升级软件包后，ATI的显卡驱动莫名其妙的损坏了。导致桌面上的一些效果都无法使用。

在网上搜到了重装ATI显卡驱动的方法：

1. 下载显卡驱动，去ATI的官网上下载对应的驱动。

2. 生成deb包（sudo sh ./amd-driver-installer-12-6-x86.x86_64.run --buildpkg Ubuntu/precise）。

3. 安装驱动（sudo dpkg -i fglrx*.deb）。

4. 生成配置文件（sudo aticonfig --initial -f）。

5. 重启电脑后查看显卡驱动是否安装成功（fglrxinfo）。

用以上的方法就可以成功的重新安装显卡驱动。

{{ page.date | date: "%Y-%m-%d" }}
