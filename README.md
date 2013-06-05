# Hoardup

## Overview

**hoardup** is a backup shell script.

* Using rsync

## Install

    curl -o hoardup https://raw.github.com/satoruk/hoardup/master/bin/hoardup
    chmod 755 hoardup

## Update

    $ hoardup self-update

## Quick start

    $ hoardup init backup
    $ cd backup
    $ hoardup backup

## Setup

セットアップはバックアップの内容次第で変わりますが、最低限SSHの公開キー認証で接続できると便利です.
以下は公開キー認証の手順です.

### Local side

まず、ローカルで公開キーと秘密キーのペアを作成します.

    $ ssh-keygen -t rsa -C username@example.com -f ./id_rsa
    id_rsa
    id_rsa.pub

### Server side

バックアップするターゲットのサーバにアカウントを作成します.


    # adduser --ingroup users username
    # usermod -G nogroup,backup,www-data username
    # sudo su username
    
    $ cat id_rsa.pub >> .ssh/authorized_keys


間違えたときは以下のコマンドでユーザが消せる

    # deluser username; rm -rf /home/username



