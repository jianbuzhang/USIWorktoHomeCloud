Command         add-data                 discription

COM		dos command    		�g�� com port�e��ƨ� UUT��(�tenter) �p
					�G�n�e�ťզr�i�H�U COM SPACE (�u���@��
					�ťդ��tenter) 
					COM OFF , COM ON �i�}�� COM PORT 
					
					���@��com port ��X�J
			   		COM =  �r���ܼƦW��
					COM ���]�w�bsymbol.ini [COM] ID
					

COMHEX 		ASCII-CODE		�i�g�� COM PORT�e16�i�쪺�r���UUT��.
					COMHEX  313A00  

GETHEX		ON | OFF		�i�g�� COM PORT ���i�Ӫ���ƥH16�i����
					��,����HON OFF �ӱ���
					GETHEX ON ��ܱNCOM PORT����Ƨ�H16�i
						    ��Ȧ��J
					GETHEX OFF ��ܱNCOM PORT����ƥH�r���
						    �����J



MCOM		dos command    		�g�� com port�e��ƨ� UUT��(�tenter) �p
MCOM2					�G�n�e�ťզr�i�H�U MCOM SPACE (�u���@��
					�ťդ��tenter) 
					MCOM OFF , MCOM ON �i�}�� MCOM PORT 
					
					���@��com port ��X�J

			   		MCOM =  �r���ܼƦW��
					
					MCOM ���]�w�bsymbol.ini [COMMON] 


MCOMHEX 	ASCII-CODE		�i�g�� MCOM PORT�e16�i�쪺�r���UUT��.
MCOM2HEX				MCOMHEX  313A00  

								

GETMHEX		ON | OFF		�i�g�� MCOM PORT ���i�Ӫ���ƥH16�i����
GETM2HEX				��,����HON OFF �ӱ���
					GETMHEX ON ��ܱNMCOM PORT����Ƨ�H16�i
						    ��Ȧ��J
					GETMHEX OFF ��ܱNMCOM PORT����ƥH�r���
						    �����J






LAN             dos command    		�g�� lan�e��ƨ� UUT��ON / OFF�Ψӳ]�w
					LAN���}��
					LAN ON     / LAN OFF 
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

				LAN ���]�w�bsymbol.ini [LAN] ID

