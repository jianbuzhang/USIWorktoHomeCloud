Command         add-data                 discription

COM		dos command    		�g�� com port�e��ƨ� UUT��(�tenter) �p
					�G�n�e�ťզr�i�H�U COM SPACE (�u���@��
					�ťդ��tenter) 
					COM OFF , COM ON �i�}�� COM PORT 
					COM ON 38400  COM2 
					�bON �ɥi�H�]�w COM PORT���ǿ�v�M���w
					RTS CONTROL������
					COM ON 38400 COM2 ON
					COM ON 38400 COM2 OFF
					�̫᪺ON OFF�O�M�wRTSControl�O�_�}�ҥi�b
					�o���ʺA�ק�,�p�G�n�T�w�i�bGB.INI���]�w
					ON ��ܨϥ�RTSControl
					OFF ��ܤ��ϥ�RTSControl

					���@��com port ��X�J
			   		COM =  �r���ܼƦW��
					
					�{�������G��COM Device�i�]�w,�����w�h��
					�βĤ@��COM Device �]�w�i�� COM ON/OFF 
					���L�{�ӫ��w�ϥ� @@1 or @@2  �ӰϹj
					COM OFF @@2    COM ON 38400 COM2  @@2
					COM =  �r���ܼƦW�� @@2
					COM ABCD.EXE  @@2


COMFILE		data    		�g�� com port�eTXT�ɮ׸�ƨ� UUT��,����
					��COM PORT�n�����},�~�i�H����o�өR�O,
					DATA���r������G�ӳ����� , �����j.  
					�Ĥ@�ӳ���:���C�@�椧���n����h�� ms 
					�ĤG�ӳ���:���ҭn�ǿ骺txt file �����|�M
					�ɦW
					
					COMFILE  50,D:\123.TXT 



                                                          
COMHEX 		ASCII-CODE		�i�g�� COM PORT�e16�i�쪺�r���UUT��.
					COMHEX  313A00  

					�{�������G��COM Device�i�]�w,�����w�h��
					�βĤ@��COM Device �]�w�i�� COM ON/OFF 
					���L�{�ӫ��w�ϥ� @1 or @2  �ӰϹj
					COMHEX  313A00 @2    
					



GETHEX		ON | OFF		�i�g�� COM PORT ���i�Ӫ���ƥH16�i����
					��,����HON OFF �ӱ���
					GETHEX ON ��ܱNCOM PORT����Ƨ�H16�i
						    ��Ȧ��J
					GETHEX OFF ��ܱNCOM PORT����ƥH�r���
						    �����J


DIO		name  value		�Ѧ� DIO.INI  [dio] setion & name==>
					     DIO DATA1 255
					name �i�bDIO.INI���ۦ�]�w�һݪ����
					�p�G�u���@��bit�]�i�� DIO data1  ON   
					; DIO data1 OFF �Ӱ��}�����ʧ@

DIOMACRO	name			�Ѧ�DIO.INI [DIOMICRO] Setion & name�i�b
					DIO.INI���ۦ�]�w�һݪ����name 
					DIOMICRO  POWERON
                                        
DIOREAD		name  data		�Ѧ�DIO.INI [dio] setion-name �]�wname &
					������data �p�GNI DIO ���^����ƩMdata 
					�ۦP�hTRUE �_�h�^�� FALSE �i�H�s���ܼƤ�
					�ӧP�_ DIOREAD  DATA1 = ABCD�A�H 
				   IF ( ABCD > 234 ) THEN @ERROR1 ELSE @ERROR2

					DIOREAD  DATA1 = ABCD >> 
					�h�|�N��Ƥ]�s��VAR.INI����savevar
					section ���ܼƸ��,�̫�|�[��
					testlog.txtvar���� 



ACHV		name			�Ѧ� 
					DIO.INI [ACHV] setion & name==>ACHV V3P7
					name �i�bDIO.INI���ۦ�]�w�һݪ���Ʀp�G
					�������h�|�s��var.ini��������ܼƤ�,���P
					�_���
					ACHV  TEST1 = MYTEST 
					���G�|�s�� VAR.INI����MYTEST�ܼƤ�

					ACHV  TEST1 = MYTEST >> 
					�h�|�N��Ƥ]�s��VAR.INI����savevar
					section ���ܼƸ��,�̫�|�[��
					testlog.txtvar����,���P�_��� 

					ACHV  TEST1  >> �h�|�N��Ƥ]�s��VAR.INI
					����savevar section���ܼƸ�ƥ�errorcode
					���W��,�̫�|�[��testlog.txtvar����,�|
					�P�_��� 

ACHI		name			�Ѧ� DIO.INI [ACHI] setion & name==> 
					ACHI   OperaTionChargeTest1
					�p�G�������h�|�s��var.ini��������ܼƤ�,
					���P�_���
					ACHI  TEST1 = MYTEST  
					���G�|�s��VAR.INI����MYTEST�ܼƤ�

					ACHI  TEST1 = MYTEST >> 
					�h�|�N��Ƥ]�s��VAR.INI����savevar
					section ���ܼƸ��,�̫�|�[��
					testlog.txtvar	����,���P�_���

					ACHI  TEST1  >> �h�|�N��Ƥ]�s��VAR.INI
					����savevar section ���ܼƸ�ƥ�
					errorcode���W��,�̫�|�[��
					testlog.txtvar����,�|�P�_��� 


SAVEWAIT	ON / OFF		�i�H�]�w�O�_�n�N���쪺�r���s�b�ܼƤ�,
					�H�ѸѪR�r��ϥ�,�ݭn�t�XWAIT�Өϥ�
					SAVEWAIT ON   ���}���ݦr���s��
					WAIT GOOD = MYDATA �|�N����GOOD�r�ꪺ��
						    �@��s��VARINI����varstring
						    �ܼƦW�٬� MYDATA ����Ƥ�
					SAVEWAIT OFF    �������ݦr��檺�s��
					

                
