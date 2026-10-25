# 夏普 AQUOS R2 compact 803SH boot 镜像

从设备直接读出的原厂 boot 分区，未做任何修改。

| 项目 | 值 |
|---|---|
| 机型 | Sharp AQUOS R2 compact（803SH / SG803SH） |
| 系统 | Android 11 |
| 版本号 | S2003 |
| 安全补丁 | 2022-01-01 |
| 抓取日期 | 2026-10-25 |
| **当前系统槽位** | **`_b`** —— 即 `boot_b.img` 是现在正在用的系统 |

## 文件

| 文件 | 分区 | 大小 | SHA-256 |
|---|---|---|---|
| `boot_a.img` | boot_a（`/dev/block/sde28`） | 67,108,864 | `c3ebc8b10df1924732bb17b8d15954fb4968a8e5a6cd73d35ae54fa3ec6814ba` |
| `boot_b.img` | boot_b（`/dev/block/sde29`） | 67,108,864 | `7707a5e81f3a37237ae1d1219c9515ee4ab6d87ab3e358a06e66e0e15d7a0757` |

两个都是 Android boot image **header v1**，文件头 `ANDROID!`，page size 4096。
kernel 约 14.1 MB，ramdisk 约 10.6 MB。

## 提取方式

全程只读，没有写任何分区：

```sh
su -c "dd if=/dev/block/by-name/boot_a of=/sdcard/Download/boot_a.img bs=4096"
su -c "dd if=/dev/block/by-name/boot_b of=/sdcard/Download/boot_b.img bs=4096"
```

槽位由 `getprop ro.boot.slot_suffix` 确认为 `_b`。

## 说明

- 镜像为原厂未改动状态
- 刷写有风险，与本仓库无关
