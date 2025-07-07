# Chapter 1

## SSH key-based authentication

### SSH keys generation
```bash
ssh-keygen
ssh-keygen -f .ssh/key-with-pass
ssh-keygen -N "" -f ~/.ssh/edtroleis_rsa


useradd -G wheel edtroleis

ssh -o PreferredAuthentications=password serverb
ssh server

cat ~/.ssh/config

# show who is logged on and they are doing
w --from
```

### Share the public key
```bash
ssh-copy-id -i .ssh/key-with-pass.pub user@remotehost
ssh -i .ssh/key-with-pass user@remotehost
ssh -v user@remotehost
```

# Create a diagnostic report
```bash
# install sos
dnf install -y sos | tail -4

# configuration file for sos
vim /etc/sos/sos.conf

# run sos report
sos report -l | less
sos report

mkdir -pv /root/sos_reports
sos report -o /root/sos_reports
tar xf /root/sos_reports/sos-*.tar.xz -C /root/sos_reports

sos report --upload
```

# Red Hat Insights
1. The Insights client collects system metadata on the Red Hat Enterprise Linux system.
2. The Insights client uploads system metadata to the Red Hat Insights service.
3. Red Hat Insights analyzes system metadata to determine which issues and recommendations apply.
4. The administrator views the recommended actions in the Red Hat Insights customer portal.

```bash
insights-client --register
insights-client --status
insights-client --run
```
