# MIRACLE FailSafe
## Webinar
## 2020/09/16 CUI �Ŋ����I MIRACLE FailSafe �̎����\�z
- https://www.cybertrust.co.jp/info/2020/0826-failsafe-webinar.html
- Webinar �Ŏg�p�����X�N���v�g�̃T���v�������J���܂��B
  - https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916
#### �f����
- MIRACLE LINUX 8 Aianux Inside (4.18.0-147.5.1.el8.x86_64)
- MIRACLE FailSafe (miracle-failsafe-4.2.1-2.x86_64)
- Node.js (v10.16.3)
- MariaDB (10.3.17)
- Apache (2.4.37)
#### �T���v���X�N���v�g�̗��p���@
1. �K�v�ɉ����āA�ȉ������O�ɃC���X�g�[�����Ă��������B
   - Node.js
     - RESTful API �ŃN���X�^�𑀍삷��ꍇ�ɕK�v�ƂȂ�܂��B
   - MariaDB
   - Apache
1. MIRACLE FailSafe ���C���X�g�[�����A���C�Z���X��o�^���Ă��������B
1. clpcfset �R�}���h���ȉ�����_�E�����[�h���Ă��������B
   - https://github.com/EXPRESSCLUSTER/CreateClusterOnLinux/releases
1. �ȉ��̃f�B���N�g���̃t�@�C���ꎮ���_�E�����[�h���Ă��������B
   |�f�B���N�g��               |�p�r|
   |---------------------------|----|
   |[00_base](https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916/00_base)|EXEC ���\�[�X�̂�|
   |[01_mariadb](https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916/01_mariadb)|MariaDB �̐���/�Ď�|
   |[02_mariadb_apache](https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916/02_mariadb_apache)|MariaDB, Apache �̐���/�Ď� (1�̃O���[�v�Ő���)|
   |[03_mariadb_apache_one_group](https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916/03_mariadb_apache_one_group)|MariaDB, Apache �̐���/�Ď� (1�̃O���[�v�Ő���)|
1. clpcfset �R�}���h�� perl �t�@�C���𓯈�f�B���N�g���ɕۑ����Ă��������B
   ```
   01_mariadb �̏ꍇ

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
1. �_�E�����[�h���� Perl �t�@�C�� (create_xxx.pl) �����s���Ă��������B
1. �N���X�^���N�����Ă���ꍇ�A�N���X�^���~���Ă��������B
   ```sh
   # clpcl -t
   ```
1. �\�����𔽉f���Ă��������B
   ```sh
   # clpcfctrl --push -l -x .
   ```
1. �N���X�^���N�����Ă��������B
   ```sh
   # clpcl -s
   ```
1. �N���X�^������ɋN�����Ă��邱�Ƃ��m�F���Ă��������B
   ```sh
   # clpstat 
   ```
#### ���l
- ���\�[�X�̊���/�񊈐��ُ�A���j�^���\�[�X�ُ̈팟�o���̓�����Ӑ}�I�ɗ}�����Ă���܂��B�ُ펞�̓����L���ɂ��邽�߂ɂ́A�e Perl �t�@�C���� norecovery �� 0 ��ݒ肵�Ă��������B
  ```perl
  #
  # recovery action
  #
  # norecovery
  # 0: initiate recovery action
  # 1: not initiate recovery action
  my $norecovery = 1;  
  ```