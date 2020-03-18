# Apache2.4 for RHEL7

## Trademarks

- Linuxは、Linus Torvalds氏の米国およびその他の国における登録商標または商標です。
- RedHat、RHEL、CentOSは、Red Hat, Inc.の米国およびその他の国における登録商標または商標です。
- Windows、PowerShellは、Microsoft Corporation の米国およびその他の国における登録商標または商標です。
- Ansibleは、Red Hat, Inc.の米国およびその他の国における登録商標または商標です。
- pythonは、Python Software Foundationの登録商標または商標です。
- Apache、Tomcatは、Apache Software Foundationの登録商標または商標です。
- Java およびすべてのJava 関連の商標は、Oracle Corporation およびその関連会社の登録商標です。
- NECは、日本電気株式会社の登録商標または商標です。
- その他、本ロールのコード、ファイルに記載されている会社名および製品名は、各社の登録商標または商標です。

## 概要
本プロジェクトのリポジトリでApache HTTP Serverのインストール、セットアップRoleを公開しています。  
OSSの対象バージョンは以下のバージョンとなります。  
・Apache2.4  
　  
対応OSは以下となります。  
・RHEL7  

各ロールの説明はREADME_role.mdをご参照ください。

## Supports

- 管理マシン(Ansibleサーバ)
  * Linux系OS（RHEL/CentOS）
  * Ansible バージョン 2.0 以上 (動作確認済みバージョン：2.2)
  * Python バージョン 2.6 または2.7


- 管理対象マシン(構築対象マシン)
  * Red Hat Enterprise Linux 7

## roles

 - Apache_install  
    Apache2.4のパッケージのインストールを行うroleです。  
    提供している機能は以下です。

   * Apache2.4関連のパッケージのインストール


 - Apache_setup  
  Apache2.4のconfファイルへの設定を行うroleです。  
  提供している機能は以下です。

   * httpd.conf、proxy.confへの設定
   * サービスの自動起動設定の変更
   * Apache2.4の再起動


## Exastro IT Automationでの利用時について
Exastro IT Automation(以下、ITA)利用時に必要なITA独自ファイル「ita_readme_role名.yml」 を公開しています。  
ITA独自ファイルのないroleに関してはそのままITAで利用することができます。  
ITAの操作方法、ITA独自ファイルの利用方法についてはITAの利用マニュアルをご確認ください。  

### ITA利用時の注意事項

  - ITAの代入値管理において以下の不要な変数が表示されます。
     この変数は、Apache2.4においては不要ですので、入力の必要はありません。  

      + VAR_Apache_PidFile  
      + VAR_Apache_DefaultType  

  - ITAの代入値管理においてVAR_Apache_ServiceAuto変数のデフォルト値が空欄で表示されますが、role内では、default値として"off"が定義されています。  自動起動設定を有効にしたい場合のみ代入値管理で"on"を指定してください。  

# Copyright

Copyright (c) 2016 NEC Corporation

# Author Information

NEC Corporation

