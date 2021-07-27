# 概要
ゼロからのOS自作入門の勉強記録です  
X86_64ではなくAAech64で進めることを目標にしています。

## 本
http://zero.osdev.jp/
## Git
https://github.com/uchan-nos/mikanos

# 環境構築の参考
## Dockerコンテナ情報
https://github.com/sarisia/mikanos-docker
## AArch64対応情報
https://github.com/uchan-nos/os-from-zero/wiki/kaz399;-AArch64%E5%90%91%E3%81%91%E3%81%AE%E7%92%B0%E5%A2%83%E6%A7%8B%E7%AF%89%E6%89%8B%E9%A0%86

# 開発環境
## メインPC
- Windows10
- VSCode + devcontainer
# 開始手順
1. 本リポジトリをgit clone
2. ダウンロードしたフォルダをVScodeで開く

## ターゲットボード
「Raspberry Pi 3 Model B+」を想定する。  
上記対応のUEFIは下記から入手できる。  
[Raspberry Pi 3 UEFI Firmware Images](https://github.com/pftf/RPi3)

# AArch64対応メモ
## 第2章
build手順は本と同じ、AArch64対応のため下記2ファイルに修正を加える
```
■ ~/edk2/Conf/target.txt (本の手順で作成)
- TARGET_ARCH           = X64
+ TARGET_ARCH           = AARCH64

■ MikanLoaderPkg/MikanLoaderPkg.dsc　（cloneしたものは修正済み）
- SUPPORTED_ARCHITECTURES        = X64
+ SUPPORTED_ARCHITECTURES        = AARCH64
```
のように修正しbuildする。  
すると「~/edk2/Build/MikanLoaderAARCH64/DEBUG_CLANG38/AARCH64/Loader.efi」が生成される。  
このファイルをラズパイのUEFI用に作成したSDカードの「efi/boot/bootaa64.efi」として配置する。  
後はSDを挿入して起動すればよい

