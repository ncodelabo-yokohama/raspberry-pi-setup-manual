# Raspberry Pi セットアップマニュアル

## 目次
1. [環境](#環境)
2. [microSDのセットアップ](#microsdのセットアップ)

## 環境
- Raspberry Pi Imager v1.8.5
- Raspberry Pi 4B(8GB)
- Ubuntu OS 22.04 LTS Server
- Tailscale

## microSDのセットアップ

### 準備
1. [Raspberry Piの公式サイト](https://www.raspberrypi.com/software/)から、`Raspberry Pi Imager`をダウンロード
2. ダウンロードしたインストーラーを実行し、インストール
3. microSDカードをPCにセット

### OSの選択
1. `Raspberry Pi Imager`を起動
![起動時の画面](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/001.png)
2. `デバイスを選択`から、自身のRaspberry Piのモデルを選択
   - 例: 「Raspberry Pi 4」
3. `OSを選択` から以下の順で選択:
   - `Other general-purpose OS` > `Ubuntu` > `Ubuntu Server 22.04.5 LTS (64-bit)`
4. `ストレージを選択`からセットしたmicroSDカードを選択

### カスタマイズ設定
1. `次へ`をクリックし、表示される`Use OS customization?`ダイアログで「設定を編集する」を選択
2. 基本設定：
   - `ホスト名`：任意の名前を設定
   - `Wi-Fi設定`（無線LANを使用する場合のみ）：
     - `Wi-Fiを設定する`にチェック
     - `SSID`と`パスワード`を入力
     - `Wi-Fiを使う国`を`JP`に変更
   - `ロケール設定`：
     - `タイムゾーン`：`Asia/Tokyo`
     - `キーボードレイアウト`：`jp`
3. `サービス`タブ:
   - `SSHを有効化する`にチェック
   - `パスワード認証を使う`を選択
4. 設定を保存
![設定例(一般タブ)](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/002.png)
![設定例(サービスタブ)](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/003.png)

### 書き込みの実行
1. `Use OS customization?`のダイアログで`はい`を選択
2. 警告ダイアログが表示されたら`はい`を選択
3. インストール完了まで約15分待機
4. 完了したら、microSDをPCから取り出し、Raspberry Piにセット