# 初めての方へ：何から始めればよいか

### まずは環境構築をしましょう
- [競技における事前セットアップ](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/setup.md)を参考に環境構築をしましょう．

### Teleopを用いてロボットを操作してみよう
- 得点獲得までに踏まなければならないステップが非常に多いため，handyman-rosパッケージにある[teleop_key.launch.py](https://github.com/TeamSOBITS/handyman-ros/blob/humble-devel/handyman-ros/launch/teleop_key.launch.py)で実行してみるなどしてイメージを掴んでみてください．

### ルールを確認しましょう
- [Handyman Rules for RCSO2025](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/rules_ja.md)にあるルールを読みましょう．

### 練習問題で練習しましょう
- 運営側が練習するための問題（[Google Drive](https://drive.google.com/drive/folders/1SWfb7NuYQMf4eMNAOcCy9lm2-Bk9tO0o?usp=sharing)）を作成しましたので，ぜひご活用ください．
  - Window側のPCにダウンロードしてください．ダウンロードしたファイルをパス`handyman-unity-master\handyman-unity-master\SIGVerseConfig\Handyman`に移動して，以下のファイル名に変換してください．
    - EnvironmentInfo01.json
    - AvatarMotions01.dat
  - 切り替えの練習をしたい場合，`EnvironmentInfo02.json`と`AvatarMotions02.dat`も併せて用意してください．
- 何の練習問題が含まれているかは，[RCSOinSummer2025_練習問題一覧](https://docs.google.com/spreadsheets/d/1sA8g8CZICu-WVadZzMxreUlOkIxEBMaMXxDLx5-GPAQ/edit?usp=sharing)にてご確認いただけます．
- `handyman-unity-master/SIGVerseConfig/Handyman`の中にあるconfigファイルの内容を修正することで，セッションの制限時間を変更することができます．練習に活用してください．

### 物体認識には何を使えばいい？
- 初心者の方にとって最も始めやすいのは，[YOLO（You Only Look Once）](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Redmon_You_Only_Look_CVPR_2016_paper.pdf) 系の手法ではないかと思います．
- YOLOは，リアルタイムで高速かつ高精度な物体検出が可能なモデルで，多くのプロジェクトで広く利用されています．
- 以下のリポジトリを利用することで，YOLOのデータセット作成，学習，推論をすることができます．
  - [yolo_dataset](https://github.com/TeamSOBITS/yolo_dataset/tree/develop)
  - [yolo_ros](https://github.com/TeamSOBITS/yolo_ros)
