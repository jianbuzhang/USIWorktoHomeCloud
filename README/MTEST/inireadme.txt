***************************************************************************
*                                       GB.INI                            *
***************************************************************************
��b \prod\ �M��\���� �ؿ��U


[COUNT]			�b�]�w�{�����һݭ���p�ƾ�.
Retest= 5		�]�wretest ���s�u��]�w����5��,�h���F�h�|�۰ʵ����^��barcode 
			form �S���]�wdefault�Ȭ�99��
			
Retry= 3		�]�wretry ���s�u��]�w����3��,�h���F�h�|�۰ʵ����^��barcode 
			form �S���]�wdefault�Ȭ�99��


			����4��FORM �ӦU�۰��ۤv��POWER RESET
[POWERRESET]
 �p�G���|�֥[�y���귽�j�W,�i�H�b���]�w�n�M�����R�O,���|�b�Ҧ�����form�^��barcode�ɰ�
��@��,�t�~�b���� MTEST.EXE�ɷ|����@��.�ȷV�ϥ�,�D���n���n�ϥ�.
�Ҧp:
1= WAIT
2= DOSCMD taskkill /F /IM fastboot.exe 
3= WAIT DOSCMD-END,10000
4= WAIT
5= DOSCMD taskkill /F /IM adb.exe 
6= WAIT DOSCMD-END,3000
7= WAIT
8= DOSCMD taskkill /F /IM cmd.exe 
9= WAIT DOSCMD-END,3000


[POWERRESET1]		�i�H�b���[�JUUT COMMAND ,�i�H���ϥΪ̫��U�q���������s�ɷ|������
1=FLAG ON MCOM		��UUT COMMAND,�����|�̸��X�̧ǰ���.�]�w�Mfctcommand �P,�����n
2=ECHO HELLO1		�[�Jerrorcode �����]���n�[�JEND,�@�θ귽�ݥ[�JFlag���o�귽.
3=ECHO HI1              �����D�n��z:
4=FLAG OFF MCOM		��U��form�һݪ�reset�g���U�۪�reset,��reset key�ɷ|�N�o�qcode��
			�N�ثe��fctcommand���e�Ӱ���,�ҥH�Y�l��rtest�]�O��������L��reset
			���e.��error code or pass fail�|�O���즳�� pass fail���|�ܧ�


[POWERRESET2]
1=FLAG ON MCOM
2=ECHO HELLO2
3=ECHO HI2
4=FLAG OFF MCOM


[POWERRESET3]
1=FLAG ON MCOM
2=ECHO HELLO3
3=ECHO HI3
4=FLAG OFF MCOM


[POWERRESET4]
1=FLAG ON MCOM
2=ECHO HELLO 4
3=ECHO HI4
4=FLAG OFF MCOM



***************************************************************************
*                              BARCODE.INI                                *
***************************************************************************
��b \prod\ �M��\���� �ؿ��U

[Position]				�Φb�HUSI BARCODE�����Ȥ᪺�պA��,�n�qUSI BARCODE��START��m������
START=1					LENGTH ���r���ӹ����|��prod\systemBom.ini�����X�Ȥ������config���
LENGTH=9				���������Ʒ|��� [code] CONFIG= MC3000-KK...  ��

USIADD= ON				ON��ܭn�[�J,OFF���Υ[�JUSI���r���Ȥ᪺�r�����
					�Φb�HUSI BARCODE�ӥ[�J���P�y��Τ��POS���������ަp�G�Ȥ᪺BARCODE
					���]�t�y�媩��������,�hUSI�i�ΨӱN�䱱�ޥ[��Ȥ᪺�᭱,�H�QDOWLOAD
					�N  section USIADD �������ҹ�����code �[�� section Config��
					�p�G�v�s�b�h���A�[,�p�G��off�h�|�R���Ӷ�

[USIADD]
;�s��     �W��      �_�l��m    �r����	�]�p�n�[��[CONFIG]�����M[CODE]����CONFIG= �r��᭱
1=	  LANG	      3           2	���O�w��USI�Ƹ���m
2=        USITYPE     5           2
3=        GGYY        7           2

[Config]
;�s��     �W��      �_�l��m    �r����	�պA��BARCOD�C�Ӧr������ܷN�q�|�s��DIO��VARSTRING��
1=       LAN         5           1	�w��[CODE] CONFIG����m
                                        LAN���W�٬��T�w,�ΨӧP�_���S��LAN ���s�b,�p�G�S���n�b�o�Ӧ�m���ȬO'0'
					�p�G����0�h�|���}�n�DUSER ���� MAC CODE,�n�����o�ӥ\��NLAN ���O���W�r
					�Y�i

2=       WAN         6           1	�o�̪� �_�l��m ���ഫ���Ȥ�Barcode�ҹ����Ȥ�Barcode���_�l��m,�Ӥ��O
3=       TYPE        8           1	USI Barcode��������m,����ο�
4=       SCANNER     9           1
5=       WANCARRIER  10          1




[control]   �]�wbarcode form���ϥΤΦU��ƪ��ת�����
EMP_NOLength=5				�]�w�@�~�����X������
BarcodeLength=22			�]�wBarcode������
SendBarcodeOnly=ON			�]�w�u��Barcode��shop flow server���ަ��S��MAC ��������
MACCodeLength=5				�]�wMACCode������
MACCodeUses=OFF				�]�w�O�_�ϥ�MACCode form
MACHead=ABCD                            �]�w��MACCode�����פ���12�X��,�e��SFIC�e�ݭn�ɪ���,�G�̪��ץ[�_�ӭn��n12�r��
MultiMAC=3				��P�@���O�l���h��MAC Code�n��J��,�i�H�b�o�̳]�w�n�h�֭�MAC�n�[�J,
   					�e�����|���[MultiMAC],�̫�@���٬O��b��Ӫ�[code]MAC= ����

GUIDCodeLength=2			�]�wGUIDCode������,�����ȥi��J���N���ת��r��,�߭n�[enter, �~��A���U�]

