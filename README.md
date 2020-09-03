# MIRACLE FailSafe
## Webinar
### 2020/09/16 CUI �Ŋ����I MIRACLE FailSafe �̎����\�z
- https://www.cybertrust.co.jp/info/2020/0826-failsafe-webinar.html
- Webinar �Ŏg�p�����X�N���v�g�̃T���v�������J���܂��B
  - https://github.com/EXPRESSCLUSTER/MIRACLE-FailSafe/tree/master/script/20200916
#### �T���v���X�N���v�g�̗��p���@
1. �K�v�ɉ����āA�ȉ������O�ɃC���X�g�[�����Ă��������B
   - Node.js
   - MariaDB
   - Apache
1. MIRACLE FailSafe ���C���X�g�[�����A���C�Z���X��o�^���Ă��������B
1. clpcfset �R�}���h���ȉ�����_�E�����[�h���Ă��������B
   - https://github.com/EXPRESSCLUSTER/CreateClusterOnLinux/releases
1. �ȉ��̃f�B���N�g���̃t�@�C���ꎮ���_�E�����[�h���Ă��������B
   - 00_exec
     - 
   - 01_mariadb
   - 02_mariadb_apache
   - 03_mariadb_apache_same_group
   - CMS (WordPress)
1. ��L�_�E�����[�h���� perl �t�@�C�� (.pl) �����s���Ă��������B
1. �N���X�^���~���Ă��������B
   ```sh
   # clpcl -t
   ```
1. �\�����𔽉f���Ă��������B
   ```sh
   # ls

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