CLAN             DATA	    	�g�� lan�e��ƨ� SERVER 

  �`�N�s����CLAN ���ݭn�A�U CLAN ON  ,CLAN OFF,�����U�F�Q�n�Ǫ��r��N�n.
  ����Server�^����,�|�۰�����.�e���ɷ|�۰ʶ}�� CLAN

					CLAN  SEND-COMMAND-String
					�]�i�H�� = �᭱���ܼƪ��覡�Ӷǰe
					

				VARSTRING FEI = 'C:\ABC\ABC.EXE '+ BARCODE
					CLAN = FEI  �Φr���ܼƨӰe�Ѽ�

				��SERVER IP PORT�|�MBARCODE FORM�ϥΤ@�P���]�w
				�|�bBARCODE.INI �εۦbCHANGE.INI[HOST]���]�w
				SFIS��IP�MPORT���a�� 

                                

   �d��:
	#-----------------------------------------------#
	#	    Get MC3K ESN Number			#
	#-----------------------------------------------#
	ERRORCODE MC0A >Compare ESN Number with SFIS
	
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
	

	VARSTRING ScanESN = 'GetESN.exe GetESN ' + ESN_SFIS + ' PlanCode 5211'
	COM = ScanESN
	WAIT SUCCESSFUL TEST




ECHO		DATA			�i�NDATA ����r��ܨ� LOG FILE ��; �p�G
					�� ECHO = ABC�������ܼƭ�,���s�b�|��
					�� NON DATA,�p�GMESSAGE ON����,�]�|���
					��䤤�b�r�ꤤ�[ ~ �|�۰ʴ���  
					ECHO ABCD~ABCD


SLEEP		delay-time		delay ms times ==> SLEEP 1000   
					(1000 =  1 second)���@�����


YESNO		data			�]�wmessage box ���ϥΪ̽T�{ YES OR NO,
					��YES�|�e'YES'�� log file�åB�~�����U
					�������O,��NO �|�e'NO'��log file�åB��
					�ܿ��~�X,�������䥦���O,data����ܦr
					��

					YESNO  = ABC �i�������ܼƦr��,���ݦs
					�b VAR.INI����
					�p���s�b�h�|��� ABC: OK


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



@NAME					Label ��jump �ɨϥ�

JUMP		Label			JUMP @123 ����ҼХܪ���m
					�t�~�]�i����r���ܼƫ��ܨ�n������m
					VARSTRING  MYJUMP = @TESTJUMP

					JUMP = MYJUMP
					�o�ӵ��G�|�M
					JUMP @TESTJUMP ���@�άۦP



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
					�i�H�ϥ�()���ݦh�Ӧr��,������] = �M >>

					~ ��or,  & �� and
					���ݦr�꦳ , �ɥi�ΤU�����D�]�w
 					WAIT (crc32,4,),2000  
					�o�ɭԫ᭱�@�w�n
					�]TIME OUT ���ɶ�,����] = �M >>

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
				WAIT 
					WAIT �ᤣ������r��,�hUUT�ǨӪ��r��|��
					�ɫO�s�bBUFFER�����e�X�ӳB�z����U�@�� 
					WAIT waitstring �r�ꪺcommand�X�{�ɤ~�|
					�N���e���r��e�X�ΥH����j�q�ֳt��ƳB
					�z�t�ת����D
                                 WAIT @200       
					�C�@��ɶ����j 0.15��.�p�G�n�ۭq���j�ɶ�
					�i�H�U WAIT @200 ��ܶ��j 0.2��,�b�J��U
					�@���� WAIT�|�_�즨0.15��

				����r��ɷ|���@���r��s�b VARSTRING WAITTEMP��.

                                        
WAITVAR  DATA				�NVARSTRING �����ܼ� DATA�W�٨��X�Ӵ���
					WAIT waitstring,timeout���榡
                                        �Ҧp:
                			VARSTRING DATA = 'ABC >>,2000'
					WAITVAR DATA
					�|�ܦ�:
					WAIT ABC >>,2000
                                       


                                       

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
			doscmd  cmd /c dir/w d:\
			doscmd  f:\battloop.txt

                     DOSCMD D:\USIPROJECT\IMAGE\NCR\Release-0410_TDD\flashall.bat

                                        �t�~�p�G�u�@�ؿ��Ӫ�,���n�]�w�i�H�ϥΤU����
					�k������WORKPATH �A�U�F DOSCMD
					���n�`�N�U���n�ϥήɭn�O�o�N���ܦ��Ū��Ϋ��w
					�s���ؿ�,���M�|�û����b�̫�]�w�� WORKPATH
		   ��:
�쥻
DOSCMD D:\USIPROJECT\IMAGE\WT6000\Fedex_20160530\Eng\fastboot.exe flash bootloader u-boot-imx6q.imx -s 16110523025026                   
�i�H�令
  DOSCMD WORKPATH D:\USIPROJECT\IMAGE\WT6000\Fedex_20160530\Eng\
  DOSCMD fastboot.exe flash bootloader u-boot-imx6q.imx -s 16110523025026
  ���O�ϥ� WORKPATH ����|������]�t "." �_�h�|�X�{���~
  �ϥ� WORKPATH����|�|�@�����V�]�w�����|,����U����אּ�� 
  

