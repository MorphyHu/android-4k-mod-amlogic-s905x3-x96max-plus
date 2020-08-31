# android-4k-mod-amlogic-s905x3-x96max-plus
<https://github.com/sceext2/android-4k-mod-amlogic-s905x3-x96max-plus>

Modify Android system UI from 1920x1080 to 3840x2160. (for x96-max+ box)


## Box hardware

+ Product name: `x96 max+`

+ SoC: `Amlogic S905X3`

+ RAM: `4 GB`

+ eMMC storage: `64 GB`

+ OS: `Android 9`


## How to apply this patch

1. Switch to root before continue

  ```
  franklin:/ $ su
  franklin:/ # 
  ```

2. Flash the `dtbo` image

  ```
  franklin:/ # dd if=dtbo-4k.img of=/dev/block/dtbo
  ```

3. Remount `/vendor` to read-write

  ```
  franklin:/ # mount -o remount,rw /vendor
  ```

4. Replace the stock hwcomposer

  ```
  franklin:/ # cp hwcomposer.amlogic-4k.so /vendor/lib/hw/hwcomposer.amlogic.so
  ```

5. Reboot and enjoy !

  ```
  franklin:/ # sync
  franklin:/ # reboot
  ```


## Test after apply

Use this command:

```
franklin:/ # wm size
Physical size: 3840x2160
```

```
franklin:/ # wm density
Physical density: 240
```

```
franklin:/ # dumpsys display
```

```
franklin:/ # dumysys SurfaceFlinger
```

```
franklin:/ # cat /proc/device-tree/fb/sceext_4k
20200825 1946
```


## Known issue

+ After change the system screen resolution from 1920x1080 to 3840x2160,
  there will be performance decrease of graphics.


## Detail explanation

Please see [here](doc/).

(`sceext 2020-08-31 d700`)
