# install-ros2-on-WSL2
ロボット開発に必須なROS(Robot operating system)をインストールします。このセクションでは、Windows環境及びUbuntu20環境を想定してます。尚、このチュートリアルの開始前に以下のものがインストールされている場合はアンインストールしてください。
- Windows Subsystem for Linux (WSL)
- Windows Subsystem for Linux 2 (WSL2) 

## WSL2のインストール
1. 管理者権限でPowershellを開きます。（右クリック->その他->管理者権限で実行)。そして以下のコマンドを実行してWSLをオンにします。

```
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

2. 仮想マシンプラットフォームをオンにするために以下のコマンドを実行します。

```
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

3. ここでPCを再起動します。

4. Powershellを一般ユーザー権限で開きます(普通に開く)。WSL2を指定するために以下のコマンドを実行します。

```
wsl --set-default-version 2
```

5. Linux Kernel update package を以下のURLよりダウンロードします。ダウンロードしたらインストールウィザードに沿ってインストールします。

[Linux Kernel Update Packege (Microsoft)](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)

6. Ubuntu 20.04LTS on WSL をインストールします。以下のリンクからインストールします。

[Ubuntu 20.04LTS on WSL (MS Store)](https://apps.microsoft.com/store/detail/ubuntu-2004/9N6SVWS3RX71?hl=ja-jp&gl=JP)

7. スタートメニューからUbuntu20.04を起動します。ユーザーを作成します。ユーザー名を入れた後、パスワードを2回入力します（パスワードは、＊＊＊や●●●も表示されませんが、入力できています）。
8. ユーザー名＠ホスト名:~$と表示されたら成功です。

## ROS2 Foxy のインストール。



