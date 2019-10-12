apt-get install -y  kmod ssh

安装add-apt-repository

    apt-get install python-software-properties
    apt install software-properties-common

mame

    #Remove old sdlmame repositories (if any):
    sudo rm -f /etc/apt/sources.list.d/sdlmame4ubuntu.*
    #Add the main repository for unofficial builds:
    sudo add-apt-repository ppa:c.falco/mame
    #Now update the information on your box:
    sudo apt-get update
    #Finally install the package from the repository:
    sudo apt-get install mame