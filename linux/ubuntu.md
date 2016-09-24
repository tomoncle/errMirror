###dpkg 被中断，您必须手工运行 dpkg --configure -a 解决此问题。
解决:  rm /var/lib/dpkg/updates/* && apt-get update &&  apt-get upgrade
