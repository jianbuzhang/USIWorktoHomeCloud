Command         add-data                 discription

COM		dos command    		�g�� com port�e��ƨ� UUT��(�tenter) �p�G�n�e�ťզr
					�i�H�U COM SPACE (�u���@�Ӫťդ��tenter) 
					COM OFF , COM ON �i�}�� COM PORT 
					COM ON 38400  COM2 �bON �ɥi�H�]�w COM PORT���ǿ�v
							   �M���w���@��com port ��X�J
					COM =  �r���ܼƦW��

COMHEX 		ASCII-CODE		�i�g�� COM PORT�e16�i�쪺�r���UUT��.
					COMHEX  313A00  

GETHEX		ON | OFF		�i�g�� COM PORT ���i�Ӫ���ƥH16�i�����,����HON OFF
					�ӱ���
					GETHEX ON   ��ܱNCOM PORT����Ƨ�H16�i��Ȧ��J
					GETHEX OFF  ��ܱNCOM PORT����ƥH�r��Φ����J


                                                          
WAIT            waitstring,timeout	����COM port�e�L�Ӫ���Ʈֹ�,timeout���ݮɶ�(1000)��1�� 
					Default �O3����: ��: WAIT C:>,1000
SLEEP		delay-time		delay ms times ==> SLEEP 1000   (1 second)���@�����

END		NON			���յ����ɭn�[�o�Ӹ��,�~��o����է��������G  
					�� ==> END
ERRORCODE       data			�p�GUUT�ݨS���w�q���~�X,�i�ۦ�]�w���լy�{�������~�X 
                                        ==> ERRORCODE 0001, UUT�ݥi�z�LCOM port�eerror code��
                                        HOST �榡�p�� ERROR-CODE:0001  ,ERROR-CODE:�|�Q�����u
                                        �O�d 0001
SENDBARCODE 	NON			�z�LNI DIO �NBarcode�g�� UUT keyboard �e�� UUT  ��
                                        ==> SENDBARCODE
YESNO   	data			�]�wmessage box ���ϥΪ̽T�{ YES OR NO,��YES�|�e'YES'�� 
					COM port�åB�~�����U�������O,��NO �|�e'NO'��COM port
                                        �åB��ܿ��~�X,�������䥦���O,data����ܦr��


RUNPCEXE	data			����q���W�����ε{��,��com.ini IMAGE section �����W��,�p�G
					�䤤���n���N���r��i�� # �����,�h�|��SYMBOL.INI����USB Section
					����form ��caption���o���,���N# �o�ӲŸ��Ҧb����m

RUNSTR		DATA			DATA���o�ӰѼƬO�s�bcom.INI����IMAGE section �����W�٦r��
					�{���|�D�ʨ�Com.ini ����� SYMBOL section  ��APPATH�W��    
					�N APPATH �M  DATA �ҫ�����Ƶ��X�ܦ��һݭn�������Ӱ���
					�䤤���n���N���r��i�� # �����,�h�|��SYMBOL.INI����USB Section
					����form ��caption���o���,���N# �o�ӲŸ��Ҧb����m

					RUNSTR Monitor
					�|���Ͱ���
					D:\ibmbeta\GetWinH\Multi-Flash\MultiLoad.exe  (APPATH)
					d:\MC3000\DVT\BSP4.1.002\Hex Images\MC3000C42B\MC30XXC42XMon0115.bin
					(Monitor)

COPYDIR		data			DATA���o�ӰѼƬO�s�bcom.INI����IMAGE section �����W�٦r��
					�{���|�D�ʨ�Com.ini ����� SYMBOL section  ��APPATH�W��    
					�N APPATH �M  DATA �ҫ�����Ƶ��X�ܦ��һݭn�������Ӱ���
					�b SYMBOL section ���ҳ]�w�����Ϻо� �N��,���ҭn�s�񪺥ت�
					�Ϻо�,�� APPATH �O�T�w����PDDEClient.exe �ϥ�DDE Protocol
					�M pmcom.exe ���q.

					COPYDIR FEI
					�|�N COM.INI����[IMAGE] FEI= �ɮ׸��| �U�Ҧ���ƽƻs��۹�
					�� SYSBOL.INI���ҹ������Ϻо����h.
					

SDCOPY	DATA			


SYMBOLIMG	data			�]�wsymbol usb load�{��,data��com.ini [IMAGE] section ����ID
					�W�٨Ҧp: SYMBOLIMG Monitor   ; SYMBOLIMG  Partition ���h�|
					�N�ҫ��w�����|COPY ����ݪ����ؤ�,�ë�����

WAITALL         NON                     ���Ҧ��}�Ҫ���������o�ɤ~�~�����

USBDELAY	delay-time		�]�w����Ҧ������ɨC�ӵ������U���椤�������j	

SINGLEON	NON			�w��Image download����ֳt�L�k�P�B�U���i�H�t�XWAITALL �ӨϨ�@�_�}
SINGLEOFF	NON			�l,�M��@�Ӥ@�Ӱ���,�b Download������n�g SINGLEOFF�~��ϤU�@���~
					�� Download,�G��command �n�t�X�ϥ�


***********  �U�U�ܼƦW�٫ŧi����ۦP*****************************

VARREAL		DATA			�i�ƥ��ŧi����ܼ�,�ΥΨӰ���ƪ��p��
					VARREAL  ABC,DEF
					VARREAL  HILL = DEF + (ABC -1) / 2
					�Ω�B����ܼƥ��ݥ��e�ŧi�L,�����G�ܼ� HILL�h����

VARSTRING	DATA			�i�ƥ��ŧi�r���ܼ�,�ΥΨӰ��r�ꪺ�B��
					VARSTRING   ABC,DEF
					�i�s�r���ܼ� VARSTRING  ABC = DEF + '1234567'�䵲�G�� �r���ܼ�DEF�[
					�W1234567�����G�s�� ABC���ܼƦr�ꤤ,�p�GDEF���s�b�h�O���Ŧr��



VARRANGE	NAME			�i�Ω�ѥ��e�s���ܼƭȩM DIO.INI��[VARRANGE]�����Ȱ����,�ݬO�_�b�d
					�򤧤�,���W�٥����n�ۦP�~����
					VARRANGE ABC   �����bDIO.INI�MVAR.INI�����s�b ABC�o���ܼƤ~��
					���
*************************************************************************
@NAME					Label ��jump �ɨϥ�

JUMP		Lable			JUMP @123 ����ҼХܪ���m



CASE		DATA			DATA�Ȭ��r���ܼƦs�b�bVAR.INI����VARSTRING���i�̾�DATA�ӧ�nJUMP��Lable
					�p�G�n�զX�r��i�� VARSTRING FEI = VAR1 + VAR2 + VAR3 �M���
					CASE  FEI
					�p�GDATA ���r���ܼƭȤ��s�b�h�|���� @ELSE
                                        �ҥH���@�w�n�]�w�@�� @ELSE �� Lable

ECHO		DATA			�i�NDATA ����r��ܨ� LOG FILE ��; �p�G�� ECHO = ABC�������ܼƭ�,���s�b
					�|��� NON DATA,�p�GMESSAGE ON����,�]�|��ܨ�䤤                            

				