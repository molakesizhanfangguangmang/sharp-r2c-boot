# 夏普 AQUOS R2 compact 803SH boot 镜像

本仓库提供 Sharp AQUOS R2 compact（803SH）的 boot_a 与 boot_b 分区镜像，由设备直接导出。

## 设备信息

| 项目 | 值 |
|---|---|
| 机型 | AQUOS R2 compact（803SH / SG803SH） |
| 系统版本 | Android 11 |
| 版本号 | S2003 |
| 安全补丁 | 2022-01-01 |
| 导出日期 | 2026-10-25 |
| 当前槽位 | `_b` |

当前系统运行于 b 槽，`boot_b.img` 对应当前系统。

## 文件

| 文件 | 分区 | 大小（字节） | SHA-256 |
|---|---|---|---|
| `boot_a.img` | boot_a（`/dev/block/sde28`） | 67,108,864 | `c3ebc8b1…ec6814ba` |
| `boot_b.img` | boot_b（`/dev/block/sde29`） | 67,108,864 | `7707a5e8…5d7a0757` |

两个镜像均为 Android boot image header v1，文件头 `ANDROID!`，page size 4096；kernel 约 14.1 MB，ramdisk 约 10.6 MB。

完整校验值：

```
c3ebc8b10df1924732bb17b8d15954fb4968a8e5a6cd73d35ae54fa3ec6814ba  boot_a.img
7707a5e81f3a37237ae1d1219c9515ee4ab6d87ab3e358a06e66e0e15d7a0757  boot_b.img
```

## 导出命令

```sh
su -c "dd if=/dev/block/by-name/boot_a of=/sdcard/Download/boot_a.img bs=4096"
su -c "dd if=/dev/block/by-name/boot_b of=/sdcard/Download/boot_b.img bs=4096"
```

槽位可通过 `getprop ro.boot.slot_suffix` 查看。
