## Restart networking [run as root]
```bash
nmcli networking off && nmcli networking on
```

## Set static IP
```bash
nmcli device status
nmcli device show eth0
```

```bash
nmcli con mod eth0 ipv4.addresses 192.168.1.80/24
nmcli con mod eth0 ipv4.gateway 192.168.1.1
nmcli con mod eth0 ipv4.method manual
nmcli con mod eth0 ipv4.dns "8.8.8.8"
nmcli con up eth0
```

## Autoconnect
```bash
nmcli con mod eth0 connection.autoconnect yes
```

## Bonding
```bash
nmcli connection add type bond con-name bond0 ifname bond0 bond.options "mode=balance-tlb,miimon=1000"
nmcli device status
nmcli connection modify eth0 master bond0
nmcli connection modify eth1 master bond0
nmcli connection up eth0
nmcli connection up eth1
nmcli connection up bond0
nmcli device
```

### Notes
```bash
nmcli device
```
> Delete Connection
```bash
nmcli connection delete eth0
```
> Add Connection
```bash
nmcli con add type ethernet con-name eth0 ifname eth0
nmcli device modify eth0 ipv4.method auto
```