WAIT		waitstring,timeout	����COM port�e�L�Ӫ���Ʈֹ�,timeout����
					�ɶ�(1000)��1��	Default �O3����: 
					��: WAIT C:>,1000
				WAIT (crc32 is 0xAB744A4C~crc32 is 0x87F536A4) 
					�i�H���ݦh�Ӧr�� 

					~ ��or,  & �� and
					���ݦr�꦳ , �ɥi�ΤU�����D�]�w
 					WAIT (crc32,4,),2000  �o�ɭԫ᭱�@�w�n
					�]TIME OUT ���ɶ�,����]=�M>>

					WAIT crc32 is 0xAB744A4C = TEST,2000 �|
					�N���Χ䤣��g��r���ܼ�
					TEST �� TEST= TRUE  or  TEST= FALSE�i��
					IF�Ӱ��P�_�b�� = �������A�U����ɶ��W�L
					�ɤ��|����,�u�|�]�w�ܼƬ�FALSE�M���~��
					�U����
					
				WAIT ABC = TEST >>,2000 WAIT ABC >>,2000
					�S��= �������k�ɪ�������,  >> �h�|�N���
					�]�s��VAR.INI����savevar section ���ܼ�
					��Ƴ̫�|�[��testlog.txtvar����

					WAIT �ᤣ������r��,�hUUT�ǨӪ��r��|��
					�ɫO�s�bBUFFER�����e�X�ӳB�z����U�@�� 
					WAIT waitstring �r�ꪺcommand�X�{�ɤ~�|
					�N���e���r��e�X�ΥH����j�q�ֳt��ƳB
					�z�t�ת����D

                                        
WAITVAR  DATA				�NVARSTRING �����ܼ� DATA�W�٨��X�Ӵ���
					WAIT waitstring,timeout���榡
                                        �Ҧp:
                			VARSTRING DATA = 'ABC >>,2000'
					WAITVAR DATA
					�|�ܦ�:
					WAIT ABC >>,2000
 
VARSTRING TEST = 'ABC = GOOD,10000'     �p�GUUT �ǰe���r��O ABC HELLO
SAVEWAIT ON				�h���쪺�r��GOOD���e�ȬO
WAITVAR TEST				GOOD = ABC  HELLO
SAVEWAIT OFF
ECHO = GOOD                                     


FINDPCFILE     TimeInterval filename	�M���ɮ׬O�_�s�b,�O�_�O�b���w����Ƥ����ͪ�
					TimeInterval: ���\�b�h�֮ɶ��d��,�H�����
					filename: �n��M���ɮ׸��|�M�W��.

					��:
					FINDPCFILE  60 C:\TD.TXT
					
					��ܴM�� TD.TXT�ɮ׬O�_�s�b,�O�_�O�b60����
					���ͪ��ɮ�.
					VARSTRING TEST = '60 C:\TD.TXT'
					FINDPCFILE = TEST
					���G�M�W�z�ۦP.
					��쪺��
					VARSTRING BFINDPCFILE = TRUE
					�S��쪺��,�ε۶W�L�ɶ�
					VARSTRING BFINDPCFILE = FAIL

                                        �i�H�ϥ�*��,���u�|�ϥβĤ@�ӧ�쪺FILE�����
					FINDPCFILE 60  C:\T*.TXT
 

WAITFILE	waitstring,timeout	�O���ݬY�ӥؿ����O�_��waitstring���ɮצW
					�٥X�{,timeout���ݮɶ�(1000)��1��Default
					�O3����: 
					��: WAITFILE C:\TEMP\TEST.TXT,1000  
					��ܵ�TEST.TXT�o���ɮפ@����,�W�L�ɶ��N
					FAIL,�p�G�n�H�o�ӳq�����~,�i��
					UUT_FAIL.DAT
					�ӧi���䥢��:  
					�n��b�P�ŧi���ۦP���|��C:\TEMP\ 

					��: WAITFILE = ABC,1000
  					��ܭn�qVAR.INI�����r���ܼ�ABC���X�ɮ׸�
					�|,�i�H�Φ������ҬY���ɮ׬O�_�s�b




WAITNOW	        waitstring,command,type,number
					
					����COM port,Lan �e�L�Ӫ���Ʈֹ�,�p�G�s
					�b�Ҧ��쪺�r��,�h��type�ҩw�q���ǿ��k,
					�N�r��^�Ǧ^�h,�öǰe�h�֦�number
 					
					
					type: 1,2��com port �ǿ�, 3�� Lan �ǿ�

					��:  WAITNOW  {,d,1,20
					==> ���� { �r��, �ϥ� com port �e�X d �o
					    �Ӧr�� 20��
					��:  WAITNOW  {,d@2,1,20
					==> ���� { �r��, �ϥ� com2 port �e�X d 
					   �o�Ӧr�� 20��

					�b�᭱�ݭn����Y�Ӧr�ꦬ���n�U
 					
					WAITNOW OFF  �~�|�����o�ӥ\��





SLEEP		delay-time	  delay ms times ==> SLEEP 1000   
					(1000 =  1 second)���@�����

SMB		name			�]�wusi smart battery borad�q�� 
						refrence 
					DIO.INI [ACHI] 
					setion & name ==>
					 SMB OperaTionChargeTest1 

KEY		data			��dio�����e key�Ȩ� UUT ��L ==> KEY A 
					���tENTER,�Ѧ�DIO.INI [KEY]��� �M
					[DIO] KEYDATA ��DIO port �]�w

KEYSTRING	data			��dio�����e�r��� UUT keyboard 
					==> KEYSTRING  test? 
					(?is enter) ��l�]�w�P KEY�����
					�z�Ldio�����e���,�@�Ӧr���@�Ӧr������
					�e

DAC		name			�]�w DAC��ưѦ�DIO.INI [DAC] setion & 
						name
					==> DAC SINWAVE ON  (ON | OFF),�YNI 
					analog ��X�]�w


PULSE           NAME  ON/ OFF		�]�wCOUNTER ��X��i�T��,�i�]�w�һݪ��W
					�v,�]�w��ưѦ�
					DIO.INI [PULSE]  setion 
					==> PULSE  P200 ON ��X�W�٬�P200���W�v.
					    PULSE  P200 OFF ��������P200����X




ALLKEYTEST	delay-time		�i�H�ק� DIO.INI [ALLKEY] setion
					���ȨӲ��Ϳ�J����
                                        
POST		data,timeout		�g��LPT PORT��������post code data
					==> POST A0,3000  
					timeout���ݮɶ�(1000)��1��Default �O3
					���� 

LPTW		data			�g��ƨ�LPT PORT,�����G�خ榡,�gLine 
					and �g port
				port => 0:data port; 
					1:Status port 
					2:control port
					�n�gline�h�n���T�Ӹ��:
					LPTW  port,line,data  
					==>  LPTW  0,2,1    
					data�u�ର0,1
					�g port �h�u���G�Ӹ��
 					LPTW  port,data  ==>  LPTW 0,234         
					data < 255


LPTR		data = varName		�g��ƨ�LPT PORT,�����G�خ榡,�gLine 
					and�g port
			port => 0:data port; 1:Status port 2:control port
					�n�gline�h�n���T�Ӹ��:
				LPTR  port,line = varName  
					==>  LPTR  0,2 = MYTEST   Line�u�ର
					0-7�g port �h�u���G�Ӹ��
 				LPTR  port = varName
					==>  LPTW 0 = mydata    
					�|�s���ܼ�mydata���i�H�A�t�Xvarrange��
					�P�_����εۥ�if-then-else�ӨM�w
					
					�ثe�u�䴩EPP MODE,�Х��NBIOS���]�w�令
					EPP MODE �o��command�~���

#�o�өR�O�������ΤF
# RJ1145	NON			�g�� DIO.INI [RJDATA] setion ���]�w,�n�t
#					�Xfunction Board�Ӳ��� loop back �\��,��
#					�bIBM UUT