GUIDCodeUses=OFF			�]�w�O�_�ϥ�GUIDCode form
GUIDSaveTO= 2				�]�w�o�����n�s�񪺦�m,  �S���o������Default�O�Q��GUID�e					
						2: ��ܩҰe����Ƭ� GUID data 
						3: ��ܩҰe����Ƭ� SSN data
						4: ��ܩҰe����Ƭ� SN2 data 
						5: ��ܩҰe����Ƭ� MO_NUMBER data




CONFIGLength=18				�]�w�Ȥ�պA��bar code ����,�|��prod\systemBOM.INI��ŪUSI PN �۹����Ȥ᪺��ƪ���
					���X����|�s�b barcode.ini ��[code] CONFIG �H�ѵ{���P�_�ϥ�.



CONFIG=ON				�]�w�O�_�n�ϥΫȤᤣ�P�պA�ҭn�������{��

	

BarcodeFormname=MTest.exe

ShopFlow=OFF				�]�w�O�_�n�ϥ� SFC �t��

RDID1=B65D7763				Check sum �ҥ[���ˬd��,�w��fctcommand.txe
RDID2=1179D371				DIO.INI
RDID3=9ECAAE2C				COM.INI
RDID4=C7A51634				BARCODE.INI

Version=00-00-00-00

***************************************************************************
*                              DIO.INI                                    *
***************************************************************************

[VARRANGE]    �Ψӳ]�w�M VAR.INI����[VARREAL] �����,���X�䤤���ȨөMUP LOW ���O�_�b�d��,���G��W
              �٭n�ۦP COMMAND  �i�Ѧ� readmec.txt���� VARRANGE 
;name               UP       LOW
HPCurrent=          2       1.3     


[UIMACRO1]
NAME ���o��MACRO���I�s�W��,�U�өR�O�� % �Ÿ��j�},�i�H�ϥ� FCTCOMMAND�Ҵ����Ҧ����R�O
�U��FORM �n�ϥΪ����e�O�����ۤv��[UIMACRO1] [UIMACRO2] [UIMACRO3] [UIMACRO4]
�Ҧp:  UIMACRO  MYSTRING �o�˦b FCT COMMAND�i�H�ϥΦP�@�� UIMACRO �W��,�����e
�i�H���P


