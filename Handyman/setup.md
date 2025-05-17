# 競技における事前セットアップ

## 概要
RCSO25に出場するには，ROS 2の環境とSIGVerseの環境の2つの環境を整える必要があります．

### IP アドレスの設定
ROS 2 を実行するPCと，Windows側のSIGVerseシミュレータがネットワーク通信できるようにするため，以下のように固定IPアドレスを設定します．
| Device  | IP Adress |
| --- | --- |
| Windows PC | 192.168.0.1 |
| ROS2 実行PC | 192.168.0.2 |

### ROS 2環境
本大会では，ROS 2 のみ対応となっております．そのため，開発は ROS 2 環境にて進めてください．\
推奨バージョンは以下の通りです．
| System  | Version |
| --- | --- |
| Ubuntu | 22.04 (Jammy Jellyfish) |
| ROS    | Humble Hawksbill |

### SIGVerse環境設定
SIGVerseは，Unity上で動くシミュレーション環境です．Unityをインストールした上で，SIGVerse環境をセットアップしてください．
- [SIGVerse環境とROS2 HumbleでHSRを動かすためのセットアップ方法](https://esa-pages.io/p/sharing/19758/posts/108/5ee40954d9b18a8cd0ea.html)

### 競技環境レイアウト設定
Handymanをはじめ，レイアウト，物体の位置などを変更したい場合は，SIGVerseConfigを変更する必要があります．以下のリンクは，その仕方について述べます．
- [SIGVerseのレイアウト設定方法](https://esa-pages.io/p/sharing/19758/posts/81/3eb70fdabe437dcbf15d.html)