END		NON			���յ����ɭn�[�o�Ӹ��,�~��o����է���
					�����G  
					�� ==> END

ERRORCODE	data			�p�GUUT�ݨS���w�q���~�X,�i�ۦ�]�w���լy
					�{�������~�X 
				==> ERRORCODE 0001, UUT�ݥi�z�LCOM port�e
				        error code��HOST�榡�p��ERROR-CODE:0001
					,ERROR-CODE:�|�Q�����u�O�d 0001
					�p�G�[ > ���᭱���r�N�|�b buglist���X�{
					����~����T
					ERRORCODE 0001 > TEST FIRST


TDERRCODE	data			�o�ӬOTD�]�w��ERRORCODE,�o��ERROR CODE�M
					ERRORCODE ���w�q�ۦP,���|�e��SFIS,������
					�P�{����Retry�ʧ@,�{����retry�٬O�H
					ERRORCODE ���D,���|���쩹�e��
 					TDERRCODE
 
				==> TDERRCODE 0001, 
					
					�p�G�[ > ���᭱���r�N�|�b buglist���X�{
					����~����T
					TDERRCODE  0001 > TEST FIRST
					



SENDBARCODE	NON		�z�LNI DIO �NBarcode�g�� UUT keyboard 
					�e�� UUT  ��
				==> SENDBARCODE

YESNO		data			�]�wmessage box ���ϥΪ̽T�{ YES OR NO,
					��YES�|�e'YES'�� log file�åB�~�����U
					�������O,��NO �|�e'NO'��log file�åB��
					�ܿ��~�X,�������䥦���O,data����ܦr
					��

					YESNO  = ABC �i�������ܼƦr��,���ݦs
					�b VAR.INI����
					�p���s�b�h�|��� ABC: OK

SELECT		data			�]�w select box �� USER ��ܭn�ϥΨ��@
					��,USER ��ܫ�|�̿諸���Ǧs�� VAR.INI 
					����[VARSTRING] ���� SELECT �ܼƤ��n��
					�ܪ����إ� ' , ' �Ӥ��j,�̶��Ƿ|�s�� 
					1,2,3...����
					SELECT  test1,test2,test3 �|���ͤT�ӿ�
					�� test1~3
					



CLOSESMB	NON			�����Ҧ�smart battery board���q���]�w	


COUNTER		name			�Ѧ� DIO.INI  [COUNTER] setion & name
					==>COUNTER VGAMODE 
					�D�n�b�q�����i�M�b�i�����,�ѤW�U���ӧP
					�_���T�P�_
					COUNTER  VGAMODE = MYTEST ���G�|�s�� 
					VAR.INI����MYTEST�ܼƤ�
					COUNTER  VGAMODE = MYTEST >> �h�|�N���
					�]�s��VAR.INI����savevar section ���ܼ�
					���,�̫�|�[�� testlog.txtvar����,���P
					�_��� 
			
					COUNTER  VGAMODE >> �h�|�N��Ƥ]�s��
					VAR.INI����savevar section���ܼƸ�ƥ�
					errorcode���W��,�̫�|�[��
					testlog.txtvar����,�|�P�_��� 


SENDMAC		Dos-command		�g�� barcode.ini���o MAC data ,
					Dos-command �OUUT�ݭn�g�JMAC��ƪ� DOS 
					���O(by chipset	support),���O�|�z�Lcom 
					port���XDos-command �MMAC ��ƨӰ���,�p
					�GCOMMAND�n�MMAC�s�b�@�_�h�U Command~
					�h���O�|����CommandMAC���M�O����
					Command  MAC
					

SENDGUID	Dos-command		�g�� barcode.ini���o GUID data ,
					Dos-command �OUUT�ݭn�g�JGUID��ƪ� DOS 
					���O(by chipset support),���O�|�z�Lcom 
					port ���XDos-command �MGUID ��ƨӰ���,
					�p�GCOMMAND�n�MGUID�s�b�@�_�h�UCommand~ 
					�h���O�|����CommandGUID ���M�O����
					Command  GUID 


WRITEBARCODE	Dos-command		�g�� barcode.ini���o BARCODE data , 
					Dos-command �OUUT�ݭn�g�JBARCODE ��ƪ� 
					DOS���O(by chipset support),���O�|�z�L
					com port���XDos-command �MBARCODE ���
					�Ӱ���,�p�GCOMMAND�n�MBARCODE�s�b�@�_�h
					�U Command~ �h���O�|����CommandBARCODE 
					���M�O����
					Command  BARCODE 
					exp:
					WRITEBARCODE  UUT /A/B ,2,5  
					==> UUT /A/B 
					��UUT �ݪ��R�O,��,2,5���barcode �Ѳ�
					�G�������5�Ӱe�N�|���� UUT /A/B 23456
					�e�X�h




FAILSTOP				��FCTCOMMAND �D�ʩI�s��fail stop.�S����
					��

DOSCMD					�i�H�ϥ�DOS �������R�O,�|���o�^����,�Ҧp:
                                        DOSCMD ipconfig
					DOSCMD ping 127.0.0.1
					DOSCMD adb devices
                                        �i�H�ϥ��ܼƦW��:
					VARSTRING MYIP = 'ipconfig'
					DOSCMD = MYIP
					��ĪG���P
					DOSCMD ipconfig
                                        �I�sBAT FILE �ɻݵ��������|
                                        �`�N�ƶ�:
                                        1.�����|�ɭn���Ϻо��N��
                                        2.���|�W�٤����n���ťթM . (�I)���Ÿ�,�|
  				          �~�P
					3.bat file�@�w���ݥ[�J.bat�����ɦW,�]���o
					  �O�P�_�O�_��bat file���з�

			doscmd   adb push f:\battloop.txt  /storage/sdcard0/DCIM
			doscmd  dir/w d:\
			doscmd  f:\battloop.txt

                     DOSCMD D:\USIPROJECT\IMAGE\NCR\Release-0410_TDD\flashall.bat

SAVETOFILE command data			�i�N�ҭn����r�s���ɮ�,command���U�C�X��
					CLEAR �M�����e�Ҽg�����
					ADD   �[�J�ҭn����r
					NAME  �n�s���ɮצW��.


					ON �q�o�өR�O�᪺�r�굥�P�ϥ�ADD �[�J
					OFF�@�����۰ʥ[�J���R�O
					ON/OFF�u�@�ΦbLAN, COM���q�~�ӿ�J���r��

					,�Ҧp:
                                        SAVETOFILE CLEAR   
					SAVETOFILE ADD  DIR/W C:\
					SAVETOFILE ADD  ECHO TEST
					SAVETOFILE NAME C:\MYTEST.BAT
					SAVETOFILE ON
					SAVETOFILE OFF

					�W�����\��
   					1.�M�����
					2.�[�J�r�� DIR/W C:\
					3.�[�J�r�� ECHO TEST
					4.�N�[�J����r,�s���ɮצW��C:\MYTEST.BAT
					5.�}�l�[�J�r��
					6.�����[�J�r��
command data �]�i�H�ϥΦr����N
varstring test1 = 'ADD DIR/W C:\'
varstring test2 = 'NAME C:\MYTEST.BAT'
SAVETOFILE = Test1
SAVETOFILE = Test2





LOADFILE  data			�i�N�ҭn����r�ɮ�,�q�ɮ׸��J��FCT COMMAND���ؿ�
                                ��:
                                 LOADFILE F:\MYTEST.TXT
                                 LOADFILE F:\MYTEST.BAT

                                �p�G�n����r�ɤ�����ƥi�ΤU�C��k.
				WAIT
				LOADFILE F:\MYTEST.TXT
				WAIT B0:05:94:FD:B2:96,5000
 

*********************** GPIB FUNCTION******************************************
POWERSAFE	ON/OFF			�]�wON ��,�@���q�����տ��~�ߧY�_�q,OFF��
					�i�H����,default��OFF


GPIBCONFIG	name			�g�� DIO.INI [GPIBConfig] setion & name
					==>GPIBConfig AAA
					�z�LGPIB�ӳ]�w PowerSupply��GPIB�������]
					��

SETHPPOWER	name			�g��DIO.INI  [HPPOWERSET] setion & name
					��ƨӳ]�wGPIB
					PowerSupply ==>SETHPPOWER SET37V

READGPIBDATA	name			�g�� DIO.INI  [GPIBDATA] setion & name��
					��ƨӳ]�w�����==>READGPIBDATA HPCurrent,
					�i�ɥ�TYPE ��ܬO�nŪ���q���ιq�y�ȦA�P 
					UP & LOW �Ȥ����^��TRUE OR FASLE
					READGPIBDATA HPCurrent = ABC 
						�i�N�^�Ǫ���Ʀs���ܼƤ�
					READGPIBDATA HPCurrent = ABC >> 
						�h�|�N��Ƥ]�s��VAR.INI����
					savevar section ���ܼƸ��,�̫�|�[��
					testlog.txtvar����,���P�_��� 
					
					READGPIBDATA HPCurrent  >> �|�ۦ�P�_��
					��,�|�N��Ʀs��VAR.INI����
					savevar section ���ܼƸ�ƥ�errorcode��
					�W��,�̫�|�[��testlog.txtvar�����|�P�_
					���


HPOUTPUT	ON/ OFF			�g�� GPIB�����]�wPOWER ��X�OON or OFF
					==> HPOUTPUT ON

GPIBSTR		DATA			DATA�r��z�LGPIB PORT�Ӱe��GPIB DEVICE

					GPIBSTR  =  �r���ܼƦW��
					�i�ɥ��ܼƨӲ��ͩR�O�C
 					VARSTRING  MYDATA = '*IDN?';
					GPIBSTR = MYDATA 

					

GETGPIBSTR	DATA = varName		DATA���n��GPIB PORT�U�F�n�^�Ǹ�ƪ�
					COMMAND,�ݵ��ܼưѼƦW��
					GETGPIBSTR CURR:STATE = ABC 
					    �����e����DEVICE COMMAND,�᭱���n
						�s���ܼƦW��ABC
					GETGPIBSTR CURR:STATE = ABC >> 
						�h�|�N��Ƥ]�s��VAR.INI����
					savevar section ���ܼƸ��,�̫�|�[��
					testlog.txtvar����,���P�_��� 
					
					�p�G�S��= varName�N�|�����NŪ�쪺��Ʃ�
					��VARSTRING ���� GPIBQuery��

GPIBCOMPARE    DATA			DATA���n��諸���,��GETGPIBSTR �Ǩ�
					VARSTRING ���� GPIBQuery.�|�۰ʤ��
					�p�GDATA ������Ʀs�b GPIBQuery��
					�N�|�Ǧ^pass,�_�h���ܷ|�޵oUUT-FAIL

					GETGPIBSTR *IDN?
					    �]���S��= ���ܼƩҥH�|�s�b
					VARSTRING GPIBQuery��
					�A�U:

					GPIBCOMPAR 6632B 
						�h�|���GPIBQuery�����r���O�_
					�]�t��6632B�o�Ӧr��
					
					
*********************** VISA  FUNCTION****************************************

VISA  Command  DATA			�D�n�O�z�LNI VISA�ɭ��ӱ���Ҧ��i��VISA
					�s�����ɭ�,�pCOM ,GPIB,USB...����

                                        Command �Ϥ���
                                        1.FindResource
  					2.RsrcName 
					3.OPEN
					4.CLOSE
					5.WRITE
					6.READ
1. FindResource ���M�䥻���O�_�������i�s�u�� VISA Device,�|�N�ҧ�쪺�귽��� 
		LOG ��,�H�ѧP�_�O�_�n�����򱱨� VISA���ʧ@.

                VISA FindResource

2. RsrcName DATA	���ҧ�쪺 resource �r��]�w,�䬰���wVISA Device �ϥ�
			,Data�n�]�w���ҭn�s����sorce �r��,�@�w�n���]�w����~��
			�ϥ� OPEN CLOSE, WRITE,READ���R�O,���M�L�k�ϥΥH�U�|��
			�R�O

		VISA RsrcName  USB0::0x0957::0x0507::MY44003692::INSTR
		VISA RsrcName  ASRL3::INSTR
                VISA RsrcName  = DATA ��ܥ�VARSTRING����X�W��DATA���r��Ӵ��N



3. OPEN		�����}�ҫ��w���]��,�S�� DATA �Ѽ�
		
		VISA OPEN


4. CLOSE		�������ҫ��w���]��,�S�� DATA �Ѽ�
		
		VISA CLOSE

5. WRITE  DATA	���̾کҥ��}�� Device �ϥΤ�U�U�F����������O 
		
		VISA WRITE  *IDN?
                2.3.5.6 �����䴩
                VARSTRING TEST = 'WRITE *IDN?'
                VISA = TEST
                ���P VISA WRITE *IDN?


6. READ   varName  �ݰt�X WRITE �Ӿާ@,�S��WRITE ���|��READ����ƥiŪ
		  VISA PORT �U�F�n�^�Ǹ�ƪ�COMMAND,�ݵ��ܼưѼƦW�� varName
		  VISA READ = ABC �᭱���n�s���ܼƦW��ABC,�|�s�JVARREAL �ܼ�
				��,�ҥH�@�w�n�O��Ƹ�Ʀp�G���O��Ƹ�ƭn�t�X 
				  SAVEWAIT�Ӱ�

		  VISA READ = ABC >> �h�|�N��Ƥ]�s��VAR.INI����savevar 
				     section���ܼƸ��,�̫�|�[��
				     testlog.txtvar����,���P�_��� 			


******************************************************************************

ACHWAVE		name  			�g�� DIO.INI [ACHWAVE]���oACH wave ���I
					�M�C�I�t�ȬO�_�btop<->low���϶���
					==> ACHWAVE AUDIO 
					�i�s���ܼƦW�٤� ACHWAVE AUDIO = ABCD 
					ACHWAVE AUDIO = ABC >> 
					�h�|�N��Ƥ]�s��VAR.INI����savevar 
					section	���ܼƸ��,�̫�|�[��
					testlog.txtvar����,���P�_��� 
					
					ACHWAVE AUDIO   >> �|�ۦ�P�_���,�|�N
					��Ʀs��VAR.INI����savevar section ����
					�Ƹ�ƥ�errorcode���W��,�̫�|�[��
					testlog.txtvar����


ACHFREQ		name			�g�� DIO.INI [ACHFREQ]���]�w�i�H�P�_ �W
					�v,offset, �p��p���Ȯt,���W�v�ŧQ����
					�����j�p��
						ACHFREQ  FEI
                                        
					�i�s���ܼƦW�٤� ACHREQ FEI = ABCD �|��
					�ʥHABCD���ͥ|�ո��
						ABCD1 = �p��p���Ȯt
						ABCD2 = OFFSET
						ABCD3 = �W�v
						ABCD4 = ���W�v���ŧQ���ഫ����

					ACHREQ FEI = ABCD >> ,���P�_���,�|�N��
					�Ƥ]�s��VAR.INI����
					savevar section���ܼƸ��,�̫�|�[��
					testlog.txtvar�������u�s�G�ӭ�Offset&�W
					�v
						ABCDO = OFFSET
						ABCDF = �W�v
 
					
					ACHREQ FEI  >>�|�ۦ�P�_���,�|�N��Ʀs
					��VAR.INI����savevar section ���ܼƸ��
					��errorcode���W��,�̫�|�[��
					testlog.txtvar�������u�s�G�ӭ� Offset & 
					�W�v
						errorcodeO = OFFSET
						errorcodeF = �W�v

         



DACPOINT	name 	ON/OFF		�g�� DIO.INI [DACPOINT] setion & name��
					�]�w�T�w��DAC��X�q��
					===>  DACPOINT V3P7 ON /OFF
					�]�i�H�ϥ�VARREAL���ܼƨӳ]�w���
					 DACPOINT V3P7 = MYDATA       
					MYDATA�O����ܼ�,�i�b�]�w�e���w
					�Ҧp VARREAL MYDATA = 3.55

                                        

//�H�U����������NI CARD DIO
NIDIO		name  value		�Ѧ� DIO.INI  [dio] setion & name
					==>NIDIO DATA1 255
					name �i�bDIO.INI���ۦ�]�w�һݪ����


NIDIOREAD	name  data		�Ѧ�DIO.INI [dio] setion-name �]�wname 
					& ������data �p�GNI DIO ���^����ƩM
					data �ۦP�h TRUE �_�h�^�� FALSE 
					   NIDIOREAD  MYDIO 233
					�i�H�s���ܼƤ��ӧP�_ 
					NIDIOREAD  name = ABCD
					�A�H 
			IF ( ABCD > 234 ) THEN @ERROR1 ELSE @ERROR2

					NIDIOREAD  name = ABC >> 
					�h�|�N��Ƥ]�s��VAR.INI����
					savevar section���ܼƸ��,�̫�|�[��
					testlog.txtvar����,���P�_���
	
					NIDIOREAD  name DATA1 >> �|�ۦ�P�_���
					,�|�N��Ʀs��VAR.INI����savevar section
					���ܼƸ�ƥ�errorcode���W��,�̫�|�[��
					testlog.txtvar����


NIDIODIR	name			�Ѧ� DIO.INI  [NIDIODIRECT] setion & 
					name �i�H��������NI CARD��IN OUT 
					����V ---> 
					NIDIODIR PORT0 
					NIDIODIR PORT1 
					NIDIODIR PORT3

/*					�j�d��mark,��\��Pc++���\��,�ݰt�X */
					�@������

RUNPCEXE	DATA	DATA�������ɦbpc�ݪ����|,�ɮצW��,�p�G
					�ӵ{���v�g�s�b�i�t�XPfindexe.exe�ӧ�{
					���Ӱ���i�קK���ư���
					RUNPCEXE  Pfindexe.exe �n���檺exe ��
					�{����caption
	==>RUNPCEXE  Pfindexe.exe   C:\WINDOWS\system32\calc.exe "�p��L"
	==> RUNPCEXE = ABC    �h�|�� var.ini��r���ܼ�ABC�ӥN�J����
        ==> RUNPCEXE "C:\PROGRAM FILE\ABC B.EXE " �p�G���|���Ů�n��" �]�_��
        ==> RUNPCEXE "C:\PROGRAM FILE\AA.EXE ;/A/B"���Ѽƪ��ܤ]�n�]�_�Өæb��
					�ƫe�[�W�����H���Ϥ�



EXECLOSE	DATA	�p�G�HData�� caption �������s�b����,�N��
					�{������


RUNSTR		DATA			DATA���s�bCOM.INI��[IMAGE] section ��KEY�W
					�ٵ{���|�D�ʨ�Com.ini ����� [SYMBOL] section  
					��APPATH�W�ٱN APPATH �M  DATA �ҫ�����Ƶ�
					�X�ܦ��һݭn�������Ӱ���䤤���n���N���r��i
					�� # ����ܡA�h�|��SYMBOL.INI����USB Section
					����form ��caption���o��ȡA���N# �o�ӲŸ���
					�b����m
		�Ҧp:
		COM.INI
		[SYMBOL]
		APPath=D:\HexLoader.exe	
		[IMAGE]
		 Monitor= /u # /d 3 \IMAGE\MC3000\30XXc50AenMO0133XX.hex
		SYMBOL.INI
		[USB]
		DEVICEID =ABC
	
		RUNSTR Monitor
		�|���Ͱ���
		Runpcexe D:\HexLoader.exe /u ABC /d 3 \IMAGE\MC3000\30XXc50AenMO0133XX.hex



IF					
					�C�@�ӼƤ����n���ť�, �r��e��n�[ ' �� 
					=> 'abcd' �n����
					����m THEN @abc ELSE @123  �B��Ÿ���
					�n���ťհϹj���M�O�q�̫e�}�l�����ҥH
					�n�קK����.

				IF ( BOX1 = 'ABC' ) THEN @ABC ELSE @ERROR  
						�r����BOX1�O�r���ܼ�
				IF ( BOX1 = BOX2 ) THEN @ABC ELSE @ERROR  
						�r����BOX1,BOX2�O�r���ܼ�    

	IF ( ( USB5V_1 > 4.75 ) AND ( USB5V_1 <  5.25 )  )  THEN @USB5V_11   
					�٤䴩�U�C�զX:
					 NOT * / AND + - OR XOR >  <  >=  <=  
					<>  =
					<> ��ܤ�����

	�ϥ��ܼ�	
	ERRORCODE 0000

	VARREAL TEST = 0X12300

	IF ( (TEST > 0X1230A ) AND ( TEST < 0X123FF) ) THEN @PASS ELSE @FAIL
	@FAIL
	  YESNO FAIL
	  JUMP @MYTEST
	@PASS
	  YESNO PASS

	@MYTEST
	END

	�ϥΦr��
	ERRORCODE 0000

	VARSTRING TEST = '123A0'

	IF ( (TEST > '1230A' ) AND ( TEST < '123FF') ) THEN @PASS ELSE @FAIL
	@FAIL
	  YESNO FAIL
	  JUMP @MYTEST
	@PASS
	  YESNO PASS

	@MYTEST
	END



FLAG		DATA 			�D�n�ϥΦbRetest �ɷ��ҩl��m���P�_
					�i�H��֤w���L�����ح��ЦA��,���s�y�{
					���H���ݦۦ�w��
					FLAG 0 
					FLAG 1
                                     

@NAME					Label ��jump �ɨϥ�

JUMP		Label			JUMP @123 ����ҼХܪ���m
					�t�~�]�i����r���ܼƫ��ܨ�n������m
					VARSTRING  MYJUMP = @TESTJUMP

					JUMP = MYJUMP
					�o�ӵ��G�|�M
					JUMP @TESTJUMP ���@�άۦP

***********  �U�U�ܼƦW�٫ŧi����ۦP******************************************

LAB      Source  Distiation		�o�ӥ\��b�p��color LAB�� Delta E,�^��
					����T�|��b VARREAL LABTEMP��,�H�ѫ���
					�P�_Source �O�bDIO.INI section [LAB]��
					���W��,��s�񤤶��Ȫ� L A B �H�ťհϹj
					Distianation �O�H VARSTRING �ҲզX�X��
					��L A B�r���ܼƥH�ťհϹj
 


VARREAL		DATA	�i�ƥ��ŧi����ܼ�,�ΥΨӰ���ƪ��p��
					VARREAL  ABC,DEF
					VARREAL  HILL = DEF + (ABC -1) / 2
					�Ω�B����ܼƥ��ݥ��e�ŧi�L,�����G�ܼ� 
					HILL�h���i��16�i��B��
					VARREAL TEST1 = 0x1101
					VARREAL TEST2 = 0x101
					VARREAL TEST3 = TEST1 AND TEST2
					
					�i�H�ϥΰʺA�ܼƦW�٫ŧi
  					TEST1 �OVARSTRING �ε� VARREAL�����s��
					�Ҧp VARSTRING TEST1 = 'MYVAR' + '1'  '2' '3'
					�h TEST1 �r��|�ܦ� MYVAR1 �p�G�᭱�ϥ�
					COUNT �ӳv���[�h�|�X�{ MYVAR2 MYVAR3 

					VARREAL  TEST1 << DEF + (ABC -1) / 2
 					�h�W�@�榡�l�|�s�� VARREAL �ܼƤ��H 
					MYVAR1 ���W�٦s��
                                        ��:
                      VARREAL ICOUNT = 2
                      VARSTRING TEST = 'MYVAR'+ ICOUNT 
                      
                      VARREAL TEST <<  ( 20 * 2 )

                      �o�ɷ|���ͤ@�� MYVAR2�� VARREAL �ܼƭȬ�40
                      �ϥ� ECHO = MYVAR2 �|��� 40




STRHEX          DATA			�S���ܼƩM�r��ɬ��]�w�ثe�ҭn�]�wHEX��
					����,
					STRHEX 12   ��ܩұo�����G���O�H12�쪺��
						    �ƪ��רӦs,���D�U���A�ץ�
					�䥦���W�h�PVARREAL ���B��.
					�u���b�ݭn�o��HEX �r��ɤ~�ݭn�ϥ�
					
					VARREAL ABC = 123                  
					STRHEX 12
					STRHEX HEX = ABC
					ECHO = HEX
					���G=> 00000000007B
					�]��123��10�i����


					
					VARREAL ABC = 0X123                  
					STRHEX 12
					STRHEX HEX = ABC
					ECHO = HEX
					���G=> 000000000123
					�]��123��16�i����


					16�i��n�p�U����k�e���� �sX ���O�^��rO
					STRHEX  12
					VARREAL HEX1 = 0X000FFF
					VARREAL HEX2 = 0X00F
					STRHEX HEX3 = HEX1 + HEX2
					ECHO = HEX3
					�|���  00000000100E
	


VARSTRING	DATA			�i�ƥ��ŧi�r���ܼ�,�ΥΨӰ��r�ꪺ�B��
					VARSTRING   ABC,DEF
					�i�s�r���ܼ� 
					VARSTRING  ABC = DEF + '1234567'
					�䵲�G�� �r���ܼ�DEF�[�W1234567�����G�s
					��ABC���ܼƦr�ꤤ,�p�GDEF���s�b�h�O����
					�r��i�H�ϥΰʺA�ܼƦW�٫ŧi
  					TEST1 �OVARSTRING �ε� VARREAL�����s��
					�Ҧp VARSTRING TEST1 = MYVAR + '1'

					VARSTRING  TEST1 << DEF + '1234567'
 					�h�W�@�榡�l�|�s�� VARSTRING �ܼƤ��H 
					MYVAR1 ���W�٦s��

 					�p�G�ݭn�[���i��#�Ө��N + ��:  
					VARSTRING DATA = 'ABC# 234'
					�h ECHO = DATA �|��ܥX ABC+ 234
 					�p�G�ݭn#���i��2��# ��:  
					VARSTRING DATA = 'ABC##234'
					�h ECHO = DATA �|��ܥX ABC#234

					VARSTRING S1 = 'ABCD'+0X27
                                        ECHO = S1
					�o�쪺�ȬO ABCD' 
					0X�u��]�w�@�Ӧr��.����ϥ�0X4142
					�n�Ϊ��ܥu�� VARSTRING S1 = 0X41 + 0X42


                                        

VARRANGE	NAME			�N���e�s���ܼƭȩM DIO.INI [VARRANGE]���]
					�w�Ȥ��A�ݬO�_�b�d�򤧤��A���W�٥����n
					�ۦP�~����		
					DIO.INI
					[VARRANGE]
					ABC =  1  10
					VARRANGE ABC   
					�h�|�h���ABC�o�ӭȬO�_�b1-10����
					VARRANGE ABC >>
					�|�N��Ʀs��VAR.INI��[savevar] section 
					Key�ȥH�ܼƦW��ABC�x�s

					 


COMVAR		VARNAME   LINE		�i�N COM OR LAN �Ǧ^�Ӫ���Ʀs��VARREAL 
					���ܼƤ�,�p�G���Ʀr�h�i��VARRANGE �Ӱ��P
					�_,�p�G���r��h�n�ϥ� IF THEN ELS �� 
					COMMAND �ӧP�_ LINE ���n��Ǧ^���r��ĴX
					��r��s�� VARNAME �ҫ��w���ܼƤ�,���ɦp
					�ϥ� WAIT ���ݦr��h�|�L�k�ϥ�,���ݭn��
					��
					**SAVE COMVAR OFF**
					�~�|��_���`
					COMVAR  MYTEST   2       
						��^�Ǫ��ĤG��r��s���ܼƤ�
					COMVAR  MYTEST           
						��^�Ǫ��Ĥ@��r��s���ܼƤ�

					

SUBSTRING    TYPE  NAME  Position Token  �i�NVAR.INI���� VARREAL or VARSTRING��
					�r��I���X�ӦA�s��VAR.INI��
					1.TYPE  = R | S  R:��VARREAL��� 
							 S:��VARSTRING�����
					2.NAME  ��bVAR.INI  VARREAL �ε� 
						VARSTRING���ܼƦW��
					3.Position  ��ܭn�s�����r��Ҧb����m
					4.Token ��ܥγo�Ӧr�����j�r��, ����
						�h���H�ťզr��Ӥ��j

                                        SUBSTRING  R  ABC  3  #        
					    ==>��� VARREAL ����ABC �ܼƥH# 
					    �Ӥ��j���ĤT��
                                        SUBSTRING  S  ABC  3  #        
					    ==>��� VASTRING ����ABC �ܼƥH# 
					   �Ӥ��j���ĤT��
                                        SUBSTRING  S  ABC  3  # = TEST  
					     ==>��� VASTRING ����ABC �ܼƥH#
					     �Ӥ��j���ĤT��,�M��s�� TEST�ܼƤ�

                                        SUBSTRING  S  ABC  3   = TEST  
					    ==>��� VASTRING ����ABC �ܼƥH'�ť�'
					    �Ӥ��j���ĤT��,�M��s�� TEST�ܼƤ�

SUBSTRING2   TYPE  NAME  Start Length  �i�NVAR.INI���� VARREAL or VARSTRING���r
				      ��I���X�ӦA�s��VAR.INI��
				1.TYPE  = R | S R:��VARREAL��� 
						S:��VARSTRING�����
				2.NAME  ��bVAR.INI  VARREAL 
					�ε� VARSTRING���ܼƦW��
				3.Start  ��ܭn�s�����r��_�l��m
				4.Length ��ܱq�_�l��m���h�������

                                        SUBSTRING2  R  ABC  3  3        
					==>��� VARREAL ����ABC �ܼƱq3�}�l����
					��3
	 					
                                        SUBSTRING2  S  ABC  3  3       
					==>��� VASTRING ����ABC �ܼƱq3�}�l����
					��3
					   
                                        SUBSTRING2  S  ABC  3  3 = TEST  
					==>��� VASTRING ����ABC �ܼƱq3�}�l����
					��3�M��s�� TEST�ܼƤ�
                                        SUBSTRING2  R  ABC  3          
					==>��� VARREAL ����ABC �ܼƱq3�}�l����
					����
					  

					  


