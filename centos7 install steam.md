sudo yum install http://download1.rpmfusion.org/free/fedora/releases/19/Everything/i386/os/libtxc_dxtn-1.0.0-3.fc19.i686.rpm

sudo yum -y localinstall --nogpgcheck https://download1.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm https://download1.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-7.noarch.rpm

sudo yum-config-manager --add-repo=https://negativo17.org/repos/epel-steam.repo

sudo yum -y install steam