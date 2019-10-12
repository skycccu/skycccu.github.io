```
#!/bin/bash

    # Install Shadowsocks on CentOS 7
    
    echo “Installing Shadowsocks...“
    random-string()
    {
        cat /dev/urandom | tr -dc \'a-zA-Z0-9\' | fold -w ${1:-32} | head -n 1
    }
    CONFIG_FILE=/etc/shadowsocks.json
    SERVICE_FILE=/etc/systemd/system/shadowsocks.service
    SS_IP=`ip route get 1 | awk \'{print $NF;exit}\'`
    SS_METHOD=aes-256-cfb
    SS_TIMEOUT=600
    GET_PIP_FILE=/tmp/get-pip.py
    # install pip
    curl “https://bootstrap.pypa.io/get-pip.py“ -o “${GET_PIP_FILE}“
    python ${GET_PIP_FILE}
    # install shadowsocks
    pip install --upgrade pip
    pip install shadowsocks
    # create shadowsocls config
    cat <<EOF | sudo tee ${CONFIG_FILE}
    {
        “server“:“0.0.0.0“,
        “port_password“:{
            “00000“:“xxxxxxxx“
        },
        “timeout“:${SS_TIMEOUT},
        “method“:“${SS_METHOD}“
    }
    EOF
    # create service
    cat <<EOF | sudo tee ${SERVICE_FILE}
    [Unit]
    Description=Shadowsocks
    [Service]
    TimeoutStartSec=0
    ExecStart=/usr/bin/ssserver -c ${CONFIG_FILE}
    [Install]
    WantedBy=multi-user.target
    EOF
    # start service
    systemctl enable shadowsocks
    systemctl start shadowsocks
    # view service status
 sleep 5
    systemctl status shadowsocks -l
    echo “================================“
    echo ““
    echo “Congratulations! Shadowsocks has been installed on your system.“
    echo “You shadowsocks connection info:“
    echo “--------------------------------“
    echo “server:      ${SS_IP}“
    echo “user:        00000:XXXXXXXXX“
    echo “method:      ${SS_METHOD}“
    echo “--------------------------------“
```