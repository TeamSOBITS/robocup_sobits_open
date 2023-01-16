# **RoboCup SOBITS Open Simulation Leagueについて**

SOBITSでは，RoboCupを模した競技会である「RoboCup SOBITS Open」を開催しています．
これは，RoboCupに出場したことのないメンバー(主にB3，B4)のみなさんに，開発に必要な力を身につけてもらうことを目的とした競技会になります．

ここでは，春休みに開催されるシミュレーションを用いた基本的な技能を競い合う「Simulation League」について述べます．
競技会への参加は任意ですので，参加したいと思う方のみで，後述する競技内容に従って競っていただきます．
競技の開発は1人で行ってもらいますが，競技で用いる1つ1つの要素技術はSOBITSのパッケージとしてまとめられており，それらを使いこなすことで初学者の方でも充分に1人で挑戦できる競技内容になっています．
本競技会は，基本的に先輩から開発に関するアプローチは行いませんので，主体的に行動するよう心掛けて下さい．

本競技会での開発には，機能を実現する技術力はもちろん，壁にぶつかったときの突破力や，期限が決まった中で開発を進める計画力，その計画を実行する行動力など，様々な力が必要になります．
この「RoboCup SOBITS Open」が，このような力を身に付けるきっかけとなって，みなさんの今後の研究生活に役立てることができると，とても嬉しく思います．
そして，毎年開催されるRoboCupでの優勝を目指して，チームSOBITSの開発力をグッと高める機会にしていきましょう！！

## **目次**

1. [**Simulation League(SRL)**](#simulation-robot-leaguesrl)
    1. [競技内容(SRL)](#1-競技内容srl)
    2. [競技手順(SRL)](#2-競技手順srl)
    3. [競技の点数表(SRL)](#3-競技の点数表srl)

## **Simulation Robot League(SRL)**

Simulation Leagueについて説明していきます．Simulation Leagueは，基本的に秋セメスターが終わった後の春休み中に，約3週間程度で開発を進めてもらいます．以下から競技の内容について説明していきます．

### 1. 競技内容(SRL)

Simulation Leagueでは，RoboCup Simulation Leagueで行われたHandymanタスクを模した競技を行います．
Handymanタスクでは，与えられた命令文を解析し、ロボットが自律的に移動し，注文された物を掴み，別のところまで運ぶことを行います．
今回は競技を簡単にするために，家具や把持物体などの位置を含めたファイルを共有します．
環境や把持物体はランダムに決定されます．

### 2. 競技手順(SRL)

本競技では，画像に示すアリーナを用います．
競技の手順は以下の通りになります．

1. モデレータの指示を聞く
2. 指定された部屋へ移動する
3. 指定された物体を探索する
4. その物体を把持する
5. 指示された置き位置へ物体を運ぶ
6. 置き位置に物体を置く

- 本競技の解説動画：smb://192.168.11.72/share/robocup/RCSO/2022_winter/handyman_demo.mp4

競技開始後，セッション中に動作しなくなった場合はそのセッションをスキップし、次セッションから再起動できます．
制限時間は各セッション600秒です．

### 3. 競技の点数表(SRL)

<table>
    <tr>
        <th>タスク内容</th>
        <th>得点</th>
    </tr>
    <tr>
        <td>セッションの開始</td>
        <td>0点</td>
    </tr>
    <tr>
        <td>命令文章を解析する（挑戦：多様な表現）</td>
        <td>10点（20点）</td>
    </tr>
    <tr>
        <td>指定された部屋へ移動する</td>
        <td>20点</td>
    </tr>
    <tr>
        <td>指定された物体を探索する</td>
        <td>20点</td>
    </tr>
    <tr>
        <td>問題文の間違いを指摘</td>
        <td>50点</td>
    </tr>
    <tr>
        <td>指定された物体を把持する</td>
        <td>30点</td>
    </tr>
    <tr>
        <td>指定された場所を指定された場所に運ぶ</td>
        <td>10点</td>
    </tr>
    <tr>
        <td>指定された場所に物体を置く</td>
        <td>20点</td>
    </tr>
    <tr>
        <td>衝突による減点(ロボット or 物体)</td>
        <td>衝撃の強さにより変動</td>
    </tr>
    <tr>
        <td>合計</td>
        <td>160(170)点</td>
    </tr>
</table>

本競技は，1人3セッション挑戦することができ，3セッションの総合得点で順位を決めます．  
得点圏に至らない人が多かった場合は審査員側で実行過程に評価点を入れます．  
実機と違い、課題のスキップ等はできません．
得点獲得までに踏まなければならないステップが非常に多いため、teleopで実行してみるなどしてイメージが掴みやすいと思います.

---

## 追記情報
### 2023/01/05

必ず用いる必要のあるパッケージに関して

- [sobit_common(branch:nostic_sigverse)](https://github.com/TeamSOBITS/sobit_common/tree/noetic_sigverse)
- [hsr_ros(branch:noetic_sigverse_2022)](https://github.com/TeamSOBITS/hsr_ros/tree/noetic_sigverse_2022)

### 2023/01/12

- [物体リスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2022_srl/object_list/graspable_object_list.txt)
- [置き位置リスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2022_srl/object_list/destination_list.txt)
- [家具などすべてのオブジェクトリスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2022_srl/object_list/other_object_list.txt)

を追加しました．

### 2023/01/16

競技で使用する環境は以下の4環境です。
「Layout2019HM01」
「Layout2019HM02」
「Layout2020HM01」
「Layout2021HM01」

追加でアドバイスなのですが、運営（三江、大熊、向川）では教えられる範囲に限りがあります。
そのため競技者間で教えあったり、前にメインを担当していた人や先輩に聞くことでより開発が効率的に進むと思います。
ルールや仕様などに関しては運営への質問をお願いします。

[トップに戻る](#robocup-sobits-openについて)