[UIMACRO1]
IFTEST=  @a % VARREAL ABC = ABC + 1 % YESNO LOOP % IF ABC > 10 THEN @END ELSE @a123 4
MYSTRING = VARSTRING ABC = 'HELLO1'  % YESNO MYMACRO % ECHO = ABC % YESNO = FORMID

[UIMACRO2]
IFTEST=  @a % VARREAL ABC = ABC + 1 % YESNO LOOP % IF ABC > 10 THEN @END ELSE @a123 4
MYSTRING = VARSTRING ABC = 'HELLO2'  % YESNO MYMACRO % ECHO = ABC % YESNO = FORMID

[UIMACRO3]
IFTEST=  @a % VARREAL ABC = ABC + 1 % YESNO LOOP % IF ABC > 10 THEN @END ELSE @a123 4
MYSTRING = VARSTRING ABC = 'HELLO3'  % YESNO MYMACRO % ECHO = ABC % YESNO = FORMID

[UIMACRO4]
IFTEST=  @a % VARREAL ABC = ABC + 1 % YESNO LOOP % IF ABC > 10 THEN @END ELSE @a123 4
MYSTRING = VARSTRING ABC = 'HELLO4'  % YESNO MYMACRO % ECHO = ABC % YESNO = FORMID






***************************************************************************
*                              VAR.INI                                    *
***************************************************************************
FCTCOMMAND���s�ܼƪ���m   ��b \prod\ �M��\���� �ؿ��U
[VARREAL]


[VARSTRING]

