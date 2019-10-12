文件权限

    600 authorized_keys
    700 ~/.ssh

打开密钥登录功能

    RSAAuthentication yes
    PubkeyAuthentication yes

root 用户能通过 SSH 登录

    PermitRootLogin yes

禁用密码登录

    PasswordAuthentication no

端口转发

    将发往本机的80端口访问转发到174.139.9.66的8080端口
    ssh -C -f -N -g -L 80:174.139.9.66:8080 master@174.139.9.66

    发往174.139.9.66的8080访问转发到本机的80端口
    ssh -C -f -N -g -R 80:174.139.9.66:8080 master@174.139.9.66

SSH远程连接时间设置

    ClientAliveInterval       ：   多久向客户端发送请求，300表示300秒即5分钟；
    ClientAliveCountMax  ：    超过多少次请求没被客户端响应，结束连接；
    因此设置ClientAliveInterval       300，ClientAliveCountMax  10   表示每隔300秒请求一次，超过10次客户端无响应，即50分钟后断开连接。

用SSH登录远程的机器，在远程机器上执行本地机器上的脚本

    ssh root@10.245.111.93 \'bash -s\' < /root/testlocal.sh
https://www.cnblogs.com/awpatp/p/9935820.html