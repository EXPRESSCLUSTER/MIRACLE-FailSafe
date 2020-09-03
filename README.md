# MIRACLE FailSafe
## Webinar
### 2020/09/16 CUI で完結！ MIRACLE FailSafe の自動構築
- https://www.cybertrust.co.jp/info/2020/0826-failsafe-webinar.html
- Webinar で使用したスクリプトのサンプルを公開します。
  - https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916
#### サンプルスクリプトの利用方法
1. 必要に応じて、以下を事前にインストールしてください。
   - Node.js
   - MariaDB
   - Apache
1. MIRACLE FailSafe をインストールし、ライセンスを登録してください。
1. clpcfset コマンドを以下からダウンロードしてください。
   - https://github.com/EXPRESSCLUSTER/CreateClusterOnLinux/releases
1. 以下のディレクトリのファイル一式をダウンロードしてください。
   - 00_exec
     - 
   - 01_mariadb
   - 02_mariadb_apache
   - 03_mariadb_apache_same_group
   - CMS (WordPress)
1. 上記ダウンロードした perl ファイル (.pl) を実行してください。
1. クラスタを停止してください。
   ```sh
   # clpcl -t
   ```
1. 構成情報を反映してください。
   ```sh
   # ls

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