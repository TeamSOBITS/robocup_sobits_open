> [!WARNING]
> Layoutは今後更新される可能性があります。

## **Handyman**

RoboCup Simulation Leagueで行われた競技の1つであるHandymanタスクについて説明していきます．

## **目次**

1. [競技内容(Handyman)](#1-競技内容handyman)
2. [競技手順(Handyman)](#2-競技手順handyman)
3. [競技の点数表(Handyman)](#3-競技の点数表handyman)


### 1. 競技内容(Handyman)

Handymanタスクでは，与えられた命令文を解析し、ロボットが自律的に移動し，注文された物を掴み，別のところまで運ぶことを行います．
今回は競技を簡単にするために，家具や把持物体などの位置を含めたファイルを共有します．
環境や把持物体はランダムに決定されます．

- 本競技は，1人3セッション挑戦することができ，3セッションの総合得点で順位を決めます．
- 実機と違い、タスクのスキップ等はできません．
- 競技開始後，セッション中に動作しなくなった場合はそのセッションをスキップし、次セッションから再起動できます
- [環境レイアウトと把持・配置地点のリスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/layout_and_location_list.md)、や[把持物体リスト](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/object_list.md)は，事前に公開しており、ご確認ください
- 制限時間は各セッション600秒です．

### 2. 競技手順(Handyman)

競技の手順は以下の通りになります．

1. モデレータの指示を聞く
2. 指定された部屋へ移動する
3. 指定された物体を探索する
4. その物体を把持する
5. 指示された置き位置へ物体を運ぶ
6. 置き位置に物体を置く

#### 2.1. 競技手順の流れ

具体的な競技手順の流れは以下の通りになります．

1. モデレータは「Are_you_ready?」をロボットへ送信します。そして同時に「Environment」メッセージも発信します．
2. ロボットは「I_am_ready」メッセージをモデレータに送信します．
3. モデレータはロボットに「指示」のメッセージを送ります．(例: Go to the XXXX, grasp the YYYY and bring it here.)
4. 命令理解が完了した後に，ロボットは「置き位置と掴む物体」をモデレータに送信します．
5. ロボットは指定された部屋に移動します．
6. ロボットは「Room_reached」メッセージをモデレータに送信します．
7. ロボットが物体を探します．
    - 物体が見つかった場合に，ロボットは「Object_recognized」メッセージをモデレータに送信します．
    - 物体が見つからなかった場合，ロボットはモデレータに「Does_not_exist」メッセージを送信する必要があります．
        - 指示が正しい場合，スコアが追加され，モデレータはロボットに，「Corrected_instruction」メッセージを送信します．その後，ロボットは新しいオブジェクトを探す必要があります．
8. ロボットは物体を把持します．
9. ロボットは「Object_grasped」メッセージをモデレータに送信します.
10. ロボットは置き位置に物体を置きます．
11. ロボットは「Task_finished」メッセージをモデレータに送信します.
- タスクが終了した場合（成功または失敗）: モデレータは「Task_succeeded」 (タスク成功) または「Task_failed」 (タスク失敗) メッセージをロボットに送信します．すべてのタスクが終了した際に，モデレータはロボットに「Mission_complete」メッセージを送信します．
- 制限時間が終了した場合: モデレータは，タスクが失敗したことを示す「Task_failed」メッセージをロボットに送信します．
- ロボットは、タスクを達成できない場合に「Give_up」メッセージを送信できます．その場合，タスクは中止され「Task_failed」メッセージが送信され，次のセッションに進みます．

<h3>3. 競技の点数表（Handyman）</h3>
<p>※ 狭義の点数は変更の可能性があります。ご了承ください。</p>

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
      <td>セッション切り替え</td>
      <td>0点</td>
      <td>―</td>
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
      <td>家具名が与えられない状況で物体の認識</td>
      <td>40点</td>
    </tr>
    <tr>
      <td>指定された物体の把持</td>
      <td>30点</td>
      <td>透明物体</td>
      <td>50点</td>
    </tr>
    <tr>
      <td>物体を指定場所へ運搬</td>
      <td>10点</td>
      <td>ランダムな位置にいる人に手渡し※2</td>
      <td>10点</td>
    </tr>
    <tr>
      <td>物体を指定場所に配置※3</td>
      <td>20点</td>
      <td>命令文によって配置場所が非固定</td>
      <td>40点</td>
    </tr>
    <tr>
      <td><strong>合計</strong></td>
      <td><strong>100点</strong></td>
      <td></td>
      <td><strong>200点</strong></td>
    </tr>
  </tbody>
</table>

- ※1：3セッションのうち，1セッションのみで2つ目のマップが使用されます．挑戦課題のレイアウトについては[Layout2019HM02](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/layout_and_location_list)をご参照ください．
- ※2：人がいる部屋は，命令文の中で明示されます．
- ※3：物体の固定の配置場所について
  - LayoutAの場合は、living_roomのwhite_side_table
  - LayoutBの場合は、bedroomのiron_bed

[トップに戻る](#handyman)