DOSCMD2					�i�H�ϥ�DOS �������R�O,�|���o�^����,�Ҧp:
					�䬰�W���귽,�ֳt�^��,�i�`�٤����ɶ�.��l�\��P
					DOSCMD�ۦP.
					�p�^����ƫܦh��ĳ���n�ϥγo�թR�O,�]��W���귽��
					�S��,�䥦��Form�|����.


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




/*					�j�d��mark,��\��Pc++���\��,�ݰt�X */
					�@������

RUNPCEXE	DATA			DATA�������ɦbpc�ݪ����|,�ɮצW��,�p�G
					�ӵ{���v�g�s�b�i�t�XPfindexe.exe�ӧ�{
					���Ӱ���i�קK���ư���
					RUNPCEXE  Pfindexe.exe �n���檺exe ��
					�{����caption
	==>RUNPCEXE  Pfindexe.exe   C:\WINDOWS\system32\calc.exe "�p��L"
	==> RUNPCEXE = ABC    �h�|�� var.ini��r���ܼ�ABC�ӥN�J����
        ==> RUNPCEXE "C:\PROGRAM FILE\ABC B.EXE " �p�G���|���Ů�n��" �]�_��
        ==> RUNPCEXE "C:\PROGRAM FILE\AA.EXE ;/A/B"���Ѽƪ��ܤ]�n�]�_�Өæb��
					�ƫe�[�W�����H���Ϥ�



EXECLOSE	DATA			�Ѧ�ctrl-alt-delete���u�@�޲z��-���ε{�����
					���r��.�]�N�O�u�ݿ�J�����ɪ��ɦW,���Υ[exe


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
		1=ABC
	
		RUNSTR Monitor
		�|���Ͱ���
		Runpcexe D:\HexLoader.exe /u ABC /d 3 \IMAGE\MC3000\30XXc50AenMO0133XX.hex


***********  �U�U�ܼƦW�٫ŧi����ۦP******************************************



VARREAL		DATA			�i�ƥ��ŧi����ܼ�,�ΥΨӰ���ƪ��p��
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
	


					

SUBSTRING    TYPE  NAME  Position Token  �i�NVAR.INI���� VARREAL or VARSTRING��
					�r��I���X�ӦA�s��VAR.INI��
					1.TYPE  = R | S  R:��VARREAL��� 
							 S:��VARSTRING�����
					2.NAME  ��bVAR.INI  VARREAL �ε� 
						VARSTRING���ܼƦW��
					3.Position  ��ܭn�s�����r��Ҧb����m
					4.Token ��ܥγo�Ӧr�����j�r��, ����
						�h���H�ťզr��Ӥ��j,TAB ��H
						\t �Ӫ��

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
      6.SYSTEMBOM.INI
      



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


SaveINIData  Section  name  TYPE  INITYPE	
    ��h�u���\�w��SYMBOL.INI ���s�J���ʧ@,�䥦�����Ʊ榳�s���ʧ@.



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
					
                         
SELECT		data			�]�w select box �� USER ��ܭn�ϥΨ��@
					��,USER ��ܫ�|�̿諸���Ǧs�� VAR.INI 
					����[VARSTRING] ���� SELECT �ܼƤ��n��
					�ܪ����إ� ' , ' �Ӥ��j,�̶��Ƿ|�s�� 
					1,2,3...����
					SELECT  test1,test2,test3 �|���ͤT�ӿ�
					�� test1~3
					



	
					

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



                                          

SAVEBARCODE	NON			�|�s�bVAR.INI���� VARSTRING section��,
					�H�ܼƦW��BARCODE,MAC,GUID���W�٦s�r��
					�ܼ�,�p�G���h��MAC���ѼƦs�b MultiMAC 
					section �|�s��MAC1,MAC2...���ܼƤ�.
					�̫�SCAN�� Mac code �|�bControl��,�䥦
					���|��bMultiMAC ����J�����Ǧs��

					2.2.5.9�����H��|�h�s�@�Өt�Υثe�ɶ�
					�|��bTIMENOW





SAVELOG		NON			�|�N�ثe��LOG ��ƥ���s��,���ε����
					��������~�s��
                                        �p�GNON ���ɮ׸��|�M�ɦW,�h�|�NLOG�s��
					���w���ؿ���.

CLEARLOG	NON			�M���ثe���Ҧ�LOG �è�Barcode�MTime�Ӧs
					��




SAVEVARTXT	TYPE*NAME,...		�i�N�ܼƦs��@���ɮפ���,�i��{�����]�w,
					�b������|�s��bTEST LOG���̫᭱
					 TYPE*NAME, TYPE*NAME,  ......
					
					1.TYPE*NAME, TYPE*NAME,  ......(
						R:��VARREAL��� 
						S:��VARSTRING�����)
					SAVEVARTXT  R*DATA1,S*DATA2,R*DATA3
					
VARREAL TEST = 1
VARREAL TEST2 = 2
VARREAL TEST3 = 3

					SAVEVARTXT TEST,TEST2,TEST3
					SAVEVARTXT R*TEST,R*TEST2,R*TEST3

�|���[�bTEST LOG�᭱:
					TEST  TEST2  TEST3
					1     2      3





FLAG  ON/OFF FLAG-TYPE,TIMEOUT
     �H�U�귽�n�ϥΥ��ݥ��ϥ�FLAG���o�귽��,�~��ϥ�.

      ON  VISA | GPIB | MCOM | USB | MCOM2 ,180000 TIMEOUT�n�j��100  1000��1��
  FLAG ON VISA,timerout
  FLAG OFF VISA


  �b FLAG ON ����,�b FLAG OFF ���e�� FAIL���|�^�� FLAG ON���@�檺ERRORCODE
���s�}�l����,�ݭn�`�N�����]�w,��]�O�n�N�Ҧ��Ϊ��@�θ귽��.


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
                                        7.CONFIG dmm
