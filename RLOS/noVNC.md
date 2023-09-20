# Install [noVNC](https://novnc.com/info.html)
```
sudo dnf install epel-release
sudo dnf install novnc
```

### Allow VNC & noVNC firewall access
```
sudo firewall-cmd --permanent --add-port=6080/tcp
sudo firewall-cmd --permanent --add-port=5900/tcp
sudo firewall-cmd --reload
```

### Check ports
```
sudo lsof -i -P -n | grep LISTEN
sudo netstat -ltnp
```

### Configure Vino 
> Run per user
```
gsettings set org.gnome.Vino require-encryption false
```

### Test connection
```
sudo /usr/bin/novnc_proxy --vnc localhost:5900 --listen 6080
```

### Create systemd startup service
```
sudo vim /etc/systemd/system/novnc.service
```
```bash
[Unit]
Description=noVNC Service

[Service]
Type=simple
ExecStart=/usr/bin/novnc_proxy --vnc localhost:5900 --listen 6080

[Install]
WantedBy=multi-user.target
```

### Enable novnc service
```
sudo systemctl start novnc
sudo systemctl status novnc
sudo systemctl enable novnc
```

### Reload services
```
systemctl daemon-reload
```

### Web Access [example]
http://192.168.1.100:6080/vnc.html

---

## Git Install
### Install required software
```
sudo su
dnf update
dnf install git python3 python3-numpy python3-pillow python3-websockify
```

### Clone noVNC
```
git clone https://github.com/novnc/noVNC.git /opt/novnc
cd /opt/novnc
```

## Self Signed Certificate
### Create certs
```
sudo su
cd /etc/pki/tls/certs
openssl req -x509 -nodes -newkey rsa:4096 -keyout /etc/pki/tls/certs/novnc.pem -out /etc/pki/tls/certs/novnc.pem -days 365
```

### Certs permission
```
sudo chmod 600 /etc/ssl/certs/your-server-name.crt
sudo chmod 600 /etc/ssl/private/your-server-name.key
```
