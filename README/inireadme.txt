***************************************************************************
*                                       GB.INI                            *
***************************************************************************
��b \prod\ �M��\���� �ؿ��U

[SwitchData] �]�w�@�ǰ򥻪����
FCT=NOTEBOOK     	�]�w�M�w�W��,�i�H���]�w
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


NICARD=ON		�]�w�O�_�ϥ�NI CARD, �p�GOFF �h��ⶵ�]�nOFF(GBDIO,SMBCARD)
GBDIO=OFF		�]�w�O�_�ϥ� USI GB board
SMBCARD=OFF		�]�w�O�_�ϥ� USI SMB board (�M HPPOWER ����P�� ON ���M�u���@�շ|���� HP ���|OFF)
HPPOWER=OFF             �]�w�O�_�O�ϥ� HP power supply(OFF��h���յ������|��HP POWER �� RESET�ʧ@)
DMM=OFF                 �]�w�DPOWER�������ϥ�
SMBType=2               �]�w�ϥ�SMB board ������


[BOOT]			�Φb��com port �L�k�ϥ�,�i�ɥ�print port�Ǧ^��dio port�H�D������
A0=C10.BAT		�o��T�Φbnotebook main board(�ثe�v�g���γo�q���)
A1=C10.BAT
A2=C10.BAT
A3=C10.BAT
A4=C10.BAT
waitstring=C:\USI>

[COUNT]			�b�]�w�{�����һݭ���p�ƾ�.
Retest= 5		�]�wretest ���s�u��]�w����5��,�h���F�h�|�۰ʵ����^��barcode 
			form �S���]�wdefault�Ȭ�99��
			
Retry= 3		�]�wretry ���s�u��]�w����3��,�h���F�h�|�۰ʵ����^��barcode 
			form �S���]�wdefault�Ȭ�99��


[POWERRESET]		�i�H�b���[�JUUT COMMAND ,�i�H���ϥΪ̫��U�q���������s�ɷ|������
			��UUT COMMAND,�����|�̸��X�̧ǰ���.
0= 1000			0=1000 ��ܨC��COMMAND���n���j�h�֬�,���]�w�h��1000= 1��
1= COM OFF
2= COM ON
3= COM SEND DATA ....
4= DIO TEST OFF
5= ........




