# [KasmVNC](https://github.com/kasmtech/KasmVNC)

### Operating System & Software
- Rocky Linux 8 (gnome)
- KasmVNC

### Update & Upgrade
```bash
sudo dnf update -y
```
### Disable wayland
```bash
sudo sed -i 's/^#.*WaylandEnable=.*/WaylandEnable=false/' /etc/gdm/custom.conf
```

### Install required software
```bash
sudo dnf install epel-release -y
sudo dnf config-manager --set-enabled powertools
sudo dnf install moreutils
```

### Download & install [KasmVNC Releases](https://github.com/kasmtech/KasmVNC/releases)
```bash
wget https://github.com/kasmtech/KasmVNC/releases/download/v1.1.0/kasmvncserver_centos_core_1.1.0_x86_64.rpm

sudo dnf reinstall ./kasmvncserver_centos_core_1.1.0_x86_64.rpm
```

### Add $USER to kasmvnc-cert group
```bash
sudo usermod -a -G kasmvnc-cert $USER

sudo reboot
```

### Create a session
> Run the following:
```bash
vncserver
```

### Open port outputted port from a created session 
```bash
sudo firewall-cmd --zone=public --add-port=8446/tcp --permanent
sudo firewall-cmd --reload
```

### Close port if not used
```bash
sudo firewall-cmd --zone=public --permanent --remove-port 8446
sudo firewall-cmd --reload
```
