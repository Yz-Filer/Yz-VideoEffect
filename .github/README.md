# Yz-VideoEffect / Yz-ImageEffect
## はじめに
Yz-Filerの画像効果をパラメータを指定して静止画 / 動画に対してより高速に行うために作成しました。  
対応している画像効果は、エッジ、2値化、3値化、水彩画風、黒板アート風、スケッチ風の6つです。  
高価なソフトウェアを使わずに手軽に画像効果をつけられるソフトはそんなにないのではないかと思います。  
速度改善のためにOpenCVに変更してるので、Yz-Filerとは処理結果が変わっています。

## インストール・設定
- 動作環境は、Windows10 64bit .NET Framework 4.6.1以上となります。
- レジストリは使用してません。
- 任意のディレクトリに、「Yz-VideoEffect_1.0.zip」を解凍してください。
- 解凍時に作成されたディレクトリに、「OpenCvSharpExtern.zip」を解凍して下さい。
- ウィルスチェックは実施済みです。
- アンインストールはディレクトリごと削除して下さい。
- 動画の保存にはffmpegが必要となります。
- Yz-VideoEffectは動画用でコマンドラインツールとなります。
- Yz-ImageEffectは静止画用でGUIツールとなります。  
  コマンドライン引数として静止画のフルパスが渡せるため、設定すればYz-Filerのマクロからも起動できます。

## 画像効果
 | 0:Edge<br>　　　　　　(エッジ)　　　　　　| 1:binarization<br>(2値化) | 2:Ternarization<br>(3値化/漫画風) |
:----: | :----: | :----: 
![](./Edge.jpg) | ![](./binarization.jpg) | ![](./Ternarization.jpg) 

| 3:Watercolor<br>(水彩画風) | 4:Blackboard<br>(黒板アート風) | 5:Sketch<br>　　　　(スケッチ風)　　　　|
 :----: | :----: | :----: 
![](./Watercolor.jpg) | ![](./Blackboard.jpg) | ![](./sketch.jpg) 

## 向いてる/向いてない素材
- 向いてると思う素材
  - 人や動物、風景など
  - 直線が多い素材
    - ビル、街並み、店の外観など
    - 雑然としたオフィス、家具の多い部屋など
    - 乗り物、ロボットなど機械的な物
    - 文房具や工具など
  - 2次元素材  
    絵やイラスト、アニメ、ゲームなど2次元素材も向いてる場合があります。

- 向いてないと思う素材  
  事前に加工することで問題がなくなる場合もあります。  
  - 明るすぎる物や全体的に白っぽい素材
  - 暗すぎる物や全体的に黒っぽい素材
  - 写ってる物が少なく、背景が単色の素材
  - ノイズが多い素材（暗い素材は目立たないけどノイズが多い場合があります）
  - コントラストが高すぎるまたは低すぎる素材

## 動画用オプション（静止画の同様オプションは同義）
| ショート形式<br>(short) | ロング形式<br>(long) | 必須<br>(Required) | モード<br>(effect mode) | 説明<br>(description) |
:--- | :--- | :---: | :---: | :--- 
-m | --effect_mode | true | all | 画像効果の種類を数字で指定<br>Effect mode<br> 0 : Edge<br> 1 : binarization<br> 2 : Ternarization<br> 3 : Watercolor<br> 4 : Blackboard<br> 5 : Sketch
-i | --input | true | all | 動画のフルパス<br>Full path of video file
-s | --maxsize | - | all | 出力動画の最大サイズ<br>Maximum size<br> 0 : SD (720x480)(Default)<br> 1 : HD (1280x720)<br> 2 : FHD (1920x1080)
-b | --background | - | all | 背景画像のフルパス<br>Full path of background image file
-w | --video_width | - | all | ビデオの最大幅(縮小用)<br>Video width
-h | --video_height | - | all | ビデオの最大高(縮小用)<br>Video height
-x | --left | - | all | 背景画像上のビデオ左端<br>(はみだせない)<br>Left
-y | --top | - | all | 背景画像上のビデオ上端<br>(はみだせない)<br>Top
-t | --threshold | - | Binarization | 2値化の閾値<br>threshold(0-255) (Default:128)
 |  |  |  | Watercolor | 水彩画風の適用度(%)<br>strength(0-100) (Default:70%)
 |  |  |  | Blackboard | 黒板アート風のノイズの閾値<br>noise threshold(0-255) (Default:8)