[SAVEVAR]//��command�����ϥ� >> �ɷ|�N�ܼƭȦs���o,�̫�@�@������X�ҭn���ܼƭ�
	 ��K��ƻ`���M�έp
0=ITEM1 11.0000
1=ITEM2 12.0000

[ERROR] �s�񥢱Ѫ���ƶ��X,�H�K�b���~�ɴ��ѩҦ����~��LIST(�b���Ʊ���դ��_�ɨϥ�)
	CS-RP �Ŀ�ᰣ�F�q�t�������|����q�L�@�몺���~�i�H�~�����

[ERRORDATA] �s�����q�t���~�s�񪺭�

[SAVETIME] �s��C�@�Ӵ������ծɶ�
0=20:55:18
1=20:55:20
2=20:55:20
3=20:55:25

[RETRY]  �s��C�@�Ӵ��������F�h�֦�
CM002=14
SD005=8
USB13=8

***************************************************************************
*                              Version.INI                                *
***************************************************************************
��ini file �ݩ�b�U��project���ؿ��U,���n��J�Uproject�������ؿ��ح��h   ��b \prod\ �M��\ �ؿ��U
[number]
BarCodeNumber= 22  	 �]�wBARCODE������
CheckLength= 9      	�]�w�Φh�֭Ӧr���ӧP�_������T
START=1		    	�qUSI BARCODE��START��m��CheckLength���רӤ��
BatchNumber= 123345679 	�p�Gversion����ܬO�z�L��barcode�N�|���ͤ@�Ө̾� start,checklength�ҧ�X�Ӫ��r��
			���ѫ��򲣫~barcode�����,�קK���P�妸���άۦP�ؿ����ժ��O�l�V��,�o�ӵ{���|�۰ʧ@ 

[barcode]
barcode  �ھڤW��CheckLength�Ӥ��barcode�����
QC �O�Ϥ��OQC�����թε۬O���u������
PATHNAME �O�U��PROJECT���l�ؿ��W��
Explain ��r�y�z�o�ӥؿ����������

;    barcode        QC        PathName                        Explain 
1=   246102401       N         Ver2.01                         8100VER3.0
�����᭱�n���ť�,�����TAB ��ӪŮ�,��Ʈ榡�|���~

***************************************************************************
*                              product.txt                                *
***************************************************************************
�Ĥ@��O�y�z���~�Ҧb��m:  �b����ؿ��U
D:\ibmbeta\usi\usiGBTool\prod\Apollo\v1.1\
�ĤG��O�y�z�O�_��QC�ϥΪ��� �O�� Y  ���O�� N
Y




***************************************************************************
*                              systemBOM.INI                              *
***************************************************************************
[config]   ��b \prod\ �M��\systembom.ini  �ؿ�
USIBARCODE  �Ȥ�պA�s��
810001-00=MC3000-KK0MB2BA200

�ΨӳB�z��Ȥ�պA�����ɪ��۰ʹ�����,�ɮרӷ���USI PE
�]�i�H�Ψӳ]�wbarcode or guid����Ʃҭn���o���ؿ����,�i�ɥ�GETSYSTEMBOM
  FCT Command�Ө��o.���o��|��� var.ini ���� VARSTRING section����ID
MYBOM ��
�ثe���ϥΪ��O�b�]�w���P��ID �|���o���P�����|���

                              
[control]
RDID6=66B10494  Check Sum�Ҽg�Jsystembo.ini����
SFISBOM=ON	�ϥ�SFIS �Ҵ��Ѫ� BOM �Ӥ��ϥΦۨ��w�q��BOM


***************************************************************************
*                              Symbol.ini                                 *
***************************************************************************
[COM] �Φb�h��COM PORT �������{��  ��b \prod\  �ؿ��U
;   comport          comrate       readIntervalTimeOut
1=     29               38400                10
2=     4               38400                10
3=     17                115200               50
4=     18                115200               50

COMENTER= 0D0A		�o�ӿﶵ�b��COM PORT�M�w�e�X�r���n�U��r�ꬰ����,��o�ӿﶵ���s�b��
			�зǪ�COM PORT�|�b�����[�W0D0A ,�ثe�o�ӳ]�w��ܦbCOM PORT�e�X�r���
			�u�[�W 0D �o��16�i�쪺�r��,�r���@�w�n�O�����,���i�H�u�U A0D �o�˷|��
			�Ϳ��~ 
IgnoreNullChar= ON	���]�w�h��ON,�i�]�� OFF�|���������ťզr�����\��
RtsControl=ON		���]�w�h��ON RTS control Enable�\��,�]�� OFF�|disable RTS Control����\��
DataSwitch=1            �]�w��Xlog �����j,�̤j���n�W�L 100,default = 1;

[LAN]
;  lan port
1=4000
2=4002
3=4003
4=4004




[USB] �ΦbRUNSTR ��COM.INI����# �������N�r��
; USB ID 
delay=10
1=6&25e66231&0&5
2=6&25e66231&0&6
3=6&25e66231&0&7
4=6&25e66231&0&8



[COMMON]
COMRate=38400		�]�wCOM PORT ���ǿ�v	
COMPORT=COM1		�]�w�ϥΨ��@��COM PORT ,COM1  COM2 COM3
ReadIntervalTimeOut=100 �]�wCOM PORT �r�M�r�����ǰe��timeout �ɶ�

COMENTER= 0D		�o�ӿﶵ�b��COM PORT�M�w�e�X�r���n�U��r�ꬰ����,��o�ӿﶵ���s�b��
			�зǪ�COM PORT�|�b�����[�W0D0A ,�ثe�o�ӳ]�w��ܦbCOM PORT�e�X�r���
			�u�[�W 0D �o��16�i�쪺�r��,�r���@�w�n�O�����,���i�H�u�U A0D �o�˷|��
			�Ϳ��~ 


;Com port �䥦�T���]�w�ﶵ,�S���]�w�ɨϥ�8,1,None �u�Φb�Ĥ@��Com port,�ĤG�Ӥ��|�Q�U���]�w�v�T

ByteSize= 8		�]�w�ǿ�bit ��,���]�w�h��8, �i�]��5,6,7,8���N��
StopBits= 1		�]�wstop bit����,���]�w�h��1,�i�]��1,1_5,2
Parity= None		���]�w�h��None,�i�]�� None, Odd, Even, Mark, Space
IgnoreNullChar= ON	���]�w�h��ON,�i�]�� OFF�|���������ťզr�����\��
RtsControl=ON		���]�w�h��ON RTS control Enable�\��,�]�� OFF�|disable RTS Control����\��

[COMMON2]
COMRate=38400		�]�wCOM PORT ���ǿ�v	
COMPORT=COM2		�]�w�ϥΨ��@��COM PORT ,COM1  COM2 COM3
ReadIntervalTimeOut=100 �]�wCOM PORT �r�M�r�����ǰe��timeout �ɶ�

COMENTER= 0D		�o�ӿﶵ�b��COM PORT�M�w�e�X�r���n�U��r�ꬰ����,��o�ӿﶵ���s�b��
			�зǪ�COM PORT�|�b�����[�W0D0A ,�ثe�o�ӳ]�w��ܦbCOM PORT�e�X�r���
			�u�[�W 0D �o��16�i�쪺�r��,�r���@�w�n�O�����,���i�H�u�U A0D �o�˷|��
			�Ϳ��~ 


;Com port �䥦�T���]�w�ﶵ,�S���]�w�ɨϥ�8,1,None �u�Φb�Ĥ@��Com port,�ĤG�Ӥ��|�Q�U���]�w�v�T

ByteSize= 8		�]�w�ǿ�bit ��,���]�w�h��8, �i�]��5,6,7,8���N��
StopBits= 1		�]�wstop bit����,���]�w�h��1,�i�]��1,1_5,2
Parity= None		���]�w�h��None,�i�]�� None, Odd, Even, Mark, Space
IgnoreNullChar= ON	���]�w�h��ON,�i�]�� OFF�|���������ťզr�����\��
RtsControl=ON		���]�w�h��ON RTS control Enable�\��,�]�� OFF�|disable RTS Control����\��


[GPIBConfig]
;name    PrimaryAddress   
DMM=        22               


[VISAConfig]
;name    source-name
DMM= USB0::0x164E::0x0DAD::TW00004773::INSTR   


[FixtureID]  �Ψӳ]�w�C�@�x�v�㪺ID �����e�� SFIS ���ѧO�ϥ�,�p�G�S���o��Section
             �N�|�H�q���W�ٰ��� ID ��
IDHead= PD3-L1			�i�H�]�w�C�@�x�v��ۦP������,�i�H��ʨƥ��]�w,�]�i�H���ݭn�o��

IDNumber=2349803294		�o�̪��ȷ|��Productver.exe �{���ӭt�d��J,User ���γ]�w

 NUMBERBOX=OFF				
 
[SFIS]
SUBMIT = OFF			��]�w��OFF��,���է��ᤣ�|�۰ʫ�SUBMIT����,��USER�ۤv��.�S�]�w�ɬ�OFF


[FORM]
SHOW = 0

***************************************************************************
*                              SCAN.ini                                   *
***************************************************************************
[SCANCOM]
SCANCOM = COM18			�Ψӳ]�w�۰�SCAN BARCODE���ɮ�



***************************************************************************
*                              COM.INI                                    *
***************************************************************************
��b \prod\ �M��\���� �ؿ��U



[SYMBOL]
SymbolUSB=ON					�O�_�n�}��symbol Multi Load���{��
APPath=D:\ibmbeta\GetWinH\Multi-Flash\MultiLoad.exe	Multi Load or Hexloader���{����m
MCaption=MultiLoad					Multi Load�{����caption



[IMAGE]  �U��IMAGE ����m �t�XSYMBOL���N���n��ҭn��COMMAND �ӳ]�w���m
         �b�R�O���p�G���J # ���h�|��Muti form���s���Nsymbol.ini����[USB]���۹�
	�������X�N�J, �p form1 �|�ɤJ 1= ����,form2 �|�ɤJ 2= ����
Monitor= /u # /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XMon00.21.hex
Partition= /u # /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XPTbl440001.hex
Application= /u 0 /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XApp440004.hex

Platform1= /u 0 /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XPlat440284.hex
Platform2= /u 0 /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XPlat440384.hex
Platform3= /u 0 /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XPlat440484.hex

Splash1= /u 0 /d 3 "d:\MC3000\DVT\BBSP4.4.004"\30XXc42XSplC001.hex
Splash2= /u 0 /d 3 "d:\MC3000\DVT\BBSP4.4.004"\30XXc42XSplM001.hex



***************************************************************************
*                            CHANGE.INI                                   *
***************************************************************************


[Logfile]				�]�w�򥻴��ո��
LOGPATH=d:\D7800\D7800-SYS-IMAGE\
Filename=testlog.txt
ProductLine=D7800			�]�w �Ͳ��u--���u�W��
ErrorVersion=1



[host]     �]�w�PSFC������]�w
port=1024				�]�w�PSFC���q�TPORT
IPAddress=172.25.6.225			�]�wSFC SERVER IP Address
TimeOutSec= 180				�]�w SFC Server �^�����ݮɶ�,�H�����


[MULTIMAC]	��n��J�h��MAC��,�o�̷|��e N-1�Ӫ����,��N���٬O��b�쥻��[code]
MACNumber=3
1=111111111111,122222222222,133333333333				
2=211111111111,222222222222,233333333333
3=311111111111,322222222222,333333333333
4=333333333333,222222222222

[MACRange]
CheckMAC= OFF       
Start=A950A         
End=F059F  
MACHead=ABCD

//Version.ini �����L��
�N�|�ܰʪ���Ʃ�b�o��INI ���H�K�b�������ɲ��ͻ~�P,��o���ɮפ��s�b��,�|�����ª��W�h,�H�V�e�ۮe
[number] 
BatchNumber= 123345679 	�p�Gversion����ܬO�z�L��barcode�N�|���ͤ@�Ө̾� start,checklength�ҧ�X�Ӫ��r��
			���ѫ��򲣫~barcode�����,�קK���P�妸���άۦP�ؿ����ժ��O�l�V��,�o�ӵ{���|�۰ʧ@ 




[code]  �ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
; barcode,MAC code, GUID, SSN,GUID,SN2,MO
EMP_NO=1234567
1=1111111111111111111111,111111111111,11,SSN,SN2,MO
2=22222,333333333333
3=22222,333333333333
4=22222,111111111111

[SUBMIT]
1=1234
2=PASS
3=1234
4=PASS

[CONFIG]
1=7800LWQ-GC211XE,7800LWQ-GC211XE
2=7800LWQ-GC211XE,7800LWQ-GC211XE
3=7800LWQ-GC211XE,7800LWQ-GC211XE
4=7800LWQ-GC211XE,7800LWQ-GC211XE


[restore] 	�ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
1=1111111111111111111111,111111111111,11
2=22222,333333333333
3=22222,333333333333
4=22222,111111111111
CONFIG1=7800LWQ-GC211XE,7800LWQ-GC211XE
CONFIG2=7800LWQ-GC211XE,7800LWQ-GC211XE
CONFIG3=7800LWQ-GC211XE,7800LWQ-GC211XE
CONFIG4=7800LWQ-GC211XE,7800LWQ-GC211XE

[VersionPath] �ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
;control version FCTcommand file path

[RDTEST]    RD �{���ҥΪ����,�ЫO�d���n�R��,��multi- barcode input form �ϥ�
EMP_NO=ExitE

[SYMBOL]
PATH = C:\TEMP\SYMBOL.INI    		�s�W����,�i��USER�ۦ�]�wSYMBOL.INI�s�񪺦�m,
					�S�]�w����,�Y�|�s��bUSIPROJECT\PROD\ ��
					���|�n��������|�[�ɦW.



***************************************************************************

                           �۰ʤƧ�s

***************************************************************************
*                           SERVER.INI                                    *
***************************************************************************
��b C:\USI\ �ؿ��U   �Ψӳs�u��۰ʧ�s��server �Q�� productver.exe����ɰ���
�s�ʧ@

[Server]
 ServerID=  \\W13-2\USIPROJECT ,  \\127.25.1.46\USIPROJECT   ;�]�wSERVER���ɸ��|
 USERNAME= AAA      ;�n�J���ɥؿ����ϥΪ̦W��
 PASSWORD=  12345   ;�n�J���ɥؿ����ϥΪ̱K�X
 INIPATH= UPDATE\PROJECT   ;�ΨӤ��INI file �O�_�O�̷s�����,�M�שҨϥΪ�INI ���| 
 UPDATE= ON / OFF   ;�M�w�O�_�n�s�W SERVER�h��s���

 LogServer= \\172.11.13.88\SYSLOG  �i�H���wLOG SERVER���|,���o�Ӹ��|���ݦs�b,�ϥΪ�
                                   �K�X�O�T�w,�|�s���� U:
                                   ���s�b�o��KEY�ȮɴN���|�]�w
                                   �s�b�ɥi�N���ժ�log ���V  U:\

***************************************************************************
*                            UPDATE.INI                                   *
***************************************************************************
��b C:\USI\ �ؿ��U   �ΨӨM�w�b��ɤU����ؿ����ɮ� �Q�� productver.exe����ɰ���
�s�ʧ@
���|�W�h:
     1.�e�ᤣ�ݭn�[ \ 
     2.server.ini��serverID�Y��Source�Ҧb�ؿ�
     3.*.* ��ܥu�ƻs�����ؿ�,���t�l�ؿ�
     4. +��H�ҿ� project�W�٨��N,�����i�Φb FolderBulid �M StartCheck
     5. #��H�ҿ諸 version�W�٨��N,�u��Φb VersionCheck��
     6.�U�ؿ���Ƨ�s���Ӷ���Ʒ|�̧󪺥ؿ���b c:\USI �ؿ��U,�̦~���Ϥ�
     7. �p�G�n�ƻs�줣�P���ؿ�, �h�� ; ���j�}�æb�����᭱���w�ҳ]�����ؿ�
          1= PROD\PROJECT  ; D:\MYFOLDER\ 

   [FolderBulid] �u�b�إߪťؿ�(�t�l�ؿ�) �|�b�{�}�Үɰ���
    1= PROD\ PROJECT        ;C:\USI\PROD\PROJECT  �|�w�藍�P�ؿ��إߤl�ؿ�         
    2= PROD\ PROJECT2
    3=IMAGE\PROJECT
    4=CPLD\PROJECT
    5=UUTAP\PROJECT
	:
     
   [StartCheck] �̫ᬰ*.*�h�������ؿ����]�t�l�ؿ� (���b�S���project���e�ҭn���窺�ؿ�)
		�|�b�{�}�Үɰ���(�̻ݭn�ӳ]�w) 
    1=*.*
    2= JTAG\*.* ; D:\JTAG\JTAG.BOARD
   [ProjectCheck] �̫ᬰ*.*�h�������ؿ����]�t�l�ؿ�,�p�G��+��,�h�H�ҿ諸PROJECT �W�٨��N,project ���i�ϥ�version�����N�Ÿ� #

    1= PROD\ PROJECT                  
    2= PROD\ +
    3=IMAGE\*.*
    4= JTAG\+ ;D:\JTAG\JTAG.BOARD\+
    5= JTAG\+\INI\*.* ;C:\Bst32\aexman     �D�n�b�ƻsaexman.ini����� 

   [VersionCheck] �̫ᬰ*.*�h�������ؿ����]�t�l�ؿ�(���b���Version��ҭn���窺�ؿ�) �p�G��#��,�h�H�ҿ諸version 
                  �W�٨��N,�p�G��+��,�h�H�ҿ諸PROJECT �W�٨��N,��project�����N�Ÿ��@�w�n�t�Xversion�����N�Ÿ�,�]
                  ���Uproject���������w��version�s�b,

    1=*.*
    2=PROD \PROJECT          PROD\+\#
    3=PROD\ PROJECT2\TEST
    4=IMAGE\PROJECT
    5= JTAG\+\#  ; D:\JTAG\AEXMANGER\+\#
    


