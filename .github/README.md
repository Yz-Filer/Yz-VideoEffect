# Yz-VideoEffect
## はじめに
Yz-Filerの画像効果を動画に対して行うツールです
速度改善のために、OpenCVに変更してるので、処理結果が変わってると思います

## インストール・設定
- レジストリは使用してません。任意のディレクトリに解凍して下さい。
- アンインストールはディレクトリごと削除して下さい。

## 画像効果
 | 0:Edge<br>　　　　　　(エッジ)　　　　　　| 1:binarization<br>(2値化) | 2:Ternarization<br>(3値化) |
:----: | :----: | :----: 
![](./Edge.jpg) | ![](./binarization.jpg) | ![](./Ternarization.jpg) 

| 3:Watercolor<br>(水彩画風) | 4:Blackboard<br>(黒板アート風) | 5:sketch<br>　　　　(スケッチ風)　　　　|
 :----: | :----: | :----: 
![](./Watercolor.jpg) | ![](./Blackboard.jpg) | ![](./sketch.jpg) 

## オプション
| ショート形式<br>(short) | ロング形式<br>(long) | 必須<br>(Required) | モード<br>(effect mode) | 説明<br>(description) |
:--- | :--- | :--- | :--- | :--- 
-m | --effect_mode | true | all |Effect mode<br> 0:Edge, 1:binarization, 2:Ternarization,<br> 3:Watercolor, 4:Blackboard, 5:sketch