1. FindResource ���M�䥻���O�_�������i�s�u�� VISA Device,�|�N�ҧ�쪺�귽��� 
		LOG ��,�H�ѧP�_�O�_�n�����򱱨� VISA���ʧ@.

                VISA FindResource

2. RsrcName DATA	���ҧ�쪺 resource �r��]�w,�䬰���wVISA Device �ϥ�
			,Data�n�]�w���ҭn�s����sorce �r��,�@�w�n���]�w����~��
			�ϥ� OPEN CLOSE, WRITE,READ���R�O,���M�L�k�ϥΥH�U�|��
			�R�O

                VISA RsrcName  DATA ��ܥ�VARSTRING����X�W��DATA���r��Ӵ��N



3. OPEN		�����}�ҫ��w���]��,�S�� DATA �Ѽ�
		
		VISA OPEN


4. CLOSE		�������ҫ��w���]��,�S�� DATA �Ѽ�
		
		VISA CLOSE

5. WRITE  DATA	���̾کҥ��}�� Device �ϥΤ�U�U�F����������O
		
		VISA WRITE  *IDN?



6. READ   varName  �ݰt�X WRITE �Ӿާ@,�S��WRITE ���|��READ����ƥiŪ
		  VISA PORT �U�F�n�^�Ǹ�ƪ�COMMAND,�ݵ��ܼưѼƦW�� varName
		  VISA READ ABC �᭱���n�s���ܼƦW��ABC,�|�s�JVARREAL �ܼ�
				��,�ҥH�@�w�n�O��Ƹ�Ʀp�G���O��Ƹ�ƭn�t�X 
				  SAVEWAIT�Ӱ�

		  VISA READ ABC >> �h�|�N��Ƥ]�s��VAR.INI����savevar 
				     section���ܼƸ��,�̫�|�[��
				     testlog.txtvar����,���P�_��� 			

7 CONFIG  DATA			�g�� SYMBOL.INI [VISAConfig] 
			;name    source-name
			DMM= USB0::0x164E::0x0DAD::TW00004773::INSTR   
		        �z�L[VISAConfig] �ӳ]�w PowerSupply��VISA�������]
			��


******************************************************************************************



*********************** GPIB FUNCTION******************************************
GPIB  Command  DATA			�D�n�O�z�LNI VISA�ɭ��ӱ���Ҧ��i��VISA
					�s�����ɭ�,�pCOM ,GPIB,USB...����

                                        Command �Ϥ���
                                        1.RsrcName
  					2.CONFIG 
					3.CLOSE
					4.WRITE
					5.READ
					