[CONTROL] �]�wNI CARD & GB Board ���]�w��  
DEVICE=2		�]�wNI CARD ��DEVICE �Ȭ���,�q�`�@�i�d��Ȭ�1,
CONTROLPORT=0		�]�wGB BOARD ������PORT�����@��NI ��PORT
ADDRESSPORT=2		�]�wGB BOARD ����m����PORT�����@��NI ��PORT
DATAPORT=3		�]�wGB BOARD ����Ʀs��PORT�����@��NI ��PORT
**CONTROL PORT 0,1 bit ��ܳ]�w���@�� GB Board ��DATA 11--1 10--2 01---3 00---4 
L5V=2			�]�wGB BOARD ������PORT�����@��NI��line ���������GB REALY 5V�q
DAC=3			�]�wGB BOARD ������PORT�����@��NI��line ������DAC enable                   
ACH=4			�]�wGB BOARD ������PORT�����@��NI��line ������ACH enable
RESET=5			�]�wGB BOARD ������PORT�����@��NI��line ������RESET enable
WE=6			�]�wGB BOARD ������PORT�����@��NI��line ������Write enable
RE=7			�]�wGB BOARD ������PORT�����@��NI��line ������Read enable
ADDRESSFIRST=255	�]�wGB BOARD ��address Ū�g�]�w�bGB Board���_�l��m
ADDRESSEND=252		�]�wGB BOARD ��address Ū�g�]�w�bGB Board��������m

�]�wPORT 0~ (255-252+1)*8 ��read-0 or write-1�h�]�wGB BOARD ��READ WRITE���ݩ�
PORT�����Ǭ� 0-1-2-3...-7, 8-9-10-11...-15, .......31 
PORTSET=11111111,11000000,00000011,10111111    


***************************************************************************
*                              BARCODE.INI                                *
***************************************************************************
��b \prod\ �M��\���� �ؿ��U
[ICON]    �i�H�Ψӧ���barcode form��icon�W��,�p�G�S��,default�O���媺
1=RETEST
2=SUBMIT
3=LOGOUT
4=CLOSE
5= ���տ��~				�ΨӦbMulti barcode form���ק靈���տ��~�����ܦr��

11= OFF					����"����"�����s�n���n���,Default �|���.OFF�ɷ|�ݤ���.


[NONUSI]				�D�n�O��NONUSI.EXE �ϥΪ�Section,�䥦AP�i�H�Ψϥ�
APPATH=C:\Desktop\TextDiff.exe  	NON USI AP�����|
					�p�G���ѼƩΪťխn�ϥ� " " �]�_��,�ѼƩM�{�����n�Τ���
					 ; �Ϲj
      					"C:\Program Files\Movie Maker\MOVIEMK.exe ; /a/b/c"

APCAPTION=TextDiff			NON USI AP��Caption �r��
PASSCAPTION=�p��L			NON USI AP PASS Dialog ��Caption �r��
FAILCAPTION=�p��L			NON USI AP Fail Dialog ��Caption �r��
LOGPATH= D:\NONUSI\F0772log.txt		NON USI AP Test log �ɮ׸��|�M�W��	
REPORTPATH=				NON USI AP Test report �ɮ׸��|�M�W��,�S���i����J
MARK=  ,#				NON USI AP Test log ��ưϹj�r��,�i�]�w�h�ӰϹj�r��,�p
					�ݪťխn�Ψ䥦�r���]�b�䤤�� , #

RESULTLOCAT=8				NON USI AP Test log ��ưϹjpass fail��m
ERRORLOCAT=9				NON USI AP Test log ��ưϹjerror code��m
PASSSTRING= Pass			NON USI AP Test log ���PASS����ܦr��


[Logfile]				�]�w�򥻴��ո��
LOGPATH=D:\SYMBOL\LOG\ 			�]�wLOCAL ���ո�Ʀs��a�I
VARLOG= OFF				�]�w�O�_�n��X�ܼƩM�ɶ���LOG,Default��ON
ErrorPos=4                              �]�wtest log file ��error code ����m
Filename=testlog.txt			�]�w test log file name
;����change.ini   ProductLine=1				�]�w �Ͳ��u--���u�W��
ErrorVersion=1				�]�werror code �������s��
UUTStop= END OF TEST HI                 �Φb PUSINet.exe �פ�client�����q�r��,��client�������̾�
AUTO=TRUE                               �i�H��PUSIGB.EXE�۰ʰ���M����,���]TRUE�hDefault ��FALSE,�h���|�۰ʰ���
TESTTYPE=FCT1				�ΨӴ��ѥͲ��u�C�L���ѧO�������O
PRINTCOM=COM5				�Ψӳ]�wCOM PORT ��Printer �Ѩ��� COM Port ��X

;PROJECTNAME= MC909X			�Ψӳ]�wPROJECT���W��,�|����IMAGE �M UUTAP���۰ʤƧ�s�ϥ�,�bSERVER��
					�]�n�άۦP��PROJECT �W�٨ӫإߥؿ�,�~�৹��

[OtherLogfile]
LOGPATH=D:\LOG\VC80\ 			�]�wother LOG ���ո�Ʀs��a�I,�i��O�Ȥ᪺SERVER�s���������w�ХN��
LOGEXEName=D:\Pmotolog.exe		�]�w Other LOG ������{���W��,�ΨӲ��ͫȤ�ҭn�� LOG������

1=ZEBRA_PROCESS : RHCB_FAT		�]�w�n�[�J���r��,�H ZEBRA_ ���}�Y���ܼƦW��, �� : �ᬰ�x�s����.
2=ZEBRA_STATION : RHCB_FAT01		�p�G���h�ӻݭn�T�w��J�����,�̶��ǽs�� 1,2,3,4,5...
3=ZEBRA_FIXTURE : RHCB_FAT01-01


[host]     �]�w�PSFC������]�w
;����change.ini   port=1024				�]�w�PSFC���q�TPORT
;����change.ini   IPAddress=172.25.6.225			�]�wSFC SERVER IP Address
TestPort=4000				�Φb��������TCP/IP ��port�]�wPusinet.exe,�ثe�]�v�[�J��PUSIGB�����i�� 
					LAN ON / OFF �}�ҩ�����


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



 
//�Φb��IMAGE Muti form�����Ŀ� USI configuration �ɷ|���J symbolBOM2.INI��������,�Ӳ��͹�����VAR.INI�������
[Position2]				�Φb�HUSI BARCODE�����ܧ�պA��,�n�qUSI change barcode��START��m������
START=1					LENGTH ���r���ӹ���
LENGTH=2
USIADD2= ON				ON��ܭn�[�J,OFF���Υ[�JUSI���r����¦r����ݥΦb�H
					USI old BARCODE�Ӥ�藍�P�y��Τ��POS����������,�i�H�ΨӤ��s��barcode
					�ҭn��s������,�H��֥Ͳ��ɶ�,
					�N  section USIADD2 �������ҹ�����code �[��[CONFIG2]����

USICHECK=ON				ON��ܭn���USI Configuration ���ﶵ,OFF �h��ܤ��n���USI Configuration
					���ﶵ



[USIADD2]
;�s��     �W��      �_�l��m    �r����	�]�p�n�[��[CONFIG2]�����M[Position2]����CONFIG2= �r��᭱,
1=	  LANG	      3           2	��r�ꪺ�ӷ��O��USI�Ƹ���m���o
2=        USITYPE     5           2
3=        GGYY        7           2


[Config2]
;�s��     �W��      �_�l��m    �r����	�w��nConfig section���ҭn������諸�����Ӱ��W�٪�����,�����W�٭n�Mconfig
1=       VERSION    1           1	�ۦP�~���������,�p�G�ۦP�W�٦�������,�B�ȬۦP�ɷ|�N VAR.INI�����ܼƼW�[
2=       OS         2           1	�@��  �ܼƦW��+'2'= KEEP,�Ҧp OS2= KEEP �H�Q�y�{�P�_�n���n��s,���P��,
					�h���|�W�[����h���ܼ�,�٬O�H��� CONFIG �Ҳ��ͪ��ܼƬ��D





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


FCTCAPTION=USI FCT TESTER		�]�w FCT CAPTION ��ܦr��
FCTEXEName=PUSIGB.exe			�]�w FCT Command ������{���W��
FCTEXEParameters= D:\LOG\PATH\		�]�wFCT EXE ���ݪ��Ѽ�
BarcodeFormname=PBarcodeFM.exe          �]�w barcode form ������{�����W��
CloseAPCaption='USI APP'		�]�w�ҭn������AP ��Caption�W��,�o�ӷ|�b�ϥ�Productver.exe�ɲ��Ͱʧ@
 					�p�G�S���b��project�e�n������AP �h�o�Ӷ��إi�H���γ]�w,�o�Ӱʧ@�|��
					������ AP�ô��Xĵ�i,�n�D���s����PROJECT VERSION SELECT AP
					�Ҧp:�i�]�w�h��caption������ # ���j�} �e��n�['  '�p���~��b�Y���[��
					     �ժ��r��

CloseAPCaption='AEX Sequencer - 1 x 32mb#AEX Sequencer - 2 x 32mb#AEX Sequencer - 4 x 32mb'
					

	

WaitFCTTime=2				�]�w SFC Server �^�����ݮɶ�,�H�����
ShopFlow=OFF				�]�w�O�_�n�ϥ� SFC �t��

RDID1=B65D7763				Check sum �ҥ[���ˬd��,�w��fctcommand.txe
RDID2=1179D371				DIO.INI
RDID3=9ECAAE2C				COM.INI
RDID4=C7A51634				BARCODE.INI


[MultiMAC]				��n��J�h��MAC��,�o�̷|��e N-1�Ӫ����,��N���٬O��b�쥻��[code]
1=22222222				MAC= ����
2=23333333



[MACRange]  ���ϥ�MAC code�ɥi�H����d��ȥH�ѱ��ި�O�_�b�ҵ����d��
CheckMAC= OFF       �]�won off �ӳ]�w�O�_�n���d���,default�M�Ӷ����s�b�ɬOoff
Start=A950A         �]�w�}�l�d���
End=F059F           �]�w��������   
 
                    ��Ȫ����׭n�t�X [control] MACCodeLength=5 ���h�|error



[code]  �ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
Barcode=ExitExitExitExitExitEx
MAC=ExitE
GUID=Ex
EMP_NO=ExitE
;FixtuerID=EXIT
;LINE_NO=0
CONFIG=MC3000-KK0MBBBA200

�h�ӿ�J�����ɩҥΪ��榡
   barcode,MAC code, GUID, SUBID(caption), PASS or fail data
1=1111111111111111111111,11111,11,1,1234
2=9999999999999999999999,99999,99,2,pass

[restore] 	�ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
Barcode=246011901r01gc012cb01b
MAC=42343
GUID=24

[VersionPath] �ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
;control version FCTcommand file path

[RDTEST]    RD �{���ҥΪ����,�ЫO�d���n�R��,��multi- barcode input form �ϥ�
EMP_NO=ExitE



[MAINFORM]   �i�ѵ{������ҭn��ܪ� �DFORM ���e�שM�r�Τj�p
WIDTH= 700
FONT= 10

[MESSAGEFORM] �i�ѵ{������ҭn��ܪ� MESSAGE BOX���j�p�M�e��
WIDTH=280
HEIGHT=100
FONT=16
***************************************************************************
*                              DIO.INI                                    *
***************************************************************************
[KEY]  �ϥ�DIO�s��KEYBOARD ��INPUT �NKEY Matrix �ন16�i���     ��b \prod\ �M��\���� �ؿ��U
A=4A			a��16�i���
B=74

[ALLKEY]		�]�wkeyboard ���ժ�����,�ݰt�X[KEY]�����W��
; SEQUENCE  NAME
0=          A
1=          B
2=          C

[GPIBConfig]     ����GPIB Config������,�i�]�w�h��device ����,�H����h��GPIB���� ConfigID<=5
;name              BoardID   PrimaryAddress   SecondAddress   
PowerSupply=           0            1                0            

[HPPOWERSET]    �]�w POWER SUPPLY ���ѵ��q���M���q�y��
;name            voltage       �q�y      
SET37V=            3.7            3        

[GPIBDATA]      �]�wŪ��GPIB ��������,�éM�᭱��UP~LOW�Ȥ��,�O�_�b�d��,�O�Ǧ^ TRUE,�_�Ǧ^FALSE
                TYPE=1�O�]�wŪ�q�y, =2 �O�]�wŪ�q��  
;type==> VOLATGE=1  Current=2
;name            Type      UP       LOW       
HPCurrent=         2       1.3      -1.3          


[VARRANGE]    �Ψӳ]�w�M VAR.INI����[VARREAL] �����,���X�䤤���ȨөMUP LOW ���O�_�b�d��,���G��W
              �٭n�ۦP COMMAND  �i�Ѧ� readmec.txt���� VARRANGE 
;name               UP       LOW
HPCurrent=          2       1.3     

[COUNTER]	�|�g��NI COUNTERŪ�^���i�M�b�i�����,�ݬO�_�O�b�d��UP~LOW����,�O�Ǧ^TRUE,�_�Ǧ^FALSE
name�i�ۦ�����N�q���W��,CHANEL:�w�q��NI COUNTER�����@�� CHANEL Ū�^,
PORT & LINE �b�ϥ�USI GB board �ɳ]�w�Ѩ��@���X�Rport line Ū�^,
UP~LOW  �]�wŪ�^�Ȫ��d��
SLEEP   �]�w�bUSI GB Board�]�w��,�C�@�ӫ��Oidle �ɶ�

; 0:�߼e,1:�W�v,2:FallingEdge,3:HiPulseWidth,4:LoPulseWidth
;
;ModeWidth= 31;
; name     CHANEL   PORT    Line    UP     LOW      SLEEP     MeasurementType
VGAMODE=      1       3       4      0.4     0.7      1000       1
SPK1=         0       3       4      0.4     0.7      100        1

[DAC]	�|�g��NI DAC �e�X�T�W�v�T���ثe���� sine wave,plus ���W�[�\��i��
name�i�ۦ�����N�q���W��,CHANEL:�w�q��NI DAC�����@�� CHANEL �e�X,
PORT & LINE �b�ϥ�USI GB board �ɳ]�w�Ѩ��@���X�Rport line �e�X,
Wavetype ==> �]�w��X�T�����榡 sine ,plus
SAMPLE RATE==> ���˼�
Frequence==> �]�w�W�v
AMP==>       �q���d��
; name       CHANEL   Port   Line   WaveType    SAMPLE RATE    Frequence   AMP
SINWAVE=     0        3      0      sine        18000          1000         3
SINWAVE1=    0        3      0      sine        2000           10           3
MYPLUS1=     0        3      0      plus        2000           1000         1


[PULSE] �|�g�� NI GPCTR ��X�@���W�v�]�w
name�i�ۦ�����N�q���W��Counter:�w�q��NI GPCTR�����@�� LINE �e�X,6025E�u���G�� 0�M1
PORT & LINE �b�ϥ�USI GB board �ɳ]�w�Ѩ��@���X�Rport line �e�X,
Frequence==> �]�w�W�v
; name      Counter    Port   Line   Frequence 
P200=        0           0     3        200

[DACPOINT]  �|�g��NI DAC �e�X�T�w�q���T��name�i�ۦ�����N�q���W��,CHANEL:�w�q��
NI DAC�����@�� CHANEL �e�X,PORT & LINE �b�ϥ�USI GB board �ɳ]�w�Ѩ��@���X�R
port line �e�X, VOLTAGE==> �e�X�T�w�����@�өw�q��
; name       CHANEL   Port   Line     VOLTAGE
V3P7=        0        3      0         3.9


[SMB]    �]�w SMB Board ����ƭ�,�e���W�٤����,��RD�u�{�v�]�w
SMB ==> (2.5V * 6.09)/255 =0.0597  ��0~255���C�@������ �p�n8V �h�� 8/0.0597=134.0
�G���ƥi�]�� 134 �Y�i�o 8V����X�̦h�u��15.2V, ���٭n�̨������q���̤j�Ȫ�80% 
VDISDegree==> Discharge degree (��q��X)
VCHADegree==> charge degree    (�R�q���e)
SMB ==> (2.5V * 1.4484)/255 =0.0142  ��0~255���C�@������ �p�n3A �h�� 3/0.0142=211
�G���ƥi�]�� 211 �Y�i�o 3A�����q�y,�̤j�e�ǹq�y��3.6A
IDegree==> 
   
;POWER MODE SET
VDISDegree= 0.0597
VDISSub=1.25 (for SMB2�ϥ�,�Y�]�w�q���n���,�A���WDegree�ȱo�춥��)
VCHADegree= 0.0597
IDegree= 0.0142 (�R�q���q�y)
IProtectDegree= 0.0142 (�O�@�q�y)

[ACHWAVE]  Ū��ACH WAVE �����,�h���o�p��p���Ȯt,�ûPUP~LOW�Ȭۤ�b�d�򤺬�TURE�_�h�Ǧ^FALSE
SAMPLE_RATE==> ���˼ƶq        Frequence==>WAVE ���W�v�]�w
CHANEL==> �ϥ�NI CARD�����@��Chanel�Ӷq��.  port,line==> �ϥ�GB Card�ɪ��X�Rport line �����w        

; differential mode set SINGLE=0 , single mode set SINGLE=1
; name       CHANEL   Port   Line   SINGLE   SAMPLE_RATE    Frequence  SLEEP   UP     LOW   
AUDIO=        0        0      1       0         100            2000       50    2       3 



[ACHFREQ] �i�H�P�_ �W�v, offset, �p��p���Ȯt, ���W�v�ŧQ���ഫ���j�p��
  Frequence�̦n���n�q���W�v10���H�W����,���o�֩�G��,�d��b4k�H������,�G���hFrequence�i�]��8k
Frequp , Freqlow ==>�ҭn���q�W�v���W�U����
SubFup , SubFlow ==>���W���ŧQ���ഫ�Ȫ��j�p�d��
Offsetup,Offsetlow==> �Ҷq����offset���W�U����
Vup    , Vlow    ==>�Ҷq�����T���W�U����,��Ȭ��̤j�ȴ�̤p�� 3-(-3)=6 
FilterUP, FilterLow=> �Q�n�����@�ӽd�򤧶����W�v, �䥦���v������. filterUp �n�p�� frequence/2 �_�h���v�i�ɷ|���~
scannumber ==> �M�w�ҭn���˪���Ƽ�,�p�G�M�����W�v�ۦP,�h��T�׳̰�,�_�h�|���@�Ӥ�ȨM�w�~�t�d�� Frequence / scannumber = �~�t�j�p
               scannumber <= 10,000 �A�j���X��,�@�譱�|���ɫܤ[,�@�譱�O����|������,�{���| down ��


; name       CHANEL   Port   Line   Frequence   Frequp     Freqlow   SubFup    SubFlow   Offsetup     Offsetlow     Vup    Vlow  FilterUP   FilterLow   scanNumber
FEI=          0        1      1       2000       1000        800      0.01        0        2.5           0          4.5   3.5       3000       500          2000
   
[ACHV]  �z�LNI CARD��ACH�Ӷq��UUT���q��,�ûPUP~LOW�Ȭۤ�b�d�򤺬�TURE�_�h�Ǧ^FALSE
MULTIPLE==>�z�LGB CARD�i�q���j��10V �H�W���q��,�[�W���ƥi�o���T��,NI CARD�u��q10V�H�����q��
;         CHANNEL   PORT   LINE   SINGLE  SLEEP  UP     LOW   MULTIPLE
MAIN_DC=      8     0      6      1       50     3.6    3.0   1
VCC5=         0     0      1      1       50     5.25   4.75   1


[ACHI]�Q�����t�Ӻ�q�y��,DisCharge-DIFF  Charge-DIFF     DisCharge-SING    Charge-SING�ӳ]�w�U��TPYE�����v  
SW1,SW2,SW3,SW4==>CURRENT sensor

;SW set for read current, the voltage divide resistance value*** DON'T CHANGE NAME
;NAME   resistance   DisCharge-DIFF  Charge-DIFF     DisCharge-SING    Charge-SING   
SW1=    1            1               1                  1               1
SW2=    0.1          -1              -1                 -1              -1
SW3=    100          -1              -1                 -1              -1
SW4=    1000         -1              -1                 -1              -1

�z�LGB CARD& NI CARD�� Channel port,line,single�ӳ]�w���,SW��ϥΨ��@��Current sensor�Ӷq��,DisCharge on off���}��,Trikle�C�R
VD2 �q�����e(�~���q���n�j��q�����e�~���SMB�R�q),VD1��X�q��,current==>�]�w�̤j�R�q�q�y����
ProtectCurrent  ���]�w�̤j��X�q�y,���L�q�y�O�@,���� HP Powre supply protect
;                      CHANNEL   PORT   LINE  SINGLE  SLEEP        UP      LOW     SW     DisCharge  battery   Trikle   VD2   current  VD1  ProtectCurrent             
OperaTionChargeTest1=    7        2      7     0       1000       1       -2.8     SW2      OFF       1         OFF     3.7     0.2    3.5      3


#######################################   �R���F,���A�ϥ�
[RJDATA] �t�X[DIO]�����]�w�Ӧs��DIO���^�ȬO�_���T.
;item    dioname    data
0=       RJSend1    0
1=       RJReceive1 0
2=       RJSend2    0
3=       RJReceive2 0
#######################################    �R���F,���A�ϥ�

[DIO]�]�wDIO��PORT,Start line ,line bit number,
ON,OFF,0,1�O�]�wCOMMAND��ON OFF 0 1��ܪ��N�q
ON=0    
OFF=1
0=ON
1=OFF
;name�i�ۦ�����N�q���W��
PORT �b�ϥ�USI GB board �� NI card�ɳ]�w�Ѩ��@��port �e�X,
STARTLine �]�w�ҩl��line�Y���@��port���ĴX��line�}�l,�i�V��]�w�h�֭�line�YBitnumber,Bitnumber�̦h���i�W�L8
;name          PORT    STARTLine   BITNUMBER
DIOPORT=        0        0            8
PORTA=          2        0            8
PORTB=          3        0            8

[NIDIODIRECT]
; DATA:=1 OUTPUT  DATA:=0 INPUT  
; �p�G  DATA=15  0x00001111  �h Low 4bit is ouput,  up 4bit is input
; SETLINE:=1 LINE SET    O PORT SET  =1�ɪ�ܬO�Hline�ӳ]�w,=0�ɪ�ܬO�H���port�ӳ]�w
; port ��ܭn�]�w��port �����
;name�i�ۦ�����N�q���W��

;NAME        PORT   SETLINE   DATA
PORTDIR0=        0       1       242
PORTDIR2=        2       0       0


[DIOMACRO]
;Name    �W��    sleep �U��dio��Ʃҭn���j���ɶ�,  DATA==>DIO command���զX,��','�����j
DATA�������U�����O�p�P DIO COMMAND �ҤU���ۦP,�����Υ[ DIO�o�Ӧr��,���Ӷ���ƥ��ݦs�b�b
[DIO] Setion ����

POWERON=  1000,PORTA 22,PORTB 33,PORTC 44

[UIMACRO]
NAME ���o��MACRO���I�s�W��,�U�өR�O�� % �Ÿ��j�},�i�H�ϥ� FCTCOMMAND�Ҵ����Ҧ����R�O
�Ҧp:  UIMACRO  POWERON �̫�@�� , ���᪺�Ʀr�� ms �ΨӶ��j�U�R�O��delay time

NAME   DATA
POWERON=  DIO PORTDIR0 22 % ACHV V3P7 % WAIT ABC,2000



[LAB]
;NAME �W��,  L  A B  ���O��LAB������������.
COLOR1 =    220  1   -2




[DIO48DEVICE]   ��DIO48���d�ϥ�,�s���n�q1 �}�l,�p�G���h�i�d�i����  1,2,3
; 1�d���s��     2.�C�@��Port��V 0:write  1:read    3.�ҭn�]�w��l�Ȥ� section name      
; CardID  Port-direction   Initial-name
1=  0       000111            MYDIO48


[MYDIO48]  ��DIO48���ҳ]�w�U�d���ҭn�]�w��l�Ȫ�Section name �ӳ]�wwrite port����l��
;�e����ID-KEY�n��1,2,3...���覡�s�g
;   1.port number    2.��l��
;  portnumber    initial-data
1= 1                    255
2= 2                    211
3= 4                    0





***************************************************************************
*                              VAR.INI                                    *
***************************************************************************
FCTCOMMAND���s�ܼƪ���m   ��b \prod\ �M��\���� �ؿ��U
[VARREAL]

[VARBOOL] //�ثe�S���ϥ�

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

[Control]
SFISBOM = ON    ON��ܭn�qSFIS���oCONFIG DATA, Default �OOFF
***************************************************************************
*                              systemBOM2.INI                              *
***************************************************************************
[config]   ��b \prod\ �M��\systembom.ini  �ؿ�
USIBARCODE  �Ȥ�պA�s��
810001-00=MC3000-KK0MB2BA200

�ΨӳB�z��Ȥ�պA�����ɪ��۰ʹ�����,�ɮרӷ���USI PE
�D�n�@�Φb��X�f�e�n�󴫦U�ت���,���s�U��image�ΥH���٤����n���U���ɶ�,
�n�t�XsystemBOM.INI �M barcode.ini�����]�w 
�p�G���ϥΫh:
1.systemBOM2.INI ���쥻���ծɪ�barcode
2.systemBOM.INI ���n�X�f�ɭn�]��barcode

�Բӳ]�w�� barcode-readme.txt
                              
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

[USB] �ΦbSYMBOL IMAGE �U�������� USB ID
; USB ID 
delay=10
1=6&25e66231&0&5
2=6&25e66231&0&6
3=6&25e66231&0&7
4=6&25e66231&0&8

DEVICEID= 6&25e66231&0&8    �o�ӭȬO�b�]�w��PUSIGB.EXE �I�s�ɨ��N # ���e�ϥ�

[DeviceCheck] �Ψӭp�ƴ��ժO�ϥΦ���
0=1000   �ˬd�O�l���W����,��F�o�ӭȴN�|��ܬ��⪺�r,�åB�|���Xĵ�i����
1=2		�U�O�l�ϥΦ���
2=3
3=3
4=4



[FixtureID]  �Ψӳ]�w�C�@�x�v�㪺ID �����e�� SFIS ���ѧO�ϥ�,�p�G�S���o��Section
             �N�|�H�q���W�ٰ��� ID ��
IDHead= PD3-L1			�i�H�]�w�C�@�x�v��ۦP������,�i�H��ʨƥ��]�w,�]�i�H���ݭn�o��
NumberBox= OFF			�o�ӰѼƥi�H�]�w�O�_�n���XFixtrue ID ���Ǹ���J����,�p�G�bIDHead
				�v�����]���i�H���ΦA�]�w. Default �ȬO ON,�@�w�n��JOFF�r��~�|
				�����.
		 



IDNumber=2349803294		�o�̪��ȷ|��Productver.exe �{���ӭt�d��J,User ���γ]�w



�۩w SECTION & NAME �i�H����FCTCOMMAND �HGETINI COMMAND �Өϥ�GETINI ���T�ӰѼ�
GETINI   SECTION NAME VARNAME    �Ĥ@�ӬOsection �W�٨�: MAC 
                                 �ĤG�ӬO name   ��: 1, 2
                                 �ĤT�ӬO fctcommand ���n�s���ܼƦW��
                                 �ԲӤ��e�i�Ѧ� readmec.txt							
  [MAC]
   1= ABCD12345678
   2= TESTABC
					�p���ڭ̥i�H�NFCTCOMMAND �@�P�Ƥ��ΨC�xPC�n�]�w���P���y�{

[SFIS]
SUBMIT = OFF			��]�w��OFF��,���է��ᤣ�|�۰ʫ�SUBMIT����,��USER�ۤv��.�S�]�w�ɬ�ON



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


[NONUSI]		�D�n�O��NONUSI.EXE �ϥΪ�Section,�䥦AP�i�H���ϥ�
			�Φb���o��error code�MUSI Error code ������
Error #64 =  USI001
Error #65 =  USI002








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
    


***************************************************************************
*                            CHANGE.INI                                   *
***************************************************************************
[Logfile]				�]�w�򥻴��ո��
ProductLine=1				�]�w �Ͳ��u--���u�W��

[host]     �]�w�PSFC������]�w
port=1024				�]�w�PSFC���q�TPORT
IPAddress=172.25.6.225			�]�wSFC SERVER IP Address

[SYMBOL]
PATH = C:\TEMP\SYMBOL.INI    		�s�W����,�i��USER�ۦ�]�wSYMBOL.INI�s�񪺦�m,
					�S�]�w����,�Y�|�s��bUSIPROJECT\PROD\ ��
					���|�n��������|�[�ɦW.


//Version.ini �����L��
�N�|�ܰʪ���Ʃ�b�o��INI ���H�K�b�������ɲ��ͻ~�P,��o���ɮפ��s�b��,�|�����ª��W�h,�H�V�e�ۮe
[number] 
BatchNumber= 123345679 	�p�Gversion����ܬO�z�L��barcode�N�|���ͤ@�Ө̾� start,checklength�ҧ�X�Ӫ��r��
			���ѫ��򲣫~barcode�����,�קK���P�妸���άۦP�ؿ����ժ��O�l�V��,�o�ӵ{���|�۰ʧ@ 


//barcode.ini �����L�Ӫ�
[MultiMAC]				��n��J�h��MAC��,�o�̷|��e N-1�Ӫ����,��N���٬O��b�쥻��[code]
1=22222222				MAC= ����
2=23333333


[code]  �ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
Barcode=ExitExitExitExitExitEx
MAC=ExitE
GUID=Ex
EMP_NO=ExitE
;FixtuerID=EXIT
;LINE_NO=0
CONFIG=MC3000-KK0MBBBA200

�h�ӿ�J�����ɩҥΪ��榡
   barcode,MAC code, FIX, SUBID(caption), PASS or fail data
1=1111111111111111111111,11111,11,1,1234
2=9999999999999999999999,99999,99,2,pass

[restore] 	�ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
Barcode=246011901r01gc012cb01b
MAC=42343
GUID=24

[VersionPath] �ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
;control version FCTcommand file path

[RDTEST]    RD �{���ҥΪ����,�ЫO�d���n�R��,��multi- barcode input form �ϥ�
EMP_NO=ExitE


[ActiveSync]   �p�G���]�w�o��,�h�b�o�{caption���ݪ������s�b��,�|�D���Y�p��(�i�H�]�w�G��)
CAPTION= Windows Mobile �˸m����
CAPTION2= ABCD...