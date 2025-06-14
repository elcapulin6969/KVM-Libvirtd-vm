# KVM/QEMU Virtualization Guide (Linux)

## 1. Introduction

This guide consolidates essential commands and configurations for KVM/QEMU virtualization on Linux. It aims to provide a streamlined, academic-style reference for managing virtual machines.

egrep -c '(vmx|svm)' /proc/cpuinfop
sudo modprobe kvm; echo 1 | sudo tee /sys/module/kvm/parameters/ignore_msrs

Update package lists and install core dependencies:

```bash
sudo apt update && sudo apt install -y git wget qemu-full libvirt-daemon-system libvirt-clients dnsmasq python3
### KVM libvirt

For **Debian bookworm+** on Intel / AMD you need to install:

``bash
sudo apt-get install --no-install-recommends qemu-kvm qemu-system-x86 libvirt-daemon-system libvirt-clients virt-manager gir1.2-spiceclientgtk-3.0 dnsmasq-base qemu-utils iptables safe-rm xz-utils

sudo apt-get  install -y uml-utilities libguestfs-tools p7zip-full make dmg2img tesseract-ocr tesseract-ocr-eng genisoimage vim net-tools screen gir1.2-spiceclientgtk-3.0 safe-rm xz-utils qemu-utils iptables

sudo apt-get install bash coreutils curl genisoimage grep jq mesa-utils ovmf pciutils procps python3 qemu sed socat spice-client-gtk swtpm-tools unzip usbutils util-linux uuidgen-runtime xdg-user-dirs xrandr zsync 

sudo apt-get install bash coreutils curl genisoimage grep jq mesa-utils ovmf pciutils procps python3 qemu sed socat spice-client-gtk swtpm-tools unzip usbutils util-linux uuidgen-runtime xdg-user-dirs xrandr zsync ethtool network-manager firmware-linux firmware-linux-free firmware-misc-nonfree intel-microcode amd64-microcode libvirt-daemon-system virt-manager
```


``bash
sudo systemctl enable libvirtd

sudo systemctl start libvirtd
sudo systemctl restart libvirtd

```



System administration is limited to the root user by default. To enable a regular user, run the following commands.

`/etc/libvirt/libvirtd.conf` file for editing.


```bash
sudo sed -i \
-e 's/^#unix_sock_group = "libvirt"$/unix_sock_group = "libvirt"/' \
-e 's/^#unix_sock_rw_perms = "0770"$/unix_sock_rw_perms = "0770"/' \
-e 's/^#auth_unix = "none"$/auth_unix = "polkit"/' \
/etc/libvirt/libvirtd.conf
```


```bash
sudo virsh -c qemu:///system net-autostart default
sudo virsh -c qemu:///system net-start default
```

sudo systemctl enable libvirtd

sudo systemctl start libvirtd



##  quickemu/quickgui

```shell
git clone https://github.com/quickemu-project/quickemu
cd quickemu
```
