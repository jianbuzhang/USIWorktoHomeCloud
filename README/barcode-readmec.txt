
�@. �bimage download �ϥ� muti com �ʧ@,�`�N�U���ƶ�:
  1. �b�ؿ� \PORD\SYMBOL.INI
     ��[COM] �D�n�b�]�w�h�� COM PORT���������,�ثe�u��]�� COM9
     [USB] �D�n�O�w�� SYMBOL���פl�C�@��COM PORT �ҹ�����USB ID����,�קK�������~,1<-->1
  
  2.�b�ؿ� \PORD\PROJECT\ �U�i�H�]�w SYSTEMBOM.INI 
     [CONFIG] �D�n�b�]�wUSI���Ƹ�������Ȥ᪺�պA,�]�i�H�Ψӳ]�w�ۤv�Q�n���պA,�H���Ѧb
		FCTCOMMAND �������P�_���̾�
     
	\PORD\PROJECT\VERSION\Barcode.ini
		USI barcode�n�q���Ӧ�m�Ө��X,�n��barcode.ini����[Position]
		START=1 �M LENGTH=8 �ӳ]�w
                �� barcode.ini ����[Config] �N�O�̾کҹ����X�Ӫ��ȨӨ��X����ܼƭȤ�,�]�N
		�O�|���var.ini����[VARSTRING] ��,�̨�᪺�W�٨ө�J,fctcommand�]��var.ini
		���X�ӧP�_
		
		�n�ϥ�config ���\��bbarcode.ini [control] CONFIG=ON �n�]�w��ON
		CONFIGLength=18 ���פ]�n�]�w,��SYSTEMBOM.INI �������׭n�M��@�P
		
		[USIADD] �D�n�b��Ȥ᪺�պA�����H�]�t�����������,�i�H�[�JUSI��BARCODE�ӥ[�H��
			��,�H�W�[�u��,
			�n�ϥ��٭n�b barcode.ini [Position]���[�J  USIADD= ON
			�n�`�N��W�٤��n�M barcode.ini ��[Config] �W�٬ۦP,�]���|���ۻ\��

		
 
 3.�b�ؿ� \PORD\PROJECT\ �U�i�H�]�w SYSTEMBOM2.INI 
		�D�n�Φb���X�t�Τ��e�ҳ]�w����,�H�ѷs��BARCODE ���ͤ��۹���,�H�M�w�O�_�ݭn
		�A���P�˪��ʧ@,�ҦpIMAGE�O�_�n���sdownload.
       		��������]�w��:
	(1).\PORD\PROJECT\VERSION\Barcode.ini
    	    ��n��J�ĤG�� barcode�ӨѧP�_�ɭn�]�w�U�������
	    a.�b �ϥ�PBarcodeFM.exe ��  �n�Ŀ�,�~�|���X�����ѨϥΪ̿�J�ĤG�ժ�barcode,���b�h�x
		�ާ@��,�C�@�x���ݬO�P�@�ӲպA.
	    

	    b.��Jbarcode��,�|�qSYSTEMBOM2.INI���X�۹������պA,�n�q���Ӧ�m�Ө��X,
		�n��barcode.ini����[Position2] START=1 �M LENGTH=8 �ӳ]�w

                �� barcode.ini ����[Config2] �N�O�̾کҹ����X�Ӫ��ȨӨ��X����ܼƭȤ�,�]�N
		�O�|���var.ini����[VARSTRING] ��,�̨�᪺�W�٨ө�J,fctcommand�]��var.ini
		���X�ӧP�_��W�٭n�M ***[Config]*** ���ۦP�B����,����|�H �ۦP�W�٥[�@�� 2�ө��
		var.ini�� �Ҧp varsion2= abc ����
		
		
		[USIADD2] �D�n�b��Ȥ᪺�պA�����H�]�t�����������,�i�H�[�JUSI��BARCODE�ӥ[�H��
			��,�H�W�[�u��,
			�n�ϥ��٭n�b barcode.ini [Position2]���[�J  USIADD2= ON
			�n�`�N��W�٤��n�M barcode.ini ��[Config2] �W�٬ۦP,�]���|���ۻ\��


  �ثe�o�ӥ\��Φb PMCom.exe �M PBarcodeFM.exe ���զX��