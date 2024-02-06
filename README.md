> Run Sh as usual and don't forget to change the config.json!
> With this you can run Windows on Linux, Ubuntu, Debian and so on 


## Run ⏳

```
wget -O win.iso "paste your iso"
```
```
sudo apt update
```
```
sudo apt install qemu-kvm -y
```

## Setup Qemu // 15G That is the storage that will be set for hard disk storage, You can change as you like.
```
qemu-img create -f raw win.img 15G
```
```
sudo qemu-system-x86_64 -m 4G -smp 2 -cpu host -boot order=c -drive file=win.iso,media=cdrom -drive file=win.img,format=raw -device usb-ehci,id=usb,bus=pci.0,addr=0x4 -device usb-tablet -vnc :0 -smp cores=2 -device e1000,netdev=n0 -netdev user,id=n0 -vga qxl -accel kvm -bios bios64.bin
```

## Use Ngrok

```
./ngrok authtoken <insert authtoken here>
```
```
./ngrok tcp 5900
```

## Use Playit.gg ⏳

```
curl -SsL https://playit-cloud.github.io/ppa/key.gpg | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/playit.gpg >/dev/null
echo "deb [signed-by=/etc/apt/trusted.gpg.d/playit.gpg] https://playit-cloud.github.io/ppa/data ./" | sudo tee /etc/apt/sources.list.d/playit-cloud.list
sudo apt update
sudo apt install playit
```