REPLACESTR  NAME  OLDSUB  NEWSUB	�i�NVAR.INI ��VARSTRING���r��I���X�ӧ�
					�l�r���^�s.
					1.NAME �bVARSTRING���r���ܼƪ��W��
					2.OLDSUB �b�r�ꤤ�Q�n���N���r��
					3.NEWSUB �b�r�ꤤ����OLDSUB���r��


				VARSTRING  TEST = 'OK7,ESN_NUMBER=S09174521100049'
				REPLACESTR TEST =  *
				ECHO = TEST

				�|�ܦ�  OK7,ESN_NUMBER*S09174521100049
				
                             �p�G�S���� NEWSUB�Ѽ�,�h��ܱq�r�ꤤ�R�� OLDSUB�r��




SAVEVARTXT	TYPE*NAME,...		�i�N�ܼƦs��@���ɮפ���,�i��{�����]�w,
					�b������|�s��bTEST LOG���̫᭱
					 TYPE*NAME, TYPE*NAME,  ......
					
					1.TYPE*NAME, TYPE*NAME,  ......(
						R:��VARREAL��� 
						S:��VARSTRING�����)
					  SAVEVARTXT  R*DATA1,S*DATA2,R*DATA3
					

TIMESTRING     Formate			�i�̮榡���o�t�ήɶ�,��� VARSTRING MYTIME��,
					�n�ϥήɥi�I�s MYTIME ���o�ܼ�.
 					��:
					TIMESTRING   mm/dd/yyyy hh:nn:ss
					MYTIME = 11/10/2015 14:54:40
 					�i�ή榡�p�U:

y  = Year last 2 digits 
yy  = Year last 2 digits 
yyyy  = Year as 4 digits 
m  = Month number no-leading 0 
mm  = Month number as 2 digits 
d  = Day number no-leading 0 
dd  = Day number as 2 digits 
h  = Hour number no-leading 0 
hh  = Hour number as 2 digits 
n  = Minute number no-leading 0 
nn  = Minute number as 2 digits 
s  = Second number no-leading 0 
ss  = Second number as 2 digits 
��:
d/m/y = 5/6/00
dd/mm/yy = 05/06/00
d of mmm yyyy = Mon 5 of Jun 2000
  

//�D�n�Φb�Ʊ�ɥѵ{���۰ʮե��C�@�x���x���P�ѼƮɨϥ�.
GetINIData    Section  name  TYPE  INITYPE			
  					�i��symbol.ini ����section �M 
					name �����X��Ʃ�� var.ini ����
					VARSTRING or VARREAL �� section��
					�H�ۦP���W��name �Ӧs�� 
					
					TYPE :  R  / S   R:��ܩ� VARREAL ��
							 S:��ܩ�� VARSTRING��
					
				GetINIData   VCC  VCC3  R 
					==>��ܱq symbol.ini ����VCC Section 
					���W�٬�VCC3���ȩ�� var.ini ���� 
					VARREAL Section ���W�٬�  VCC3
				GetINIData  VCC  VCC3  S 
					==>��ܱq symbol.ini ����VCC Section��
					�W�٬�VCC3���ȩ�� var.ini ���� 
					VARSTRING Section ���W�٬�   VCC3


      INITYPE ��ܭn�q���@��INI FILE �ӧ���,�����N�u�|�qSymbol.ini����
      1:Barcode.ini
      2:change.ini
      3.GB.INI
      4.DIO.INI
      5.COM.INI
      



