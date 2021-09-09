# Yz-VideoEffect
## はじめに
Yz-Filerの画像効果を動画に対して行うツールです
速度改善のために、OpenCVに変更してるので、処理結果が変わってると思います

## インストール・設定
- レジストリは使用してません。任意のディレクトリに解凍して下さい。
- アンインストールはディレクトリごと削除して下さい。

## 画像効果
 | 0:Edge<br>　　　　　　(エッジ)　　　　　　| 1:binarization<br>(2値化) | 2:Ternarization<br>(3値化/漫画風) |
:----: | :----: | :----: 
![](./Edge.jpg) | ![](./binarization.jpg) | ![](./Ternarization.jpg) 

| 3:Watercolor<br>(水彩画風) | 4:Blackboard<br>(黒板アート風) | 5:sketch<br>　　　　(スケッチ風)　　　　|
 :----: | :----: | :----: 
![](./Watercolor.jpg) | ![](./Blackboard.jpg) | ![](./sketch.jpg) 

## オプション
| ショート形式<br>(short) | ロング形式<br>(long) | 必須<br>(Required) | モード<br>(effect mode) | 説明<br>(description) |
:--- | :--- | :---: | :---: | :--- 
-m | --effect_mode | true | all | 画像効果の種類を数字で指定<br>Effect mode<br> 0 : Edge<br> 1 : binarization<br> 2 : Ternarization<br> 3 : Watercolor<br> 4 : Blackboard<br> 5 : sketch
-i | --input | true | all | 動画のフルパス<br>Full path of video file
-s | --maxsize | - | all | 出力動画の最大サイズ<br>Maximum size<br> 0 : SD (720x480)(Default)<br> 1 : HD (1280x720)<br> 2 : FHD (1920x1080)
-b | --background | - | all | 背景画像のフルパス<br>Full path of background image file
-w | --video_width | - | all | ビデオの最大幅(縮小用)<br>Video width
-h | --video_height | - | all | ビデオの最大高(縮小用)<br>Video height
-x | --left | - | all | 背景画像上のビデオ左端(はみだせない)<br>Left
-y | --top | - | all | 背景画像上のビデオ上端(はみだせない)<br>Top
-t | --threshold | - | Binarization | 2値化の閾値<br>threshold(0-255) (Default:128)
 |  |  |  | Watercolor | 水彩画風の適用度(%)<br>strength(0-100) (Default:70%)
 |  |  |  | Blackboard | 黒板アート風のノイズの閾値<br>noise threshold(0-255) (Default:8)
-u | --edge_th1 | - | Edge<br>binarization | エッジをつなげる設定値(小さい程繋がる)<br>Edge threshold1 (Default:300)
-v | --edge_th2 | - | Edge<br>binarization | エッジ検出の設定値(小さい程検出する)<br>Edge threshold2 (Default:1000)
-o | --ternarization_th1 | - | Ternarization | 3値化の下限閾値(白くなる)<br>threshold1(0-255) (Default:85)
-p | --ternarization_th2 | - | Ternarization | 3値化の上限閾値(黒くなる)<br>下限との間がグレー<br>threshold2(0-255) (Default:170)
-l | --luminance_mode | - | all | 輝度のアルゴリズム<br>0 : 最小/最大を0/255にし、平坦化<br>1 : 上下2%をカットし上と同じ<br>2 : OpenCvのEqualizeHist<br>Luminance mode (0-2)
-g | --sketch_gamma | - | Sketch | スケッチ風のガンマ値(小さい程濃くなる)<br>gamma value (Default:0.3)
-n | --sketch_noise | - | Sketch | スケッチ風の時ノイズ(鉛筆の線)を更新するか<br>Updates the noise image frame by frame (Default:false)
-z | --stdout | - | all | 標準出力に出力するか<br>Output to standard output (Default:false)


