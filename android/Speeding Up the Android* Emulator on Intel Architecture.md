### KVM 설치

```bash
sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
sudo adduser `whoami` kvm
sudo adduser `whoami` libvirtd
```

### inotify
```bash
echo 'fs.inotify.max_user_watches = 524288' >> /etc/sysctl.conf
sudo sysctl -p
```
