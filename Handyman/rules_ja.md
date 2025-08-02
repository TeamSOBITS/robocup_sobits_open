> [!WARNING]
> Rulesは今後更新される可能性があります．

## **Handyman Rules for RCSO2025**

RoboCup Simulation Leagueで行われた競技の1つであるHandymanタスクについて説明していきます．

## **目次**

1. [競技内容(Handyman)](#1-競技内容handyman)
2. [競技手順(Handyman)](#2-競技手順handyman)
3. [競技の点数表(Handyman)](#3-競技の点数表handyman)


### 1. 競技内容(Handyman)

Handymanタスクでは，与えられた命令文を解析し，ロボットが自律的に移動し，注文された物を掴み，別のところまで運ぶタスクを行います．
今回は競技を簡単にするために，把持・配置地点のリストや把持物体などの位置を含めた情報を掲載します．
環境や把持物体はランダムに決定されます．

- 本競技は，1人3セッション挑戦することができ，3セッションの総合得点で順位を決めます．
- 実機と違い，タスクのスキップ等はできません．
- 競技開始後，セッション中に動作しなくなった場合はそのセッションをスキップし，次セッションから再起動できます
- [環境レイアウトと把持・配置地点のリスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/layout_and_location_list.md)，や[把持物体リスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/object_list.md)は，事前に公開しているので，ご確認ください．
- 制限時間は各セッション600秒です．

### 2. 競技手順(Handyman)

競技の手順は以下の通りになります．

1. モデレータの指示を聞く
2. 指示された部屋へ移動する
3. 指示された物体を探索する
4. その物体を把持する
5. 指示された置き位置へ物体を運ぶ
6. 置き位置に物体を置く

#### 2.1. 競技手順の流れ

具体的な競技手順の流れは以下の通りになります．

1. 競技者がUbuntu側で使用するコードをすべて起動した後，運営側がWindows側のシミュレータを起動します．
2. モデレータは「Are_you_ready?」をロボットへ送信します．そして同時に「Environment」メッセージも発信します．
3. ロボットは「I_am_ready」メッセージをモデレータに送信します．
4. モデレータはロボットに「指示」のメッセージを送ります．
5. ロボットは指定された部屋に移動します．
6. ロボットは「Room_reached」メッセージをモデレータに送信します．
7. ロボットが物体を探します．
8. ロボットは物体を把持します．
9. ロボットは「Object_grasped」メッセージをモデレータに送信します.
10. ロボットは置き位置に物体を置きます．
11. ロボットは「Task_finished」メッセージをモデレータに送信します.
- タスクが終了した場合（成功または失敗）: モデレータは「Task_succeeded」 (タスク成功) または「Task_failed」 (タスク失敗) メッセージをロボットに送信します．すべてのタスクが終了した際に，モデレータはロボットに「Mission_complete」メッセージを送信します．
- 制限時間が終了した場合: モデレータは，タスクが失敗したことを示す「Task_failed」メッセージをロボットに送信します．
- ロボットは，タスクを達成できない場合に「Give_up」メッセージを送信できます．その場合，タスクは中止され「Task_failed」メッセージが送信され，次のセッションに進みます．
  - 競技者またはロボットがGive Upを宣言することができます．そのセッションのその時点までの点数を確保され，次のセッションに移ります．

<h3>3. 競技の点数表（Handyman）</h3>
<p>※ 競技の点数は変更の可能性があります．ご了承ください．</p>

<table border="1" cellspacing="0" cellpadding="6">
  <thead>
    <tr>
      <th>タスク内容</th>
      <th>基準点数</th>
      <th>挑戦内容</th>
      <th>挑戦点数</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>-</td>
      <td>0点</td>
      <td>セッション切り替え</td>
      <td>20点</td>
    </tr>
    <tr>
      <td>命令文章を解析する</td>
      <td>10点</td>
      <td>多様な表現に対応</td>
      <td>20点</td>
    </tr>
    <tr>
      <td>指定された部屋へ移動する</td>
      <td>10点</td>
      <td>二つ目のmapで指定された部屋へ移動※1</td>
      <td>20点</td>
    </tr>
    <tr>
      <td>指定された物体の認識</td>
      <td>20点</td>
      <td>透明物体</td>
      <td>40点</td>
    </tr>
    <tr>
      <td>指定された物体の把持</td>
      <td>30点</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <td>物体を指定場所へ運搬</td>
      <td>10点</td>
      <td>ランダムな位置にいる人に手渡し※2</td>
      <td>30点</td>
    </tr>
    <tr>
      <td>物体を指定場所に配置</td>
      <td>20点</td>
      <td>-</td>
      <td>-</td>
    </tr>
    <tr>
      <td><strong>合計</strong></td>
      <td><strong>100点</strong></td>
      <td></td>
      <td><strong>180点</strong></td>
    </tr>
  </tbody>
</table>

- ※1：3セッションのうち，1セッションのみで2つ目のマップが使用されます．挑戦課題のレイアウトについては[Layout2019HM02](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/layout_and_location_list.md#layout2019hm02-%E6%8C%91%E6%88%A6%E8%AA%B2%E9%A1%8C)をご参照ください．
- ※2：人がいる部屋は，命令文の中で明示されます．また，手渡し動作の判定の範囲については[こちら(物体の運搬動作)](https://github.com/RoboCupAtHomeJP/AtHome2025/blob/main/rules/S-OPL/hm_ja.md#%E7%89%A9%E4%BD%93%E3%81%AE%E9%81%8B%E6%90%AC%E5%8B%95%E4%BD%9C)を参照してください．

<h3>4. 補足 </h3>

- 部屋名，家具名，物体名の命名規則
  - 複数の単語から構成される名前において，単語間をスペースではなくアンダースコア（`_`）で区切る命名規則を採用しています．
    <details>
      <summary>例を表示する</summary>

      - living_room
      - white_side_table 
      - white_cup
      
    </details>

- 命令文章の文法（挑戦なしの場合）
  - `Go to the (ROOM_1), grasp the (OBJECT) on the (FURNITURE_1) and put it on the (FURNITURE_2) in the (ROOM_2).`
  - 動詞は固定されておらず，以下のような類義語に置き換えられることがあります．
    - Go：Navigate, Move 等
    - grasp：pick up, get 等
    - put：locate, place, move 等

- 現在のSIGVerse採点システムでは，以下の採点項目を考慮していないため，得点するには追加処理をする必要があります．
  - 命令文章の解析
    - 与えられた命令文章を解析していることをlogに示してください．
    - Terminalにlogを出力する項目
      - `Go to the (ROOM_1), grasp the (OBJECT) on the (FURNITURE_1) and put it on the (FURNITURE_2) in the (ROOM_2).`
      - 行くべき場所 (**ROOM_1**)
      - 把持すべき物体 (**OBJECT**)
      - 物体が置かれている家具 (**FURNITURE_1**)
      - 置くべき家具 (**FURNITURE_2**)
      - 置くべき家具の部屋(**ROOM_2**)
    - 出力項目は全部で5つあり，3つ以上の出力項目が正解であれば，点数を獲得します．
  - 物体認識
    - 物体認識が成功していることを示す画像を保存してください．
      - **バウンディングボックス**
      - **物体名**
    - その画像で成功を判断し，点数を獲得します．
- 挑戦課題について，どのセッションでどの挑戦課題に挑戦するかを選ぶことができます．
  - 例：
    - 1セッション目：「二つ目のmapで指定された部屋へ移動」と「ランダムな位置にいる人に手渡し」に挑戦
    - 2セッション目：「透明物体の認識」のみに挑戦
    - 3セッション目：挑戦なし
> [!CAUTION]
> ペナルティとして，競技当日の無断欠席は-500点，運営に事前連絡した場合の欠席は-100点が科されます．

### その他
- 競技中にはWiFiの使用が可能です．命令解析においては，LLMのAPIの使用も許可されています．

[トップに戻る](#handyman)
