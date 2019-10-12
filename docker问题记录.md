同时安装kvm和docker时，如果在防火墙启动的同时打开docker服务，会导致kvm上不去网，只有关闭防火墙才会恢复正常
修复：iptables -I FORWARD -i br0 -o br0 -j ACCEPT

docker指定容器和宿主机在同一个网段
docker network create -d macvlan --subnet=192.168.1.0/24 --gateway=192.168.1.1 -o parent=br0 lan
docker run -itd --name=busybox --net=lan busybox
docker exec -it busybox /bin/sh
参考：https://my.oschina.net/jastme/blog/1499403
https://godleon.github.io/blog/Docker/docker-network-macvlan/
https://www.hi-linux.com/posts/40904.html