-u | --edge_th1 | - | Edge<br>binarization | エッジをつなげる設定値<br>(小さい程繋がる)<br>Edge threshold1 (Default:300)
-v | --edge_th2 | - | Edge<br>binarization | エッジ検出の設定値<br>(小さい程検出する)<br>Edge threshold2 (Default:1000)
-o | --ternarization_th1 | - | Ternarization | 3値化の下限閾値(黒くなる範囲)<br>threshold1(0-255) (Default:85)
-p | --ternarization_th2 | - | Ternarization | 3値化の上限閾値(白くなる範囲)<br>下限との間がグレー<br>threshold2(0-255) (Default:170)
-l | --luminance_mode | - | all | 輝度のアルゴリズム<br>0 : 最小/最大を0/255にし、平坦化<br>1 : 上下2%をカットし上と同じ<br>2 : OpenCVのEqualizeHist<br>Luminance mode (0-2)
-g | --sketch_gamma | - | Sketch | スケッチ風のガンマ値<br>(小さい程濃くなる)<br>gamma value (Default:0.3)
-n | --sketch_noise | - | Sketch | スケッチ風の時ノイズを更新するか<br>Updates the noise image<br> frame by frame (Default:false)
-z | --stdout | - | all | 標準出力に出力するか<br>Output to standard output<br>(Default:false)

## 実行方法（動画）
- 動画をファイルから取得する場合  
  オプションを複数指定する場合は、以下のような内容のbatファイルを作成した方が便利だと思います。  
  (batは「^」により、コマンドの途中で改行可能です)  
  (必須項目以外は指定しなくてもデフォルト設定で動作します)
  ```
  Yz-VideoEffect.exe ^
  --effect_mode 1 ^
  --input "hoge.mp4" ^
  --maxsize 0 ^
  --threshold 128 ^
  --edge_th1 300 ^
  --edge_th2 1000 ^
  --luminance_mode 1 ^
  --stdout false
  ```
  上記で作成したbatをDOS窓で実行すると、Windowが起動され動画が表示されます。  

- 動画を標準入力から取得する場合  
  入力ファイル名に「PIPE:WxH,FPS」(W, H, FPSは数値)を指定した場合、標準入力から動画を取得します。  
  以下は、事前にインターレース解除をffmpegで実施する例となります。
  ```
  ffmpeg -i "hoge.mp4" -an ^
  -vf yadif=0:-1:1 ^
  -vcodec rawvideo -f image2pipe -pix_fmt bgr24 - ^
   | Yz-VideoEffect.exe ^
  --effect_mode 5 ^
  --input "PIPE:960x540,29.97" ^
  --stdout false
  ```
  こちらも同じくDOS窓で実行して下さい。  

このモード(--stdout false)では、動画を処理する都度、更新されるため再生速度は維持されません。  
実行すると、DOS窓に以下のような内容が表示されます。
```
--------------------
[Input video]
fps:29.97
FrameWidth:960
FrameHeight:540

[Output video]
fps:29.97
FrameWidth:720
FrameHeight:405

[Back image]
Width:720
Height:405
--------------------
```
「fps」と、「Back image」の「Width」「Height」が保存時に必要となります。  
（実行を中断したい場合は、DOS窓をクリックしてCtr+Cキーを押して中断して下さい）

## 保存方法（動画）
「実行方法」で作成したbatを以下のように変更します
```
Yz-VideoEffect.exe ^
--effect_mode 1 ^
--input "hoge.mp4" ^
--maxsize 0 ^
--threshold 128 ^
--edge_th1 300 ^
--edge_th2 1000 ^
--luminance_mode 1 ^
--stdout true ^
 | ffmpeg -y -f rawvideo -pixel_format bgr24 -video_size 720x405 -framerate 29.97 -i - -an -vcodec libx264 -pix_fmt yuv420p "out.mp4"
```
最後の2行を変更してます。「--stdout」を「true」に変更し、ffmpegにデータを渡します。  
「video_size」と「framerate」に「実行方法」で確認した「Width」「Height」と「fps」を指定して下さい。  
尚、ffmpegの保存用オプションは、ffmpegの解説HPなどを参照してください。  

