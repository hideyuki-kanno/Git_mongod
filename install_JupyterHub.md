# JupyterHub 0.6�C���X�g�[���菇

OS:	Ubuntu 16.04

## �\��
* �f�B���N�g��
	- /etc/jupyterhub	�V�X�e���f�[�^
	- /var/jupyterhub	���[�U�f�[�^
* ���[�U
	- y_araki		�Ǘ���
	- kamae		���p��
* �O���[�v
	- jupyterhub	���p�҂̃O���[�v(�V�X�e����͕K�v�Ȃ����A�܂Ƃ߂邽��)

## �K�v�ȃ\�t�g�E�F�A�̃C���X�g�[��
	### Python 3.5�͓����Ă���
	$ sudo apt install python3-pip
	### Node.js�̃C���X�g�[��
	$ sudo apt install nodejs-legacy npm
	### Jupyter Notebook�̃C���X�g�[��
	$ sudo pip3 install jupyter

## JupyterHub�̃C���X�g�[��
	$ sudo pip3 install jupyterhub
	$ sudo npm install -g configurable-http-proxy

## �V�X�e���f�B���N�g���̍쐬
	$ sudo mkdir /etc/jupyterhub

## �ݒ�t�@�C�����쐬�A�ύX
	$ cd /etc/jupyterhub
	### �f�t�H���gconfig�𐶐�
	$ sudo jupyterhub --generate-config
	### config��ύX
	$ sudo -e jupyterhub_config.py
	c.Authenticator.admin_users = {'y_araki'}
	c.Spawner.notebook_dir = '/var/jupyterhub/%U'

## ���[�U�f�B���N�g���̍쐬
	$ sudo mkdir /var/jupyterhub
	$ sudo chown jupyter /var/jupyterhub
	$ sudo chmod a+rw /var/jupyterhub	# �N�ł��ǂݏ�����

## ���[�U�O���[�v�̍쐬
	$ sudo groupadd jupyterhub

## ���[�U�̍쐬
	# �z�[���f�B���N�g������A�p�X���[�h����
	$ sudo useradd -m -g jupyterhub kamae
	$ sudo passwd kamae
	# �f�[�^�f�B���N�g���̍쐬
	$ sudo -u kamae mkdir /var/jupyterhub/kamae

## �N��
	$ cd /etc/jupyterhub
	$ sudo jupyterhub --no-ssl

## ����m�F
	http://�T�[�o:8000/
