# install-ros2-on-WSL2
ロボット開発に必須なROS(Robot operating system)をインストールします。このセクションでは、Windows環境を想定してます。尚、このチュートリアルの開始前に以下のものがインストールされている場合はアンインストールしてください。
- Windows Subsystem for Linux (WSL)
- Windows Subsystem for Linux 2 (WSL2) 

## WSL2のインストール
1. 管理者権限でPowershellを開きます。（右クリック->その他->管理者権限で実行)。そして以下のコマンドを実行してWSLをオンにします。

```
wsl --install
```

2. ここでPCを再起動します。

7. 自動起動したUbuntu上でユーザーを作成します。ユーザー名を入れた後、パスワードを2回入力します（パスワードは、＊＊＊や●●●も表示されませんが、入力できています）。

8. ユーザー名＠ホスト名:~$と表示されたら成功です。

## Windows Terminal のインストール
[Windows Terminal (MS Store)](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=ja-jp&gl=JP)

これ以降はWindows Terminalを使用します。

## ROS2 Foxyをインストールする
この[サイト](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html)を参考にしました。

### 以下のコマンドを1行ずつ順次実行します
`~Y/n`と聞かれたら`Y`と入力します。パスワードを聞かれたらインストール時に設定したパスワードを入れます（パスワードは、＊＊＊や●●●も表示されませんが、入力できています）。

0. 下準備
```
sudo apt update
sudo apt upgrade
```

1. 言語設定 
```
sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

2. ROSリポジトリを追加
```
sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

```

3. 下準備２

```
sudo apt update
```

4. ROS2 Foxy 本体インストール
```
sudo apt install ros-foxy-desktop
```

5. vimをインストール

```
sudo apt install vim
```

6. .bashrcに書き込み
```
vim .bashrc
```

- `i`キーを押し編集モードに入る。
- 矢印キーで一番下に移動する。
- 一番下に`source /opt/ros/foxy/setup.bash`を書き込みます
- `ESC`を押し`:wq`を入力しファイルを閉じる。

7. Windows Terminal を閉じる

## 動作確認
1. Windows Terminal の Ubuntu20のターミナルに以下を入力します。
```
ros2 run demo_nodes_cpp talker
```
2. 別のウィンドウを開き以下を実行します。
```
ros2 run demo_nodes_py listener
```
