설치:
```bash
sudo coreos-install -d /dev/sda -C stable -c start.yaml
```

사용자 추가:
```bash
sudo useradd -G sudo,docker sysop
sudo passwd sysop
```

vagrant:
```bash
git clone https://github.com/coreos/coreos-vagrant.git
```