SaveINIData   Section  name  TYPE	�i��var ini ���� TYPE �M name �����X��
					�Ʃ�� symbol.ini ���� SECTION���H�ۦP
					���W�� name �Ӧs��
					TYPE :  R  / S   
						R:��ܱq VARREAL �����X
						S:��ܱq VARSTRING �����X
					
				SaveINIData  VCC  VCC3  R 
					==>��ܱq var.ini����VARREAL Section 
					���W�٬�VCC3���ȩ�� symbol.ini ����
					VCC Section ���W�٬� VCC3 ���a��
				SaveINIData  VCC  VCC3  S 
					==>��ܱq var.ini����VARSTRING Section 
					���W�٬�VCC3���ȩ�� symbol.ini ���� 
					VCC Section ���W�٬� VCC3 ���a��


		


					  
******************************************************************************


UIMACRO		NAME			�i�ƥ��� DIO.INI���� [UIMACRO] ���w�q��
					�n��COMMAND,�p���i�H²�檺�R�O�ӤU�F,�i
					�Ѧ�
					INIREADME UIMACRO  PORWRON


TIMESTOP	DATA			�i�]�w��h�[�{���n����,���ɶ���ɷ|�N
					VAR.INI���� �r��  TIMESTOP=TURE
					DATA ==>  ON stoptag  ��stoptag �H����
					�p����  TIMESTOP ON 3 
					==>��ܭp�ɨ�T�����ᵲ��
					TIMESTOP OFF �h�Y�������p��
					�D�n�ϥΦbAUTO RUN�ɰ�LOOP �n���h�[��
					�]�w�n�]�wAUTO�ɭn�]�wBarcode.ini����
					[logfile] ���� AUTO=TRUE;


