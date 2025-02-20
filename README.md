# Raspberry Pi セットアップマニュアル

## 目次
1. [環境](#環境)
2. [microSDのセットアップ](#microsdのセットアップ)

## 環境
- Raspberry Pi Imager v1.8.5
- Raspberry Pi 4B(8GB)
- Ubuntu OS 22.04 LTS Server
- Tailscale

## 1. microSDのセットアップ

### 1-1. 準備
1. [Raspberry Piの公式サイト](https://www.raspberrypi.com/software/)から、`Raspberry Pi Imager`をダウンロード
2. ダウンロードしたインストーラーを実行し、インストール
3. microSDカードをPCにセット

### 1-2. OSの選択
1. `Raspberry Pi Imager`を起動
![起動時の画面](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/001.png)
2. `デバイスを選択`から、自身のRaspberry Piのモデルを選択
   - 例: 「Raspberry Pi 4」
3. `OSを選択` から以下の順で選択:
   - `Other general-purpose OS` > `Ubuntu` > `Ubuntu Server 22.04.5 LTS (64-bit)`
4. `ストレージを選択`からセットしたmicroSDカードを選択

### 1-3. カスタマイズ設定
1. `次へ`をクリックし、表示される`Use OS customization?`ダイアログで「設定を編集する」を選択
2. 基本設定：
   - `ホスト名`：任意の名前を設定(必須)
   - OSのログイン時に使う`ユーザー名`と`パスワード`を設定(必須)
   - `Wi-Fi設定`（無線LANを使用する場合のみ）：
     - `Wi-Fiを設定する`にチェック
     - `SSID`と`パスワード`を入力
     - `Wi-Fiを使う国`を`JP`に変更
   - `ロケール設定`(必須)：
     - `タイムゾーン`：`Asia/Tokyo`
     - `キーボードレイアウト`：`jp`
3. `サービス`タブ(必須):
   - `SSHを有効化する`にチェック
   - `パスワード認証を使う`を選択
4. 設定を保存
![設定例(一般タブ)](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/002.png)
![設定例(サービスタブ)](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/003.png)

### 1-4. 書き込みの実行
1. `Use OS customization?`のダイアログで`はい`を選択
2. 警告ダイアログが表示されたら`はい`を選択
3. インストール完了まで約15分待機
4. 完了したら、microSDをPCから取り出し、Raspberry Piにセット

## 2. OSのセットアップ

### 2-1. 起動
1. Raspberry Piにmicro HDMIケーブルを接続
   - 重要: 必ず電源を入れる前にケーブルを接続してください
   - 接続が後になると、映像が表示されない場合があります

2. Raspberry Piに電源ケーブルを接続
   - 本体のLEDが点滅を始めたら、正常に通電しています
   - しばらく待つと、起動プロセスが始まるのでしばらく待ちます

3. 起動が完了すると、ログイン画面が表示されます
   - 先ほど設定した`ユーザー名`を入力し、Enter
   - 続いて、`パスワード`の入力を求められるので入力して、Enter
   - **※セキュリティ上の理由から、パスワードを入力しても画面上には表示されません**

4. 正しい認証情報が入力されると、ログインが完了します
   - コマンドを入力できる状態になれば、ログイン成功

### 2-2. 初期設定(OSのアップデート)
1. OSのアップデートを行うために、下記のコマンドを入力(5〜10分かかります)
```shell
sudo apt update && sudo apt full-upgrade -y
```

### 2-3. Tailscale(VPN)の設定
N Laboの教室からでも作業できるように、VPNをセットアップしていきます。
1. [Tailscaleの公式サイト](https://tailscale.com/)にアクセス。右上の`Log in`ボタンをクリック
![Tailscaleのトップページ](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/006.png)

2. `Sign in with Google`を選択し、Googleアカウントでログイン
![ログイン画面](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/007.png)

3. Welcome画面で`Personal use`を選択し、`Next`をクリック
![Welcome画面 - 1](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/008.png)

4. 使用中のデバイスのOSを選択し、`Download`をクリックしてTailscaleをダウンロード
![Welcome画面 - 2](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/009.png)

5. ダウンロードしたインストーラーを実行し、画面の指示に従ってインストール

6. インストール完了後、自動的にブラウザで接続画面が開くので、`Connect`をクリック
![接続画面](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/010.png)

7. `Login successful`の表示を確認。これで接続完了
![接続完了画面](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/011.png)

8. Welcome画面に戻り、`Skip this introduction`をクリック
![Welcome画面 - 3](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/012.png)

9. 管理画面で接続したデバイスの表示を確認。`Add device`>`Linux server`の順にクリック
![管理画面](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/013.png)

10. `Add Linux server`画面で`generate install script`をクリック。生成されたスクリプトをコピー
![Add Linux server](https://github.com/ncodelabo-yokohama/raspberry-pi-setup-manual/blob/main/imgaes/014.png)

11. Windowsの場合は、Win+R > `cmd`と入力し、Enterでコマンドプロンプトを、Macの場合はターミナルを開く
12. 下記のコマンドを入力し、先ほど起動したRaspberry Piに電源ケーブルを接続
```shell
# ホスト名の後に、.localを忘れずにつけること
ssh <自分で設定したRaspberryPiのユーザー名>@<自分で設定したRaspberryPiのホスト名>.local

# 例
# ssh ubuntu@raspi.local
```
13. 初回接続の場合は、`Are you sure you want to continue connecting (yes/no/[fingerprint])?`と聞かれるので、`y`と入力してEnter
14. 「OSのセットアップ」で設定したパスワードを入力(セキュリティ上の理由から表示されません)
15. `ubuntu@test-raspi:~$`のように表示されたら、先ほどコピーしたスクリプトをペーストし、実行(途中、ウィンドウが表示された場合、tabキーでカーソルを移動して、OKを選択し、Enterで進めてください。ただ、操作が効かない場合があるので、その場合はコマンドプロンプト or ターミナルそのものを閉じ、再度接続してみてください。)
16. その後、`ip a`と入力し、`tailscale0`というインターフェースが存在していればセットアップ完了