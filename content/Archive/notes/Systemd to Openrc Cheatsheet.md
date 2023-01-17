# OpenRC to systemd Cheatsheet - Gentoo Wiki

2-3 minutes

---

This article is for users that have recently converted from OpenRC to systemd. It contains a list of commands commonly used in OpenRC and its equivalent systemd command.

**Note**  
The following table is not an exhaustive list and is not intended to replace reading man pages.

Start a service

/etc/init.d/<service> start  
rc-service <service> start

systemctl start <service>

Stop a service

/etc/init.d/<service> stop  
rc-service <service> stop

systemctl stop <service>

Restart a service

/etc/init.d/<service> restart  
rc-service <service> restart

systemctl restart <service>

Get service status

/etc/init.d/<service> status  
rc-service <service> status

systemctl status <service>

Show known startup scripts

rc-status  
rc-update show

systemctl list-units

Shows scripts that exist in runlevels

Show all startup scripts

ls /etc/init.d/  
rc-update -v show

systemctl list-unit-files --type=service

Shows all installed scripts

Enable service at startup

rc-update add <service> <runlevel>

systemctl enable <service>

Disable service at startup

rc-update del <service> <runlevel>

systemctl disable <service>

The following table is a list of useful systemd commands that have no OpenRC equivalent:

Command

Syntax

Comments

Disable automatically generated service

systemctl mask <service>

Disables dynamically generated services in systemd, which unit files are generated on demand (usually storage triggered services).

Kill all processes related to service

systemctl kill <service>

Show logs events that happened today, most recent events first

journalctl -r --since=today

Show log events for a specific service

journalctl _SYSTEMD_UNIT=<service>.service