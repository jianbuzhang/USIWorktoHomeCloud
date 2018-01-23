
***************************************************************************
*                              BARCODE.INI                                *
***************************************************************************

[Logfile]				設定基本測試資料
LOGPATH=D:\SYMBOL\LOG\ 			設定LOCAL 測試資料存放地點
ErrorPos=4                              設定test log file 放error code 的位置
Filename=testlog.txt			設定 test log file name
ProductLine=1				設定 生產線--產線名稱
ErrorVersion=1				設定error code 的版本編號


[host]     設定與SFC的控制設定
port=1024				設定與SFC的通訊PORT
IPAddress=172.25.6.225			設定SFC SERVER IP Address

[control]   設定barcode form的使用及各資料長度的控制
EMP_NOLength=5				設定作業員號碼的長度
BarcodeLength=22			設定Barcode的長度
MACCodeLength=5				設定MACCode的長度
MACCodeUses=OFF				設定是否使用MACCode form
GUIDCodeLength=2			設定GUIDCode的長度
GUIDCodeUses=OFF			設定是否使用GUIDCode form
FCTCAPTION=USI FCT TESTER		設定 FCT CAPTION 顯示字串
FCTEXEName=PUSIGB.exe			設定 FCT 的執行程式名稱

WaitFCTTime=2				設定 SFC Server 回應等待時間,以秒為單位
ShopFlow=OFF				設定是否要使用 SFC 系統

[code]  備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
Barcode=ExitExitExitExitExitEx
MAC=ExitE
GUID=Ex
EMP_NO=ExitE
FixtuerID=EXIT
LINE_NO=0
; NUMBER     BARCODE                  MACCODE             GUID        IPADDRESS/com        PASSDATA   
1=1111111111111111111111,000102510316,11,1,PASS
2=9999999999999999999999,00096b82aaf0,99,2,PASS

[restore] 	備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
Barcode=246011901r01gc012cb01b
MAC=42343
GUID=24
; NUMBER     BARCODE                  MACCODE             GUID
1=1111111111111111111111,000102510316,11
2=9999999999999999999999,00096b82aaf0,99


[VersionPath] 備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
;control version FCTcommand file path



***************************************************************************
*                              COM.INI                                    *
***************************************************************************



[SYMBOL]
SymbolUSB=ON					是否要開啟symbol Multi Load的程式
APPath=D:\ibmbeta\GetWinH\Multi-Flash\MultiLoad.exe	Multi Load程式位置(或 pddeclient.exe的位置)
MCaption=MultiLoad					Multi Load程式的caption



[IMAGE]
Monitor=d:\MC3000\DVT\BSP4.1.002\Hex Images\MC3000C42B\MC30XXC42XMon0115.bin
Partition=d:\MC3000\DVT\BSP4.1.002\Hex Images\MC3000C42B\MC30XXC42BPTbl002.hex
Application=d:\MC3000\DVT\BSP4.1.002\Hex Images\MC3000C42B\MC30XXC42BApp_410.002.hex


之後的section 則為 com command 的名稱,然後依不同的com port 執行不同的命令
例如: runpcexe  myrun 則com 5 會執行c:\windows\notepad.exe
                        cmo 1 會執行C:\WINDOWS\System32\calc.exe




[MYRUN]
1= c:\windows\notepad.exe
2= C:\WINDOWS\System32\calc.exe



***************************************************************************
*                           SYMBOL.INI                                    *
***************************************************************************
設定USB HUB 各PORT依序對應到的是那一個COM Port 以及需要傳輸率,資料讀取的time out 的間隔
[COM] comport          comrate       readIntervalTimeOut
1=     5                 9600                10
2=     1                 9600                10

[USB]
; USB ID Symbol的USB在系統中的編號
1=USB1      (用在COPYDIR時可以改成所指定的磁碟機 例如 F: )
2=USB2
3=USB3
4=USB4


