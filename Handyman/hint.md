# 初めての方へ：何から始めればよいか

### まずは環境構築をしましょう
[競技における事前セットアップ](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/setup.md)を参考に環境構築をしましょう．

### Teleopを用いてロボットを操作してみよう
- 得点獲得までに踏まなければならないステップが非常に多いため，handyman-rosパッケージにある[teleop_key.launch.py](https://github.com/TeamSOBITS/handyman-ros/blob/humble-devel/handyman-ros/launch/teleop_key.launch.py)で実行してみるなどしてイメージを掴んでみてください．

### ルールを確認しましょう
[Handyman Rules for RCSO2025](https://github.com/TeamSOBITS/robocup_sobits_open/blob/rcso_2025_srl/Handyman/rules_ja.md)にあるルールを読みましょう．

### 物体認識には何を使えばいい？
- 初心者の方にとって最も始めやすいのは，[YOLO（You Only Look Once）](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Redmon_You_Only_Look_CVPR_2016_paper.pdf) 系の手法ではないかと思います．
- YOLOは，リアルタイムで高速かつ高精度な物体検出が可能なモデルで，多くのプロジェクトで広く利用されています．
- 以下の記事では，YOLOの学習方法について詳しく解説されていますので，ぜひ参考にしてください．
  - [How to use YOLO](https://esa-pages．io/p/sharing/19758/posts/82/148313344c3b93bac860.html)
