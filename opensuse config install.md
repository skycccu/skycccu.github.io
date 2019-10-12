更新源：

    sudo zypper ar -fc https://mirrors.aliyun.com/opensuse/distribution/leap/15.0/repo/oss openSUSE-Aliyun-OSS
    sudo zypper ar -fc https://mirrors.aliyun.com/opensuse/distribution/leap/15.0/repo/non-oss openSUSE-Aliyun-NON-OSS
    sudo zypper ar -fc https://mirrors.aliyun.com/opensuse/update/leap/15.0/oss openSUSE-Aliyun-UPDATE-OSS
    sudo zypper ar -fc https://mirrors.aliyun.com/opensuse/update/leap/15.0/non-oss openSUSE-Aliyun-UPDATE-NON-OSS
   sudo zypper ar -fc https://mirrors.aliyun.com/packman/openSUSE_Leap_15.0 openSUSE-Aliyun-Packman
   sudo zypper ar -fc https://download.opensuse.org/repositories/home:/opensuse_zh/openSUSE_Leap_15.0 openSUSE-zh
   sudo zypper ar -fc https://download.opensuse.org/repositories/M17N/openSUSE_Leap_15.0 M17N
   sudo zypper ar -fc https://download.videolan.org/pub/SuSE/Leap_15.0 VLC
   sudo zypper addrepo -f https://download.nvidia.com/opensuse/leap/15.0 nvidia
   sudo zypper ref
   sudo zypper up
   sudo zypper dup

安装软件：
    htop net-tools-deprecated 