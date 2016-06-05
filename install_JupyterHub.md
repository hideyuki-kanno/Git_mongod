# JupyterHub 0.6インストール手順

OS:	Ubuntu 16.04

## 構成
* ディレクトリ
	- /etc/jupyterhub	システムデータ
	- /var/jupyterhub	ユーザデータ
* ユーザ
	- y_araki		管理者
	- kamae		利用者
* グループ
	- jupyterhub	利用者のグループ(システム上は必要ないが、まとめるため)

## 必要なソフトウェアのインストール
	### Python 3.5は入っていた
	$ sudo apt install python3-pip
	### Node.jsのインストール
	$ sudo apt install nodejs-legacy npm
	### Jupyter Notebookのインストール
	$ sudo pip3 install jupyter

## JupyterHubのインストール
	$ sudo pip3 install jupyterhub
	$ sudo npm install -g configurable-http-proxy

## システムディレクトリの作成
	$ sudo mkdir /etc/jupyterhub

## 設定ファイルを作成、変更
	$ cd /etc/jupyterhub
	### デフォルトconfigを生成
	$ sudo jupyterhub --generate-config
	### configを変更
	$ sudo -e jupyterhub_config.py
	c.Authenticator.admin_users = {'y_araki'}
	c.Spawner.notebook_dir = '/var/jupyterhub/%U'

## ユーザディレクトリの作成
	$ sudo mkdir /var/jupyterhub
	$ sudo chown jupyter /var/jupyterhub
	$ sudo chmod a+rw /var/jupyterhub	# 誰でも読み書き可

## ユーザグループの作成
	$ sudo groupadd jupyterhub

## ユーザの作成
	# ホームディレクトリあり、パスワードあり
	$ sudo useradd -m -g jupyterhub kamae
	$ sudo passwd kamae
	# データディレクトリの作成
	$ sudo -u kamae mkdir /var/jupyterhub/kamae

## 起動
	$ cd /etc/jupyterhub
	$ sudo jupyterhub --no-ssl

## 動作確認
	http://サーバ:8000/
