## Red Hat update error
```bash
This system is registered with an entitlement server, but is not receiving updates. You can use subscription-manager to assign subscriptions.
```

## Red Hat fix update error
```bash
sudo -i
subscription-manager remove --all
subscription-manager unregister
subscription-manager clean
dnf clean all
rm -rf /var/cache/yum/*
subscription-manager register
subscription-manager attach --auto
```

## Check subscription
```bash
subscription-manager list
```