## 実行方法（静止画）
GUIツールなので、Yz-ImageEffect.exeをそのまま起動するか、コマンドライン引数として静止画のフルパスを指定して下さい。  
オプションの意味は動画と同じなので、動画のオプション説明を参照してください。  
ただし、背景画像の指定はできません。  
保存形式は、OpenCVが対応している形式(jpg, png, bmpなど)であれば拡張子で自動判定されると思います。  
画像効果の効きが悪い時、  
・解像度が高いと写真っぽく見えやすいので、画像の幅を500～800くらいに落としてみて下さい。  
・事前に、コントラスト・輝度・彩度の調整やノイズ除去を実施してみて下さい。  
幅や高さを変更した時、  
・アスペクト比を維持するので幅か高さを変更すれば、もう一方は自動的に計算されます。  
　(縮小率が高い方優先)  
・ 画面に表示されてる画像は拡大/縮小されませんが解像度が変化しており、保存時には  
　指定したサイズで保存されます。  
 
 
尚、静止画で背景画像を指定したい場合、Yz-VideoEffectを使うことが出来ます。  
```
ffmpeg -i "hoge.jpg" -an -vcodec rawvideo -f image2pipe -pix_fmt bgr24 - ^
 | Yz-VideoEffect.exe ^
--effect_mode 5 ^
--input "PIPE:960x540,1" ^
--background "background.jpg" ^
--maxsize 1 ^
--video_width 1000 ^
--stdout true ^
 | ffmpeg -y -f rawvideo -pixel_format bgr24 -video_size 1280x720 -i - -an -vframes 1 -f image2 "out.jpg"
```

## 制限など
- 動画出力には音声は含まれません。
- 入力ファイルは、事前にインターレース解除をしておいてください。
- 自分で撮影した素材の場合、事前にノイズ除去や輝度・彩度などの補正もやっておいたほうが良いかもしれません。
- やっつけツールですんで、エラーハンドリングはやってません。

## ライブラリ類およびライセンス
- 本ソフトウェア（Yz-VideoEffect）  
  Copyright (c) 2021 Yz  
  Released under the MIT license  
  https://opensource.org/licenses/mit-license.php  
  作者または著作権者は、本ソフトウェアに起因して被った直接的または間接的損害については一切責任を負わず、また保証/補償も出来ません  
  以下のライブラリ類については、それぞれのライセンスに従ってください  
  Please accept the license agreement for each library
  
- OpenCVSharp  
  Apacheライセンス バージョン2.0  
  https://github.com/shimat/opencvsharp/blob/master/LICENSE

- OpenCV  
  Apacheライセンス バージョン2.0  
  https://github.com/opencv/opencv/blob/master/LICENSE

- Fred's ImageMagick Scripts  
  画像効果のアルゴリズムを参考にさせて貰ってます。  
  非商用目的のみ無料で利用可  
  ```
  My scripts are available free of charge for non-commercial (non-profit) use, ONLY.
  ```
  http://www.fmwconcepts.com/imagemagick/index.php

## 処理結果イメージ
「ぱくたそ（www.pakutaso.com）
」さんが加工・公開OKだということなので使わせてもらいました。  
（下記画像の取り扱いについては、ばくたそさんの規約を守ってください）  
| Watercolor (水彩画風) | Sketch (スケッチ風) |
:----: | :----: 
![](./sample/wc_ANJI.jpg) | ![](./sample/sk_ANJI.jpg) 
![](./sample/wc_anjyu.jpg) | ![](./sample/sk_anjyu.jpg) 
![](./sample/wc_aomidori.jpg) | ![](./sample/sk_aomidori.jpg) 
![](./sample/wc_baby.jpg) | ![](./sample/sk_baby.jpg) 
![](./sample/wc_J_nishinippori.jpg) | ![](./sample/sk_J_nishinippori.jpg) 
![](./sample/wc_kanazawa.jpg) | ![](./sample/sk_kanazawa.jpg) 
![](./sample/wc_nichinan.jpg) | ![](./sample/sk_nichinan.jpg) 
![](./sample/wc_nonnu.jpg) | ![](./sample/sk_nonnu.jpg) 
![](./sample/wc_OY.jpg) | ![](./sample/sk_OY.jpg) 
![](./sample/wc_shikun.jpg) | ![](./sample/sk_shikun.jpg) 
