### Arch linux nvidia proprietární ovladače - nvidia
```bash
sudo yay -S nvidia nvidia-dkms nvidia-utils nvidia-settings lib32-nvidia-utils
sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
```

/etc/mkinitcpio.conf
```
MODULES=(nvidia nvidia_modeset nvidia_uvm nvidia_drm)
```

```bash
sudo mkinitcpio -p linux
nvidia-xconfig
```

/etc/X11/xorg.conf
```
Section "Files"
    ModulePath "/usr/lib/nvidia/xorg"
    ModulePath "/usr/lib/xorg/modules"
EndSection
```
Pokud toto přeskočíme OpenGL bude využívat mesa driver

