# mac OSX 上开发环境准备：

## 安装NASM

```sh
brew install nasm
```

or

```sh 
brew update nasm
```

## 安装QEMU

```sh
brew install qemu
```

## 编译代码

```sh
% nasm ipl.nas 
ipl.nas:58: error: attempt to reserve non-constant quantity of BSS space
```

## 修改代码

修改58行为
RESB    510 -($-$$)

## 重新编译

```sh
% nasm ipl.nas
ipl.nas:27: warning: uninitialized space declared in .text section: zeroing [-w+zeroing]
ipl.nas:58: warning: uninitialized space declared in .text section: zeroing [-w+zeroing]
```

编译通过。

## 转成IMAGE文件

```sh
% cp ipl os.img
```

## 运行模拟器

```sh
% qemu-system-x86_64 -fda os.img
WARNING: Image format was not specified for 'os.img' and probing guessed raw.
         Automatically detecting the format is dangerous for raw images, write operations on block 0 will be restricted.
         Specify the 'raw' format explicitly to remove the restrictions.
```
