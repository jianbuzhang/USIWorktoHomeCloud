
***************************************************************************
*                              BARCODE.INI                                *
***************************************************************************

[Logfile]				�]�w�򥻴��ո��
LOGPATH=D:\SYMBOL\LOG\ 			�]�wLOCAL ���ո�Ʀs��a�I
ErrorPos=4                              �]�wtest log file ��error code ����m
Filename=testlog.txt			�]�w test log file name
ProductLine=1				�]�w �Ͳ��u--���u�W��
ErrorVersion=1				�]�werror code �������s��


[host]     �]�w�PSFC������]�w
port=1024				�]�w�PSFC���q�TPORT
IPAddress=172.25.6.225			�]�wSFC SERVER IP Address

[control]   �]�wbarcode form���ϥΤΦU��ƪ��ת�����
EMP_NOLength=5				�]�w�@�~�����X������
BarcodeLength=22			�]�wBarcode������
MACCodeLength=5				�]�wMACCode������
MACCodeUses=OFF				�]�w�O�_�ϥ�MACCode form
GUIDCodeLength=2			�]�wGUIDCode������
GUIDCodeUses=OFF			�]�w�O�_�ϥ�GUIDCode form
FCTCAPTION=USI FCT TESTER		�]�w FCT CAPTION ��ܦr��
FCTEXEName=PUSIGB.exe			�]�w FCT ������{���W��

WaitFCTTime=2				�]�w SFC Server �^�����ݮɶ�,�H�����
ShopFlow=OFF				�]�w�O�_�n�ϥ� SFC �t��

[code]  �ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
Barcode=ExitExitExitExitExitEx
MAC=ExitE
GUID=Ex
EMP_NO=ExitE
FixtuerID=EXIT
LINE_NO=0
; NUMBER     BARCODE                  MACCODE             GUID        IPADDRESS/com        PASSDATA   
1=1111111111111111111111,000102510316,11,1,PASS
2=9999999999999999999999,00096b82aaf0,99,2,PASS

[restore] 	�ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
Barcode=246011901r01gc012cb01b
MAC=42343
GUID=24
; NUMBER     BARCODE                  MACCODE             GUID
1=1111111111111111111111,000102510316,11
2=9999999999999999999999,00096b82aaf0,99


[VersionPath] �ƥ��ثe���b���檺UUT���,���{������ϥ�,�ϥΪ̤��Χ��,�]����R��
;control version FCTcommand file path



***************************************************************************
*                              COM.INI                                    *
***************************************************************************



[SYMBOL]
SymbolUSB=ON					�O�_�n�}��symbol Multi Load���{��
APPath=D:\ibmbeta\GetWinH\Multi-Flash\MultiLoad.exe	Multi Load�{����m(�� pddeclient.exe����m)
MCaption=MultiLoad					Multi Load�{����caption



[IMAGE]
Monitor=d:\MC3000\DVT\BSP4.1.002\Hex Images\MC3000C42B\MC30XXC42XMon0115.bin
Partition=d:\MC3000\DVT\BSP4.1.002\Hex Images\MC3000C42B\MC30XXC42BPTbl002.hex
Application=d:\MC3000\DVT\BSP4.1.002\Hex Images\MC3000C42B\MC30XXC42BApp_410.002.hex


���᪺section �h�� com command ���W��,�M��̤��P��com port ���椣�P���R�O
�Ҧp: runpcexe  myrun �hcom 5 �|����c:\windows\notepad.exe
                        cmo 1 �|����C:\WINDOWS\System32\calc.exe




[MYRUN]
1= c:\windows\notepad.exe
2= C:\WINDOWS\System32\calc.exe



***************************************************************************
*                           SYMBOL.INI                                    *
***************************************************************************
�]�wUSB HUB �UPORT�̧ǹ����쪺�O���@��COM Port �H�λݭn�ǿ�v,���Ū����time out �����j
[COM] comport          comrate       readIntervalTimeOut
1=     5                 9600                10
2=     1                 9600                10

[USB]
; USB ID Symbol��USB�b�t�Τ����s��
1=USB1      (�ΦbCOPYDIR�ɥi�H�令�ҫ��w���Ϻо� �Ҧp F: )
2=USB2
3=USB3
4=USB4


