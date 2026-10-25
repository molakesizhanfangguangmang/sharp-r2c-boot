# 夏普 AQUOS R2 compact 803SH boot 镜像

803SH 的 boot_a 和 boot_b，从机器上直接 dd 出来的原厂镜像。

- 系统 Android 11，版本号 S2003，安全补丁 2022-01-01
- 抓取日期 2026-10-25
- 机器当前跑在 b 槽，所以 **boot_b.img 就是现在这套系统**

| 文件 | 分区 | 大小 | SHA-256 |
|---|---|---|---|
| boot_a.img | boot_a（/dev/block/sde28） | 67,108,864 | c3ebc8b10df1924732bb17b8d15954fb4968a8e5a6cd73d35ae54fa3ec6814ba |
| boot_b.img | boot_b（/dev/block/sde29） | 67,108,864 | 7707a5e81f3a37237ae1d1219c9515ee4ab6d87ab3e358a06e66e0e15d7a0757 |

两个都是 Android boot header v1，开头是 `ANDROID!`，page size 4096，
kernel 约 14.1 MB，ramdisk 约 10.6 MB。

导出命令：

```sh
su -c "dd if=/dev/block/by-name/boot_a of=/sdcard/Download/boot_a.img bs=4096"
su -c "dd if=/dev/block/by-name/boot_b of=/sdcard/Download/boot_b.img bs=4096"
```

槽位看 `getprop ro.boot.slot_suffix`。