ECHO		DATA			�i�NDATA ����r��ܨ� LOG FILE ��; �p�G
					�� ECHO = ABC�������ܼƭ�,���s�b�|��
					�� NON DATA,�p�GMESSAGE ON����,�]�|���
					��䤤�b�r�ꤤ�[ ~ �|�۰ʴ���  
					ECHO ABCD~ABCD


MESSAGE		ON / OFF		�i�H�N�T���������,�i�z�L ECHO�� Command
					�ӧ��ܵ����    

INPUTBOX	CAPTION = VARNAME,length
				 	�i�bINPUTBOX���N��J���r��s�� VARNAME
					���ܼƤ�,CAPTION�O�n��ܪ������r��
					INPUTBOX  MY BARCODE = BARCODE �h��J��
					��Ʒ|�s��VAR.INI����VARSTRING����
					BARCODE�ܼƤ�.  

					INPUTBOX  TEST = MYVAR,20
					��ܿ�J��CAPTION �O TEST
						  �s���ܼ�  MYVAR
						  �ܼƪ���  20 
					���רS���ܨS������,�]���|���ɿ�J����
					�����׮ɥ��ݦb1sec ���駹,�tenter key
					
                         

LAN             dos command   �g��lan�e��ƨ� UUT��ON / OFF�Ψӳ]�w
					LAN���}��
					LAN ON  4000    / LAN OFF 
					�bon �ɥi����lan ��port ��,�bON���᭱�[
					�WPort���ȧY�i
					LAN  SEND-COMMAND-String
					�]�i�H�� = �᭱���ܼƪ��覡�Ӷǰe
					SAVEBARCODE

				VARSTRING FEI = 'C:\ABC\ABC.EXE '+ BARCODE
					LAN = FEI  �Φr���ܼƨӰe�Ѽ�

					
					�{�������G�ӥH�W��Client�s��PUSIGB�i�]�w
					@@1, @@2, @@3 ���Ӫ�ܭn�N��ƶǵ����@��
					Client,�����w�h�O�ǵ��Ĥ@�ӳs�W�Ӫ�
					Client.
				LAN ABCDEFG  @@2  
					��ܧ� ABCDEFG �r��ǵ��ĤG�ӳs�W�Ӫ�
					Client	

CLAN            DATA  �g��lan�e��ƨ� SERVER ��ON / OFF�Ψӳ]�w
					CLAN���}��
					CLAN ON  4000    / LAN OFF 
					�bon �ɥi����lan ��port ��,�bON���᭱�[
					�WPort���ȧY�i
					CLAN ON 4000 127.0.0.1�i�H���ܩҭn�s��
					SERVER IP

					CLAN  SEND-COMMAND-String
					�]�i�H�� = �᭱���ܼƪ��覡�Ӷǰe
					

				VARSTRING FEI = 'C:\ABC\ABC.EXE '+ BARCODE
					CLAN = FEI  �Φr���ܼƨӰe�Ѽ�

				��SERVER IP PORT�|�MBARCODE FORM�ϥΤ@�P���]�w
				�|�bBARCODE.INI �εۦbCHANGE.INI���]�wSFIS��IP
				�MPORT���a��

   �d��:
	#-----------------------------------------------#
	#	    Get MC3K ESN Number			#
	#-----------------------------------------------#
	ERRORCODE MC0A >Compare ESN Number with SFIS
	CLAN ON
	GETINIDATA CODE EMP_NO S 2
	ECHO = EMP_NO
	GETINIDATA CODE FixtuerID S 2
	ECHO = FixtuerID
	GETINIDATA Logfile ProductLine S 2
	ECHO = ProductLine

