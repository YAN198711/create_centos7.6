# 使い方
Tera Termを起動、下記をコピー&ペースト

# はじめに
## ①初期化
```rm -f /var/run/yum.pid```
```yum clean all```

## ②Gitのインストール
```yum -y install git```

## ③Gitより実行ファイルをダウンロード
```git clone https://github.com/YAN198711/create_centos7.6.git```
```chmod -R 755 create_centos7.6```

## ④ファイルの実行
### (1)OSアップデートおよび日本語化（必須）：約5分
```./create_centos7.6/_basic.sh```

### (2)google-chromeのインストール（任意）：約1分
```./create_centos7.6/_chrome.sh```

### (3)デスクトップ環境(+ Windows Generator:WINE)のインストール（任意）：約1.5時間
```./create_centos7.6/_desktop_wine.sh```

### (4)リモートデスクトップのインストール（任意）：約3分
```./create_centos7.6/_remote_desktop.sh```

### (5)pythonのインストール（任意）：約10分
```./create_centos7.6/_python.sh```

### (6)cloud9のインストール（任意）：約5分
```./create_centos7.6/_cloud9.sh```

### (7)スマホから接続するファイルのインストール（任意）：約1分
```./create_centos7.6/_x11vnc.sh```

## ワンポイント！
複数を一気に構築したい場合、間に　**&&**　を入れて、文を繋げます。

#### ex1)(1)と(5)を実行したい場合、
```./create_centos7.6/_basic.sh && ./create_centos7.6/_python.sh```

#### ex2)python + cloud9 を実行したい場合（改行せずに入力)、
```./create_centos7.6/_basic.sh && ./create_centos7.6/_chrome.sh && ./create_centos7.6/_python.sh && ./create_centos7.6/_cloud9.sh```

#### ex3)デスクトップ + リモート接続 を実行したい場合（改行せずに入力)、
```./create_centos7.6/_basic.sh && ./create_centos7.6/_chrome.sh && ./create_centos7.6/_desktop_wine.sh && ./create_centos7.6/_remote_desktop.sh && ./create_centos7.6/_x11vnc.sh```

#### ex4)全て実行したい場合（改行せずに入力）、
```./create_centos7.6/_basic.sh && ./create_centos7.6/_chrome.sh && ./create_centos7.6/_desktop_wine.sh && ./create_centos7.6/_remote_desktop.sh && ./create_centos7.6/_python.sh && ./create_centos7.6/_cloud9.sh && ./create_centos7.6/_x11vnc.sh```


***
## ⑤システムの再起動
```systemctl reboot -i```

## ⑥cloud9を永続実行(（6）をインストール時、VPS再起動の度に実行必要)
TeraTermで再度接続を実施し、
```forever start ~/c9sdk/server.js -l IPアドレス(xxx.xx.xx.xx) -p 8080 -w ~/workspace/ -a 名前:パスワード```
※名前およびパスワードは管理しやすいものに変更 \
ex) \
IP：192.xx.xx.xx \
名前：user \
パス:abcd1234 \
```forever start ~/c9sdk/server.js -l 192.xx.xx.xx -p 8080 -w ~/workspace/ -a user:abcd1234```

## 下記にアクセスでcloud9に接続
```http://IPアドレス(xxx.xx.xx.xx):8080/ide.html```
ex)
```http://192.xxx.0.1:8080/ide.html```

## cloud9の設定
Python support \
Python Version　⇒　Python 3 \
PYTHON PATH　⇒　:/root/.pyenv/shims/python3 　を右端に追加 \
デフォルトのままなら以下の通りとなる \
```/usr/local/lib/python2.7/dist-packages:/usr/local/lib/python3.4/dist-packages:/usr/local/lib/python3.5/dist-packages:/root/.pyenv/shims/python3```