1. RsrcName DATA	���ҧ�쪺 resource �r��]�w,�䬰���wGPIB Device �ϥ�
			,Data�n�]�w���ҭn�s����sorce �r��,�@�w�n���]�w����~��
			�ϥ� CLOSE, WRITE,READ���R�O,���M�L�k�ϥΥH�U�|��
			�R�O

                VARSTRING DATA = 'GPIB0::22::INSTR'
                GPIB RsrcName  DATA ��ܥ�VARSTRING����X�W��DATA���r��Ӵ��N


2.CONFIG	data			�g�� SYMBOL.INI [GPIBConfig] address
						;name    PrimaryAddress   
						DMM=        22            
					==>GPIB CONFIG DMM
					�z�LGPIB�ӳ]�w PowerSupply��GPIB�������]
					��


3. CLOSE		�������ҫ��w���]��,�S�� DATA �Ѽ�
		
		GPIB CLOSE

4. WRITE  DATA	���̾کҥ��}�� Device �ϥΤ�U�U�F����������O
		
		GPIB WRITE  *IDN?



5. READ   varName  �ݰt�X WRITE �Ӿާ@,�S��WRITE ���|��READ����ƥiŪ
		  GPIB READ ABC �᭱���n�s���ܼƦW��ABC,�|�s�JVARSTRING �ܼ�
				��
********************************************************************************************	   	

 

STRCOMPARE  VARNAME  DATA		�NDATA �����r��M VARSTRING �����ܼ�VARNAME
					���ݨ�r�ꤤ�O�_���]�tDATA���r��
					�p�GDATA ������Ʀs�b VARNAME��
					�N�|�Ǧ^pass,�_�h���ܷ|�޵oUUT-FAIL
                 VARSTRING MYDATA = '1234'
                 STRCOMPARE MYDATA 'FF12345'
                 �]�i�H�ϥΤG�Ӧr���ܼư����
                 VARSTRING DATA1 = '1234'
                 VARSTRING DATA2 = 'FF1234000'
                 STRCOMPARE DATA1 DATA2

					
					
ANDROID		DATA			���oANDROID ID
                                        �p�G���\��Ʒ|��b VARSTRING AndroidID


ANDROIDCMD      ADB-COMMAND		�Q��ANDROID ID�����oID��,�i�ϥ�ANDROIDCMD
					�|�۰ʦbADB COMMAND�����[�J 
					 -s androidID �� adb command ��,�H��K�ϥ�                             

ANDROIDLOG      LOG-FILE-PATH		���X��ANDROID UUT�^�Ǫ���Ʈ榡
					PASS/FAIL , ERRORCODE, MESSAGE
					FAIL����T�|�t�s�� 
					C:\ANDROID1.BAT or 
					C:\ANDROID2.BAT or
					C:\ANDROID3.BAT or
					C:\ANDROID4.BAT
					���M��O���@��form�s�ɪ�
                                        "C:\ANDROID" + FROMID+ ".BAT"

					�A�� DOSCMD�Ӱ���{��,�զ����e��
					FAIL MESSAGE �s�JBAT FILE��
                                        �åB�bVARSTRING UUTFAIL �]�� TRUE
                                        �p�G����PASS
					VARSTRING UUTFAIL �]�� FAIL
					 

