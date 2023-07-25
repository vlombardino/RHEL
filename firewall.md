## List open ports & services
```bash
firewall-cmd --list-all
firewall-cmd --zone=public --list-ports
firewall-cmd --list-services
```

## Open ports
```bash
firewall-cmd --permanent --add-port={80/tcp,443/tcp}
firewall-cmd --reload
systemctl enable nginx
systemctl restart firewalld
firewall-cmd --zone=public --list-ports
```

## Remove port
```bash
firewall-cmd --zone=public --remove-port=80/tcp
firewall-cmd --runtime-to-permanent 
firewall-cmd --reload 
systemctl restart firewalld
firewall-cmd --zone=public --list-ports
```

## Closing Ports
```bash
firewall-cmd --zone=public --remove-port={80/tcp,443/tcp}
firewall-cmd --runtime-to-permanent 
firewall-cmd --reload
systemctl restart firewalld
firewall-cmd --zone=public --list-ports
```

## Check open ports
> localhost
```bash
ss -tulpn | grep LISTEN
```
> Remote
```bash
nc -z -v test.com 1-65535 2>&1 | grep succeeded
nmap -sTU -O test.com
```
