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
:--- | :--- | :---: | :---: | :--- 
-m | --effect_mode | true | all |Effect mode<br> 0 : Edge<br> 1 : binarization<br> 2 : Ternarization<br> 3 : Watercolor<br> 4 : Blackboard<br> 5 : sketch
-i | --input | true | all | Full path of video file
-s | --maxsize | - | all | Maximum size<br> 0 : SD (720x480)(Default)<br> 1 : HD (1280x720)<br> 2 : FHD (1920x1080)
-b | --background | - | all | Full path of background image file
-w | --video_width | - | all | Video width
-h | --video_height | - | all | Video height
-x | --left | - | all | Left
-y | --top | - | all | Top
-t | --threshold | - | Binarization | threshold(0-255) (Default:128)
 |  |  |  | Watercolor | strength(0-100) (Default:70%)
 |  |  |  | Blackboard | noise threshold(0-255) (Default:8)
-u | --edge_th1 | - | Edge<br>binarization | Edge threshold1 (Default:300)
-v | --edge_th2 | - | Edge<br>binarization | Edge threshold2 (Default:1000)
-o | --ternarization_th1 | - | Ternarization | threshold1(0-255) (Default:85)
-p | --ternarization_th2 | - | Ternarization | threshold2(0-255) (Default:170)
-l | --luminance_mode | - | all | Luminance mode (0-2)
-g | --sketch_gamma | - | Sketch | gamma value (Default:0.3)
-n | --sketch_noise | - | Sketch | Updates the noise image frame by frame (Default:false)
-z | --stdout | - | all | Output to standard output (Default:false)


