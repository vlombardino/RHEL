## List open ports & services
firewall-cmd --list-all
firewall-cmd --zone=public --list-ports
firewall-cmd --list-services

## Open ports
firewall-cmd --permanent --add-port={80/tcp,443/tcp}
firewall-cmd --reload
systemctl enable nginx
systemctl restart firewalld
firewall-cmd --zone=public --list-ports

## Remove port
firewall-cmd --zone=public --remove-port=80/tcp
firewall-cmd --runtime-to-permanent 
firewall-cmd --reload 
systemctl restart firewalld
firewall-cmd --zone=public --list-ports

## Closing Ports
firewall-cmd --zone=public --remove-port={80/tcp,443/tcp}
firewall-cmd --runtime-to-permanent 
firewall-cmd --reload
systemctl restart firewalld
firewall-cmd --zone=public --list-ports

## Check open ports
> localhost
ss -tulpn | grep LISTEN
> Remote
nc -z -v test.com 1-65535 2>&1 | grep succeeded
nmap -sTU -O test.com
