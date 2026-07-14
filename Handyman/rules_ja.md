> [!WARNING]
> Rulesは今後更新される可能性があります．

## **Handyman Rules for RCSO2026**

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
- [環境レイアウトと把持・配置地点のリスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2026_srl/Handyman/layout_and_location_list.md)，や[把持物体リスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2026_srl/Handyman/object_list.md)は，事前に公開しているので，ご確認ください．
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
      <td>セッション切り替え※3※4</td>
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
      <td>抽象的な要求への対応※2</td>
      <td>最大50点</td>
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
      <td><strong>150点</strong></td>
    </tr>
    <tr>
      <td><strong>総合最大点</strong></td>
      <td colspan="3"><strong>250点</strong></td>
    </tr>
  </tbody>
</table>

- ※1：3セッションのうち，1セッションのみで2つ目のマップが使用されます．挑戦課題のレイアウトについては[Layout2019HM02](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2026_srl/Handyman/layout_and_location_list.md#layout2019hm02-%E6%8C%91%E6%88%A6%E8%AA%B2%E9%A1%8C)をご参照ください．
- ※2：命令文に物体名は明示されません．命令文では探索する部屋，または家具・場所が毎回指定され，ロボットはカテゴリ名，意味的な説明，機能，属性，状態などに合う物体を選択します．Level 2（カテゴリ名が命令文に含まれる場合）は30点，Level 3（機能・属性・状態などで表現される場合）は50点とします．正解となる対象物体は，公開されている把持物体リストと運営内部の審判基準に基づいて判定します．カテゴリ名は公開しますが，カテゴリと物体の完全な対応表は公開しません．この挑戦課題は，物体名の直接的な文字列解析を超えた意味理解を評価します．
- ※3：セッション切り替えはセッション2と3のみで挑戦できます.
- ※4：セッション切り替え後に点数が入らなかった場合，SIGVerse側で「I_am_ready」が受信できているか確認できた場合に，点数が入ります．

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
  - 部屋名，家具名，配置先は，[環境レイアウトと把持・配置地点のリスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2026_srl/Handyman/layout_and_location_list.md)に従います．
  - 動詞は固定されておらず，以下のような類義語に置き換えられることがあります．
    - Go：Navigate, Move 等
    - grasp：pick up, get 等
    - put：place 等

- 抽象的な要求への対応（挑戦課題）
  - 命令文では，対象物体の名前が直接与えられません．
  - 探索する部屋，家具・場所，配置先は命令文の中で毎回指定されます．
  - ロボットは，カテゴリ名，意味的な説明，機能，属性，状態などに合う物体を判断して選択する必要があります．
  - 抽象的な要求への対応では，以下のカテゴリ名を使用する場合があります．
    - Drink
    - Condiment
    - Container
    - Toy
    - Household
    - Game
  - カテゴリ名を用いる場合は，`a drink`や`a toy`のように命令文にカテゴリ名が含まれます．
  - 機能・属性・状態を用いる場合は，カテゴリ名を命令文に含めません．
    <details>
      <summary>例を表示する</summary>

      - Go to the kitchen, grasp a drink on the dining_table and put it on the round_low_table in the living_room.
      - Go to the lobby, grasp a toy on the corner_sofa and put it on the wooden_bed in the bedroom.
      - Go to the lobby, grasp something used for cleaning on the wooden_shelf and put it on the wagon in the lobby.
      - Go to the kitchen, grasp the bottle that still has drink inside on the dining_table and put it on the square_low_table in the living_room.

    </details>
  - 正解となる対象物体は，公開されている把持物体リストと運営内部の審判基準に基づいて判定します．
  - カテゴリ名は公開しますが，公平性のために必要な場合を除き，カテゴリと物体の完全な対応表は公開しません．
  - 本挑戦課題では，物体名の直接的な文字列解析を超えた意味理解を評価します．

- 問題の難易度
  - Level 1：物体名が命令文に直接含まれる通常の問題です．抽象的な要求への対応の点数は入りません．
  - Level 2：カテゴリ名が命令文に含まれる問題です．抽象的な要求への対応として30点の対象になります．
  - Level 3：カテゴリ名を含めず，機能・属性・状態などで物体を表現する問題です．抽象的な要求への対応として50点の対象になります．
  - Level 3の問題は，透明物体や二つ目のmapなど，他の挑戦課題と組み合わせて出題される場合があります．

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
  - 抽象的な要求への対応
    - Level 2とLevel 3では，SIGVerse上の自動採点は運営が設定した想定正解物体名に基づいて行われます．
    - カテゴリ名や機能表現に対して適切な物体を選択できているかは，ロボットのlogと物体認識画像をもとに審判が確認します．
- 挑戦課題について，どのセッションでどの挑戦課題に挑戦するかを選ぶことができます．
  - 例：
    - 1セッション目：「二つ目のmapで指定された部屋へ移動」と「抽象的な要求への対応」に挑戦
    - 2セッション目：「透明物体の認識」のみに挑戦
    - 3セッション目：挑戦なし
> [!CAUTION]
> ペナルティとして，競技当日の無断欠席は-500点，運営に事前連絡した場合の欠席は-100点が科されます．

### その他
- 競技中にはWiFiの使用が可能です．命令解析においては，LLMのAPIの使用も許可されています．

[トップに戻る](#handyman)
