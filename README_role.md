# Ansible Role: Apache\_install

## Description

本Ansible RoleはWebサーバソフトウェアである"Apache HTTP Server"のインストールを行います。
対象バージョンは以下のバージョンです。

- Apache2.4 (RHEL7)

## Supports

- 管理マシン(Ansibleサーバ)
  * Linux系OS（RHEL/CentOS）
  * Ansible バージョン 2.0 以上 (動作確認済みバージョン：2.2、2.9)
  * Python バージョン 2.x、3.x  (動作確認済みバージョン：2.6、2.7、3.6)

- 管理対象マシン(構築対象マシン)
  * RHEL7

## Requirements

- 管理マシン(Ansibleサーバ)
  * 管理対象マシンとroot権限でSSH通信可能であること。

- 管理対象マシン(インストール対象マシン)
  * SELinuxが無効に設定されていること。
  * yumコマンドが利用できること
    + RHELレポジトリ（外部サーバ、媒体）が利用できること
    + プロキシ設定が適切に行われていること（外部サーバにアクセスする場合）
  * iptables,firewalldが適切に設定されていること

## Role Variables

Role の変数値について説明します。

### Mandatory variables

実行時には、必ず指定しないといけない変数はありません。

### Optional variables

任意に指定できる変数はありません。

## Dependencies

特にありません。

## Usage

1. 本Roleを用いたPlaybookを作成します。
2. Playbookを実行します。

## Example Playbook

インストールとすべての設定をする場合は、提供した以下のRoleを"roles"ディレクトリに配置したうえで、
以下のようなPlaybookを作成してください。

- フォルダ構成
~~~
  - group_vars/
    ・ server1
    ・ server2
  - host_vars/
    ・ host1
    ・ host2
  - roles/
    ・ Apache_install/
    ・ Apache_setup/
  - Apache_install.yml
  - Apache_setup.yml
  - conf.yml
  - hosts
  - site.yml
~~~

- マスターPlaybook サンプル「Apache\_install.yml」
~~~
 # Apache_install.yml
 - name: install  Apache
    hosts: all
    gather_facts: yes
    become: yes
    tags:
     - install
    roles:
     - Apache_install
~~~


## Running Playbook

- extra-varsを利用する場合の実行例
> ansible-playbook site.yml -k -i hosts --extra-vars="@conf.yml"

- group\_varsを利用する場合の実行例   
  group\_varsで指定したグループ名がwebserver1の場合
> ansible-playbook site.yml -k -i hosts -l webserver1

- host\_varsを利用する場合の実行例
  host\_varsで指定したホスト名がserver1の場合
> ansible-playbook site.yml -k -i hosts -l server1

- 本roleのみを実行する場合は --tags "install"を付け加える
> ansible-playbook site.yml -k -i hosts --extra-vars="@conf.yml" --tags "install"

# Copyright
Copyright (c) 2016 NEC Corporation

# Author Information
NEC Corporation