VARSTRING SENDSFIS = FixtuerID + ',' + BARCODE + ',7,' + EMP_NO + ',' + ProductLine + ',,OK,ESN_NUMBER=???'
	ECHO Send command to SFIS:
	ECHO = SENDSFIS
	CLAN = SENDSFIS

	SAVEWAIT ON
	WAIT ESN_NUMBER = SFIS_STRING
	SAVEWAIT OFF
	ECHO String From SFIS:
	ECHO = SFIS_STRING
	SUBSTRING2 S SFIS_STRING 16 15 = ESN_SFIS
	ECHO Get ESN Number:
	ECHO = ESN_SFIS
	CLAN OFF

	VARSTRING ScanESN = 'GetESN.exe GetESN ' + ESN_SFIS + ' PlanCode 5211'
	COM = ScanESN
	WAIT SUCCESSFUL TEST




	
					

TOBARCODEFORM   Type,Data   		�g�� TCP/IP �e��ƨ� Barcode form
					1: ��ܩҰe����Ƭ� MAC data 
					2: ��ܩҰe����Ƭ� GUID data 
					3: ��ܩҰe����Ƭ� SSN data
					
					4: ��ܩҰe����Ƭ� SN2 data
					5: ��ܩҰe����Ƭ� MO_NUMBER data
					
					TOBARCODEFORM  1,123456789012


					�]�i�H�� = �᭱���ܼƪ��覡�Ӷǰe
					VARSTRING FEI = '1,'+ MACCODE
					TOBARCODEFORM = FEI �Φr���ܼƨӰe�Ѽ�

					1)���իe�Y GUID��즳��J,�|�e�� SFIS
					�@�ˬd
					2)�i�� TOBARCODEFORM �R�O������
					FCTCommand ���s��e MAC �� GUID �Ψ��
					������Ƶ� SFIS ���r��
					(�O�o�n LAN ON)
					Example:
  					a. �e��@MAC:  
     					TOBARCODEFORM = 1,123456789012
     
     					�e�h��MAC:  
     	VARSTRING PATH = '1,MAC1=000000000001 MAC2=000000000002 MAC_CNT=2'
     	TOBARCODEFORM = PATH
 
	VARSTRING PATH1 = '1,MAC1=' + GUID + ' MAC_CNT=1' + ' OTHER_MAC1=' + WLAN_SFIS
 	VARSTRING PATH = '1,MAC2=' + MAC + ' OTHER_MAC1=' + WLANMAC
 
  					b. �u�eGUID:  
     					TOBARCODEFORM = 2,1234567890123456
     
     					GUID�᪺���]�e:(�o�����U�M�׭n��SFIS 
					�Q�׭���������ơA�H D9900	���ҡA
					SFIS���� GUID ��@���e��L��ơA�O�o
					�n�γr���j�})
VARSTRING PATH = '2,0010207318112233,CSN1=00000000000001 CSN2=00000000000002'
    TOBARCODEFORM = PATH
 
					PS. �H�W�\��A�Ω� SendBarcodeOnly=OFF
					�� ShopFlow=ON �����p
 

					
					�bBarcode form �����ƫ�|�^��DATA����
					�i�̳o�ӨӧP�_Barcode from�O�_����



CASE		DATA			DATA�Ȭ��r���ܼƦs�b�bVAR.INI����
					VARSTRING���i�̾�DATA�ӧ�nJUMP��Lable
					�p�G�n�զX�r��i�� 
				VARSTRING FEI = VAR1 + VAR2 + VAR3 
					�M���
				CASE  FEI
					�p�GDATA ���r���ܼƭȤ��s�b�h�|���� 
				@ELSE
                                        �ҥH���@�w�n�]�w�@�� @ELSE ��
					Lable
                                          

SAVEBARCODE	NON			�|�s�bVAR.INI���� VARSTRING section��,
					�H�ܼƦW��BARCODE,MAC,GUID���W�٦s�r��
					�ܼ�,�p�G���h��MAC���ѼƦs�b MultiMAC 
					section �|�s��MAC1,MAC2...���ܼƤ�.
					�̫�SCAN�� Mac code �|�bControl��,�䥦
					���|��bMultiMAC ����J�����Ǧs��

					2.2.5.9�����H��|�h�s�@�Өt�Υثe�ɶ�
					�|��bTIMENOW



HOSTIP		DATA			�|�NHOST IP Address �s�� VAR.INI���� 
					VARSTRING section��,�H�ܼ� DATA ���W��
					�s�b�ܼƤ� ==> HOSTIP  MYIP  �|�N 
					IP address �s�� MYIP���ܼƤ� 


GETINI		SECTION	NAME VARNAME	�|�NProd\symbol.ini ���� section- name
					����Ʀs��r���ܼ� VARNAME ����,�H����
					�{�����Ӧs���ϥ�,�bsymbol.ini���D�n�]
					�w�Mlocal pc�������ܰʸ��,�]���i��C
					�xpc�ȷ|���P,�ҥH��W�]�w�b���� 
					fct command �ϥ�,
					�Ҧp usb id , com port BT MAC ����
					GETINI MAC 1  MYMAC ==>�o�q�O�� 
					Symbol.ini ����MAC section ,�W�٬� 1 
					���Ȧs��var.ini���r���ܼ�  MYMAC ��
  		�bSYMBOL.INI �����]�w
 		 [MAC]
   		1= ABCD12345678
   		2= TESTABC
					�p���ڭ̥i�H�NFCTCOMMAND �@�P�Ƥ��ΨC
					�xPC�n�]�w���P���y�{



GETSYSTEMBOM    NAME			�|���o�ҦbPROJECT ��SYSTEMBOM.INI��
					CONFIG section ���������,���o��ƫ�
					�|��� var.ini���r���ܼ� MYBOM ��
					
					��:
  					 GETSYSTEMBOM  0001
       
					��ܥ� systembom.ini����config section
					����ID ��0001����Ʃ��var.ini���r����
					��MYBOM ��

					��:
  					 GETSYSTEMBOM  = ABC
       
					ABC ��VAR.INI�����r���ܼ�,�N����X����
					��@ID �A�� systembom.ini����
					config section����ID ����Ʃ��var.ini
					���r���ܼ�MYBOM��



SAVELOG		NON			�|�N�ثe��LOG ��ƥ���s��,���ε����
					��������~�s��
                                        �p�GNON ���ɮ׸��|�M�ɦW,�h�|�NLOG�s��
					���w���ؿ���.

CLEARLOG	NON			�M���ثe���Ҧ�LOG �è�Barcode�MTime�Ӧs
					��

GETTIME		ON/OFF 			��H GETTIME ON�ɨt�η|�}�l�p��,��
					GETTIME OFF�ɷ|�N�䶡���ɶ��s��
					[VARREAL]��GETTIME�ܼƤ��Hms�����

********************************************************************************

UUT �ݥi�Q�� COM PROT �� LAN  �^�ǥH�U�C���_�l�����,�h HOST�|����W�B�z��T

*******************************************************************************
ERROR-CODE:0001				�|�b�D�{�����UUT�ثe���쨺��ERROR ����
ERROR-UUT:0001				�|�N�D�{����ERROR CODE �令 0001

UUT-FAIL				�|�q���D�{�����ե���,���������ʧ@

VARSTRING  ABC = 'TEST DATA'		�|�NClient�ݰe�L�Ӫ� TEST DATA �s�� 
					VAR.INI�� VARSTRING���� ABC��,�]�w��k
					�i�Ѧ� VARSTRING �� COMMAND
VARREAL    ABC = 23			�|�NClient�ݰe�L�Ӫ� 23 �s�� VAR.INI�� 
					VARREAL���� ABC��,�]�w��k�i�Ѧ� 
					VARREAL �� COMMAND

