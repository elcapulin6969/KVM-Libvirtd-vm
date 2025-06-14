## Plantilla de Proyecto de Tesis en Jupyter

Esta plantilla facilita la organización y desarrollo de una tesis académica utilizando Jupyter Notebooks, promoviendo la claridad, coherencia y accesibilidad.
Perfecto. A continuación te presento una **guía completa en terminal**, que instala automáticamente los requisitos, configura `quickemu`, `quickget`, `quickgui`, y crea máquinas virtuales listas para usar de **Debian** y **NixOS** — **todo con comandos en terminal, automatizado, en formato paso a paso**. Este método es ideal para desarrolladores y tareas DevOps.


### Debian

For **Debian bookworm+** on Intel / AMD you need to install:

``shell
sudo apt install --no-install-recommends qemu-kvm qemu-system-x86 libvirt-daemon-system libvirt-clients virt-manager gir1.2-spiceclientgtk-3.0 dnsmasq-base qemu-utils iptables safe-rm xz-utils

sudo apt-get install bash coreutils curl genisoimage grep jq mesa-utils ovmf pciutils procps python3 qemu sed socat spice-client-gtk swtpm-tools unzip usbutils util-linux uuidgen-runtime xdg-user-dirs xrandr zsync 

sudo apt-get install bash coreutils curl genisoimage grep jq mesa-utils ovmf pciutils procps python3 qemu sed socat spice-client-gtk swtpm-tools unzip usbutils util-linux uuidgen-runtime xdg-user-dirs xrandr zsync ethtool network-manager firmware-linux firmware-linux-free firmware-misc-nonfree intel-microcode amd64-microcode libvirt-daemon-system virt-manager
```

System administration is limited to the root user by default. To enable a regular user, run the following commands.

`/etc/libvirt/libvirtd.conf` file for editing.

sudo nano /etc/libvirt/libvirtd.conf

Set the domain socket group ownership to libvirt.

unix\_sock\_group = "libvirt"

Adjust the Unix socket permissions for the R/W socket.

unix\_sock\_rw\_perms = "0770"

##  quickemu/quickgui

```shell
git clone https://github.com/quickemu-project/quickemu
cd quickemu
```
