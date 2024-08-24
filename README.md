# tinyjoypad キット

tinyjoypad キットは、attiny85を使ったゲーム機を作成するためのキットです。<br>
tinyjoypadプロジェクトは
[こちら](https://www.tinyjoypad.com/tinyjoypad_attiny85) 

<img src="https://github.com/user-attachments/assets/5a786e2c-6ccb-4db3-8b82-33c2ea627990" width="50%">

## 内容物
<img src="https://github.com/user-attachments/assets/f296b0f7-974a-4716-b855-78c361ee3a29" width="50%">

- 基板 x 1
- LED x 1
- ピンヘッダー（2×3） x 1
- スライドスイッチ x 1
- attiny85 x 1
- 丸ピンICソケット (8P) x 1
- 抵抗（10kΩ） x 2
- 抵抗（22kΩ） x 2
- 抵抗（33kΩ） x 2
- 抵抗（91kΩ） x 2
- タクトスイッチ x 5
- スイッチキャップ x 5
- ブザー x 1
- ボタン電池ホルダー x 1
- 0.96インチ有機ELディスプレイ(OLED)  x 1
- USBasp AVRライタ x 1

## 自分で用意する必要があるもの
最近は100均などでも手に入りますね。
- はんだごて、はんだ
- マスキングテープ
- ニッパー
- ボタン電池（CR2032）

## 作成手順
1. 抵抗を基板に書かれた場所に配置します。間違えないようにしましょう。向きは関係ありません。<br>
はんだで接続できたら、余った足はニッパーでカットしてOKです。
どの抵抗かわからなくなっても落ち着いてカラーコードを確認すれば大丈夫です。<br>

![IMG_1439](https://github.com/user-attachments/assets/a12f0c49-75a0-4cce-a289-5fa2058f2b82)<br>
 10kΩ：茶赤黒黒茶<br><br>
 ![IMG_1441](https://github.com/user-attachments/assets/3b55701e-8d33-40bd-a95e-8af8d5628162)
 22kΩ：赤赤黒赤茶<br><br>
 ![IMG_1442](https://github.com/user-attachments/assets/d0c186a5-31d9-4dfb-bc24-f39ccee16741)
 33kΩ：橙橙黒赤茶<br><br>
 ![IMG_1440](https://github.com/user-attachments/assets/90feaaa1-3b6f-4cac-88cf-e76c26dd8cbc)
 91kΩ：茶赤黒茶白<br>

2. OLEDを取り付けます。斜めにならないようにマスキングテープなどで固定してからはんだ付けしましょう。<br><br>
3. 電源スイッチを下に向けて取り付けます。ぐらぐらしますので、マスキングテープなどで仮固定してからはんだ付けしましょう。<br><br>
4. タクトスイッチを取り付けます。向きは関係ありません。スイッチキャップも付けましょう。あまり強く押さなくても取り付けられます。<br><br>
5. LEDを取り付けます。足の短い方（カノード）をGNDの方にして取り付けてください。余った足はニッパーでカットしてOKです。<br><br>
6. ピンヘッダ、ICソケットを取り付けます。ICソケットにはattiny85を取り付けます。attiny85は左側にくぼみがくるように取り付けてください。<br><br>
7. ブザーも向きがあります。＋と書いてる方を間違えずに取り付けてください。これで表面は完成です。<br><br>
8. 裏を向けてボタン電池ホルダーを取り付けます。今までと違い表面実装部品なので、先に基板にはんだを少し盛ってから、上から温めて接続するとうまくいきます。<br><br>

あとは電池を＋面が表になるように接続して電源をONにすればゲームが起動するはずです！おめでとう！
起動しない場合ははんだのミス（隣と接続されてしまっている箇所が無いかなど）、attiny85の向き、取付忘れなどないか確認してください。

## プログラムのインストール手順
初期状態でスペースインベーダーをインストールしていますが、tinyjoypadプロジェクトでは他にも面白いゲームが公開されています。
現状(2024年7月時点）でうまくいったインストール手順を紹介します。

1. [Zadig](https://zadig.akeo.ie/)にアクセスして、Zadigソフトをインストールします。
2. キットについているUSBaspをPCと接続します。
3. Zadigを起動し、USBaspを選択してlibusbkを選択してインストールします。
4. [ArduinoIDE](https://www.arduino.cc/en/software)をインストールします。
5. 基本設定ー＞追加のボードマネージャのURLに次のURLを追加します。https://descartes.net/package_drazzy.com_index.json
6. ツールー＞ボードー＞ボードマネージャの検索欄にattinyと入力してATTinyCore by Spence Kondeのバージョン1.3.2を選択してインストールします。
8. [SSD1306ライブラリ](https://github.com/Defragster/ssd1306xled)をダウンロードし、スケッチー＞ライブラリをインクルードー＞.ZIP形式のライブラリをインストールへと進み、ダウンロードしたzipファイルを選択してインストールを行います。
9. [ゲームデータ](https://github.com/cheungbx/gametiny)をダウンロード、解凍し、好きなゲームの.inoファイルを起動します。
10. ツールー＞ボードー＞ATTinyCoreー＞Attiny25/45/85を選択します。
11. チップはATtiny85、クロックは8MHz(internal)、そして書込装置はUSBaspを選択します。
12. スケッチー＞書き込み装置を使って書き込むを選択します。
13. プログラムが書き込まれます。

詳細な手順やサンプルコードについては、[tinyjoypad](https://www.tinyjoypad.com/tinyjoypad_attiny85)も参照してください。

## 自分で基板を発注してみる
gbrフォルダにあるファイルをJLCPCBなどの基板発注サービスなどに依頼すれば自分で発注することができます。
また、基板データを改造・修正する場合のライセンスはGPLv3です。

## 3Dプリンターでケースを作る
3dmodelフォルダにあるファイルをそのまま3Dプリンターなどで印刷すればケースを付けることができます。M2×15のビスが4本必要です。

<img src="https://github.com/user-attachments/assets/056c5c07-2afa-4e9e-8e62-095d6264505f" width="50%">
