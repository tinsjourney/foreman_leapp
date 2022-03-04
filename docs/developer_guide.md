# Developer guide

## Leapp tool
### Installing on RHEL 7

**Register & subscribe**
```
subscription-manager register
subscription-manager list --available --match-installed
subscription-manager attach --pool POOL_ID
```

**Update to the latest `7.x` version**
```
yum clean all
yum update
reboot

cat /etc/os-release
# => RHEL is on latest version
```

**Install Leapp tool**
```
subscription-manager repos --enable rhel-7-server-rpms
subscription-manager repos --enable rhel-7-server-extras-rpms

yum install -y leapp
```
### Installing on CentOS 7

!!! There is an error when running `leapp preupgrade` command on `CentOS 7`, better try it on `RHEL 7` !!!

**Update to the latest `7.x` version**
```
yum clean all
yum update
reboot

cat /etc/os-release
```

**Install Leapp**
```
yum-config-manager --add-repo https://copr.fedorainfracloud.org/coprs/g/oamg/leapp/repo/epel-7/group_oamg-leapp-epel-7.repo

yum install yum-utils leapp
```

## Leapp commands

**Pre-upgrade check**
```
leapp preupgrade

# => /var/log/leapp/leapp-report.json (This one is parsed by foreman-leapp)
# => /var/log/leapp/leapp-report.txt
# => /var/log/leapp/leapp-preupgrade.log

leapp preupgrade --verbose  # Enable verbose logging
leapp preupgrade --debug    # Enable debug mode
```
For the report sample see the file in `report_samples` folder.

**Upgrade**

```
leapp upgrade
```

## Resources and documentation

* [Upgrading from RHEL 7 to RHEL 8](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html-single/upgrading_from_rhel_7_to_rhel_8)
* ~~[leapp-to.github.io/gettingstarted](https://leapp-to.github.io/gettingstarted)~~ is outdated, do not use!
* [Developer documentation for Leapp tool](https://leapp.readthedocs.io/en/latest/index.html)
