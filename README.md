# MIRACLE FailSafe
## Webinar
## 2020/09/16 CUI で完結！ MIRACLE FailSafe の自動構築
- https://www.cybertrust.co.jp/info/2020/0826-failsafe-webinar.html
- Webinar で使用したスクリプトのサンプルを公開します。
  - https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916
#### デモ環境
- MIRACLE LINUX 8 Aianux Inside (4.18.0-147.5.1.el8.x86_64)
- MIRACLE FailSafe (miracle-failsafe-4.2.1-2.x86_64)
- Node.js (v10.16.3)
- MariaDB (10.3.17)
- Apache (2.4.37)
#### サンプルスクリプトの利用方法
1. 必要に応じて、以下を事前にインストールしてください。
   - Node.js
     - RESTful API でクラスタを操作する場合に必要となります。
   - MariaDB
   - Apache
1. MIRACLE FailSafe をインストールし、ライセンスを登録してください。
1. clpcfset コマンドを以下からダウンロードしてください。
   - https://github.com/EXPRESSCLUSTER/CreateClusterOnLinux/releases
1. 以下のディレクトリのファイル一式をダウンロードしてください。
   |ディレクトリ               |用途|
   |---------------------------|----|
   |[00_base](https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916/00_base)|EXEC リソースのみ|
   |[01_mariadb](https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916/01_mariadb)|MariaDB の制御/監視|
   |[02_mariadb_apache](https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916/02_mariadb_apache)|MariaDB, Apache の制御/監視 (1つのグループで制御)|
   |[03_mariadb_apache_one_group](https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916/03_mariadb_apache_one_group)|MariaDB, Apache の制御/監視 (1つのグループで制御)|
1. clpcfset コマンドと perl ファイルを同一ディレクトリに保存してください。
   ```
   01_mariadb の場合

   01_mariadb
    |
    +-- clpcfset
    |
    +-- create_mariadb.pl
    |
    +-- scripts/
         |
         +-- failover1/
              |
              +-- exec-mariadb/
                   |
                   +-- start.sh
                   |
                   +-- stop.sh
   ```
1. ダウンロードした Perl ファイル (create_xxx.pl) を実行してください。
1. クラスタを起動している場合、クラスタを停止してください。
   ```sh
   # clpcl -t
   ```
1. 構成情報を反映してください。
   ```sh
   # clpcfctrl --push -l -x .
   ```
1. クラスタを起動してください。
   ```sh
   # clpcl -s
   ```
1. クラスタが正常に起動していることを確認してください。
   ```sh
   # clpstat 
   ```
#### 備考
- リソースの活性/非活性異常、モニタリソースの異常検出時の動作を意図的に抑制してあります。異常時の動作を有効にするためには、各 Perl ファイルの norecovery に 0 を設定してください。
  ```perl
  #
  # recovery action
  #
  # norecovery
  # 0: initiate recovery action
  # 1: not initiate recovery action
  my $norecovery = 1;  
  ```