ANDROIDLOGCAT  Wait string $ grep string $ time interval ,timeout

                                        Wait string:�n���ݪ��r��
					grep string:logcat�n���^�L�o���r��
					time interval:���j�h�[���^log �@��
                                        timeout: �h�֬�TIME OUT

ANDROIDLOGCAT  SUCCESSFUL$FMX$2000,20000

SAVEWAIT ON
ANDROIDLOGCAT  SUCCESSFUL = MYTEST $FMX$2000,20000
SAVEWAIT OFF
�|�s�� VARSTRING MYTEST��

savewait on
ANDROIDLOGCAT  voltage = btt $FMX$1000,5000
savewait off
echo = btt

ANDROIDLOGCAT�e�ᤣ�ݭn�ϥ� WAIT �ε� WAIT SUCCESSFUL���|�ۤv��,Time out�|����.
���i�H�[�Jsave wait on �Msave wait off�h�s�Q�n����T.
�����|�Mlogcat -c �����n�ۤv�M��.




<< checkTag << retry times <<  background test
			
					<< myadbdevice << 2 << doscmd adb devices
					�o�ӷ|�N myadbdevice��@�ˬd�r��,
					���~�ɥu����
					2��,
					�ҭn�b�I�����檺command	
					doscmd adb devices

					�]���bcheck list ���|�s��
					myadbdevice$2$errorcode$doscmd adb device
					�@���U�FDUT�^�Ǵ���LOG��.�|�̮榡

					$$$myadbdevice$$$pass | fail


					$LOGEND$  �����Ҧ�LOG�^�ǧ������O��,
					�o�ɷ|�h�ˬdcheck list���٦����ǨS�����է���,
					�|�A�׶i�J�I������.
					�ϥ� WAIT $LOGEND$ ��������.�A�� ANALIST �ˬd�O�_
					����,�S�����h�A�U�F�I������{��,�^��o�Ө� LOG��
					 ERRORCODE���h���s���oLOG 


 SUBSTRING2 S MAC 3 2 = UUTWLANMAC2
 SUBSTRING2 S MAC 5 2 = UUTWLANMAC3
 SUBSTRING2 S MAC 7 2 = UUTWLANMAC4
 SUBSTRING2 S MAC 9 2 = UUTWLANMAC5
 SUBSTRING2 S MAC 11 2 = UUTWLANMAC6
 VARSTRING UUTWIFILOCALMAC = UUTWLANMAC1 + ':' + UUTWLANMAC2 + ':' + UUTWLANMAC3 + ':' + UUTWLANMAC4 + ':' + UUTWLANMAC5 + ':' + UUTWLANMAC6
 ECHO = UUTWIFILOCALMAC
 VARSTRING MCHECKWLANMAC = 'adb -d shell am start -n usi.tdd.androidmutitest/.MainActivity -a WLAN -e ItemName WlanMAC -e ChkMAC ' + UUTWIFILOCALMAC + ' -e LogcatMsg FALSE'
 ECHO = MCHECKWLANMAC
 << WlanMAC << 5 << androidcmd = MCHECKWLANMAC




ANALIST START | END  �����I�����զ^�ǵ��G���P�_
                       START�u�e����COMMAND��RETRY
                       END �e����COMMAND ��RETRY
                       ��LOG���L�{�u�ǰe��BUFFER,���B�z,����CHECKLIST�ɤ~�Τ@�B�z,����$$$�N�e��
			BUFFER ��

ANADUMP     ��X�ثe�s�bBuffer����data

AUTORetry 5


UUT-FAIL

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

					  


GETMHEX		ON | OFF		�i�g�� MCOM PORT ���i�Ӫ���ƥH16�i����
					��,����HON OFF �ӱ���
					GETMHEX ON ��ܱNMCOM PORT����Ƨ�H16�i
						    ��Ȧ��J
					GETMHEX OFF ��ܱNMCOM PORT����ƥH�r���
						    �����J
					�p�G���ɨS������COM FLAG�ҳ]�w��ON OFF
					�S���ĥ�






******************************************************************************


UIMACRO		NAME			�i�ƥ��� DIO.INI���� [UIMACRO] ���w�q��
					�n��COMMAND,�p���i�H²�檺�R�O�ӤU�F,�i
					�Ѧ�
					INIREADME UIMACRO  PORWRON

                                        �p�G�]������D�O���h�Ӧ@�γ]��,�ݭn�ϥΤ��P
					����,�h�i�b UIMACRO���Q��FORMID �өw�q.
                                        �Ҧp:
 
   �o�ӳ����i�H�ŧi�b FCTCOMMAND ��   
   VARSTRING MYPOWERON = '!USB'+ FORMID+'_ON'
   VARSTRING MYPOWEROFF = '!USB'+ FORMID+'_OFF'
   
   �o�ӳ����i�H��b UIMACRO ��                      
   POWERON=  COM = MYPOWERON % ECHO POWER ON % WAIT ABC,2000
   POWEROFF=  COM = MYPOWEROFF % ECHO POWER OFF % WAIT ABC,2000
   


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

