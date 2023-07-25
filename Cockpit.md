## Cockpit Install
Install packages
```bash
dnf install cockpit
```

Enable cockpit
```bash
systemctl enable --now cockpit.socket
```

Open Firewall for cockpit
```bash
firewall-cmd --add-service=cockpit --permanent
firewall-cmd --reload
```

##Certificates
Backup Original Certs
```bash
sudo su
mkdir -p /tmp/certs
mv /etc/cockpit/ws-certs.d/0-self-signed* /tmp/certs/
```

Copy certificates [test]
```bash
cp /tmp/test.com* /etc/cockpit/ws-certs.d/
```

Change permissions
```bash
chown root:cockpit-ws /etc/cockpit/ws-certs.d/*
```

Restart cockpit
```bash
systemctl restart cockpit
```
