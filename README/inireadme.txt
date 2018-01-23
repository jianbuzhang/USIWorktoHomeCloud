***************************************************************************
*                                       GB.INI                            *
***************************************************************************
放在 \prod\ 專案\版本 目錄下

[SwitchData] 設定一些基本的資料
FCT=NOTEBOOK     	設定專安名稱,可以不設定
COMRate=38400		設定COM PORT 的傳輸率	
COMPORT=COM1		設定使用那一個COM PORT ,COM1  COM2 COM3
ReadIntervalTimeOut=100 設定COM PORT 字和字之間傳送的timeout 時間

COMENTER= 0D		這個選項在為COM PORT決定送出字串後要下何字串為結尾,當這個選項不存在時
			標準的COM PORT會在結尾加上0D0A ,目前這個設定表示在COM PORT送出字串時
			只加上 0D 這個16進位的字元,字元一定要是偶位數,不可以只下 A0D 這樣會產
			生錯誤 


;Com port 其它三項設定選項,沒有設定時使用8,1,None 只用在第一個Com port,第二個不會被下面設定影響

ByteSize= 8		設定傳輸bit 數,不設定則為8, 可設成5,6,7,8任意數
StopBits= 1		設定stop bit種類,不設定則為1,可設成1,1_5,2
Parity= None		不設定則為None,可設成 None, Odd, Even, Mark, Space
IgnoreNullChar= ON	不設定則為ON,可設成 OFF會取消忽略空白字元的功能
RtsControl=ON		不設定則為ON RTS control Enable功能,設成 OFF會disable RTS Control控制功能


NICARD=ON		設定是否使用NI CARD, 如果OFF 則後兩項也要OFF(GBDIO,SMBCARD)
GBDIO=OFF		設定是否使用 USI GB board
SMBCARD=OFF		設定是否使用 USI SMB board (和 HPPOWER 不能同時 ON 不然只有一組會切掉 HP 不會OFF)
HPPOWER=OFF             設定是否是使用 HP power supply(OFF後則測試結束不會對HP POWER 做 RESET動作)
DMM=OFF                 設定非POWER的儀器使用
SMBType=2               設定使用SMB board 的版本


[BOOT]			用在當com port 無法使用,可借由print port傳回到dio port以求取控制
A0=C10.BAT		這資訊用在notebook main board(目前己經不用這段資料)
A1=C10.BAT
A2=C10.BAT
A3=C10.BAT
A4=C10.BAT
waitstring=C:\USI>

[COUNT]			在設定程式中所需限制的計數器.
Retest= 5		設定retest 按鈕只能設定重測5次,多測了則會自動結束回到barcode 
			form 沒有設定default值為99次
			
Retry= 3		設定retry 按鈕只能設定重測3次,多測了則會自動結束回到barcode 
			form 沒有設定default值為99次


[POWERRESET]		可以在此加入UUT COMMAND ,可以讓使用者按下電源關閉按鈕時會先執行
			的UUT COMMAND,其執行會依號碼依序執行.
0= 1000			0=1000 表示每行COMMAND中要間隔多少秒,不設定則為1000= 1秒
1= COM OFF
2= COM ON
3= COM SEND DATA ....
4= DIO TEST OFF
5= ........




[CONTROL] 設定NI CARD & GB Board 的設定值  
DEVICE=2		設定NI CARD 的DEVICE 值為何,通常一張卡其值為1,
CONTROLPORT=0		設定GB BOARD 的控制PORT為那一個NI 的PORT
ADDRESSPORT=2		設定GB BOARD 的位置控制PORT為那一個NI 的PORT
DATAPORT=3		設定GB BOARD 的資料存放PORT為那一個NI 的PORT
**CONTROL PORT 0,1 bit 選擇設定那一塊 GB Board 的DATA 11--1 10--2 01---3 00---4 
L5V=2			設定GB BOARD 的控制PORT為那一個NI的line 為控制給不給GB REALY 5V電
DAC=3			設定GB BOARD 的控制PORT為那一個NI的line 為控制DAC enable                   
ACH=4			設定GB BOARD 的控制PORT為那一個NI的line 為控制ACH enable
RESET=5			設定GB BOARD 的控制PORT為那一個NI的line 為控制RESET enable
WE=6			設定GB BOARD 的控制PORT為那一個NI的line 為控制Write enable
RE=7			設定GB BOARD 的控制PORT為那一個NI的line 為控制Read enable
ADDRESSFIRST=255	設定GB BOARD 的address 讀寫設定在GB Board的起始位置
ADDRESSEND=252		設定GB BOARD 的address 讀寫設定在GB Board的結束位置

設定PORT 0~ (255-252+1)*8 為read-0 or write-1去設定GB BOARD 的READ WRITE的屬性
PORT的順序為 0-1-2-3...-7, 8-9-10-11...-15, .......31 
PORTSET=11111111,11000000,00000011,10111111    


***************************************************************************
*                              BARCODE.INI                                *
***************************************************************************
放在 \prod\ 專案\版本 目錄下
[ICON]    可以用來改變barcode form的icon名稱,如果沒有,default是中文的
1=RETEST
2=SUBMIT
3=LOGOUT
4=CLOSE
5= 測試錯誤				用來在Multi barcode form中修改有測試錯誤的提示字串

11= OFF					控制"重測"的按鈕要不要顯示,Default 會顯示.OFF時會看不到.


[NONUSI]				主要是給NONUSI.EXE 使用的Section,其它AP可以用使用
APPATH=C:\Desktop\TextDiff.exe  	NON USI AP的路徑
					如果有參數或空白要使用 " " 包起來,參數和程式間要用分號
					 ; 區隔
      					"C:\Program Files\Movie Maker\MOVIEMK.exe ; /a/b/c"

APCAPTION=TextDiff			NON USI AP的Caption 字串
PASSCAPTION=小算盤			NON USI AP PASS Dialog 的Caption 字串
FAILCAPTION=小算盤			NON USI AP Fail Dialog 的Caption 字串
LOGPATH= D:\NONUSI\F0772log.txt		NON USI AP Test log 檔案路徑和名稱	
REPORTPATH=				NON USI AP Test report 檔案路徑和名稱,沒有可不輸入
MARK=  ,#				NON USI AP Test log 資料區隔字元,可設定多個區隔字元,如
					需空白要用其它字元包在其中例 , #

RESULTLOCAT=8				NON USI AP Test log 資料區隔pass fail位置
ERRORLOCAT=9				NON USI AP Test log 資料區隔error code位置
PASSSTRING= Pass			NON USI AP Test log 資料PASS的表示字串


[Logfile]				設定基本測試資料
LOGPATH=D:\SYMBOL\LOG\ 			設定LOCAL 測試資料存放地點
VARLOG= OFF				設定是否要輸出變數和時間的LOG,Default為ON
ErrorPos=4                              設定test log file 放error code 的位置
Filename=testlog.txt			設定 test log file name
;改放到change.ini   ProductLine=1				設定 生產線--產線名稱
ErrorVersion=1				設定error code 的版本編號
UUTStop= END OF TEST HI                 用在 PUSINet.exe 終止client的溝通字串,讓client結束的依據
AUTO=TRUE                               可以讓PUSIGB.EXE自動執行和結束,不設TRUE則Default 為FALSE,則不會自動執行
TESTTYPE=FCT1				用來提供生產線列印時識別測試類別
PRINTCOM=COM5				用來設定COM PORT 的Printer 由那個 COM Port 輸出

;PROJECTNAME= MC909X			用來設定PROJECT的名稱,會提供IMAGE 和 UUTAP的自動化更新使用,在SERVER端
					也要用相同的PROJECT 名稱來建立目錄,才能完成

[OtherLogfile]
LOGPATH=D:\LOG\VC80\ 			設定other LOG 測試資料存放地點,可能是客戶的SERVER連結的網路硬碟代號
LOGEXEName=D:\Pmotolog.exe		設定 Other LOG 的執行程式名稱,用來產生客戶所要的 LOG執行檔

1=ZEBRA_PROCESS : RHCB_FAT		設定要加入的字串,以 ZEBRA_ 為開頭的變數名稱, 而 : 後為儲存的值.
2=ZEBRA_STATION : RHCB_FAT01		如果有多個需要固定輸入的資料,依順序編號 1,2,3,4,5...
3=ZEBRA_FIXTURE : RHCB_FAT01-01


[host]     設定與SFC的控制設定
;改放到change.ini   port=1024				設定與SFC的通訊PORT
;改放到change.ini   IPAddress=172.25.6.225			設定SFC SERVER IP Address
TestPort=4000				用在網路版的TCP/IP 的port設定Pusinet.exe,目前也己加入到PUSIGB之中可用 
					LAN ON / OFF 開啟或關閉


[Position]				用在以USI BARCODE對應客戶的組態檔,要從USI BARCODE的START位置取長度
START=1					LENGTH 的字元來對應會由prod\systemBom.ini中取出客戶對應的config資料
LENGTH=9				其對應的資料會放到 [code] CONFIG= MC3000-KK...  中

USIADD= ON				ON表示要加入,OFF表不用加入USI的字串到客戶的字串尾端
					用在以USI BARCODE來加入不同語文或不同OS的版本控管如果客戶的BARCODE
					不包含語文版本的控制,則USI可用來將其控管加到客戶的後面,以利DOWLOAD
					將  section USIADD 的項次所對應的code 加到 section Config中
					如果己存在則不再加,如果為off則會刪除該項

[USIADD]
;編號     名稱      起始位置    字元數	設計要加到[CONFIG]尾部和[CODE]中的CONFIG= 字串後面
1=	  LANG	      3           2	均是針對USI料號位置
2=        USITYPE     5           2
3=        GGYY        7           2

[Config]
;編號     名稱      起始位置    字元數	組態的BARCOD每個字元的表示意義會存到DIO的VARSTRING中
1=       LAN         5           1	針對[CODE] CONFIG的位置
                                        LAN的名稱為固定,用來判斷有沒有LAN 的存在,如果沒有要在這個位置的值是'0'
					如果不為0則會打開要求USER 掃瞄 MAC CODE,要停掉這個功能將LAN 取別的名字
					即可

2=       WAN         6           1	這裡的 起始位置 為轉換為客戶Barcode所對應客戶Barcode的起始位置,而不是
3=       TYPE        8           1	USI Barcode的對應位置,不能用錯
4=       SCANNER     9           1
5=       WANCARRIER  10          1



 
//用在當IMAGE Muti form中有勾選 USI configuration 時會載入 symbolBOM2.INI的對應表,來產生對應的VAR.INI中的資料
[Position2]				用在以USI BARCODE對應變更組態檔,要從USI change barcode的START位置取長度
START=1					LENGTH 的字元來對應
LENGTH=2
USIADD2= ON				ON表示要加入,OFF表不用加入USI的字串到舊字串尾端用在以
					USI old BARCODE來比對不同語文或不同OS的版本控管,可以用來比對新舊barcode
					所要更新的部份,以減少生產時間,
					將  section USIADD2 的項次所對應的code 加到[CONFIG2]之中

USICHECK=ON				ON表示要顯示USI Configuration 的選項,OFF 則表示不要顯示USI Configuration
					的選項



[USIADD2]
;編號     名稱      起始位置    字元數	設計要加到[CONFIG2]尾部和[Position2]中的CONFIG2= 字串後面,
1=	  LANG	      3           2	其字串的來源是由USI料號位置取得
2=        USITYPE     5           2
3=        GGYY        7           2


[Config2]
;編號     名稱      起始位置    字元數	針對要Config section中所要對應更改的部份來做名稱的對應,取的名稱要和config
1=       VERSION    1           1	相同才能對應的到,如果相同名稱有對應到,且值相同時會將 VAR.INI中的變數增加
2=       OS         2           1	一個  變數名稱+'2'= KEEP,例如 OS2= KEEP 以利流程判斷要不要更新,當不同時,
					則不會增加任何多的變數,還是以原先 CONFIG 所產生的變數為主





[control]   設定barcode form的使用及各資料長度的控制
EMP_NOLength=5				設定作業員號碼的長度
BarcodeLength=22			設定Barcode的長度
SendBarcodeOnly=ON			設定只傳Barcode到shop flow server不管有沒有MAC 等等的值
MACCodeLength=5				設定MACCode的長度
MACCodeUses=OFF				設定是否使用MACCode form
MACHead=ABCD                            設定當MACCode的長度不足12碼時,送到SFIC前端要補的值,二者長度加起來要剛好12字元
MultiMAC=3				當同一片板子有多個MAC Code要輸入時,可以在這裡設定要多少個MAC要加入,
   					前面的會放到[MultiMAC],最後一個還是放在原來的[code]MAC= 之中

GUIDCodeLength=2			設定GUIDCode的長度,不給值可輸入任意長度的字串,唯要加enter, 才能再往下跑

GUIDCodeUses=OFF			設定是否使用GUIDCode form
GUIDSaveTO= 2				設定這個欄位要存放的位置,  沒有這個欄位時Default是被當成GUID送					
						2: 表示所送的資料為 GUID data 
						3: 表示所送的資料為 SSN data
						4: 表示所送的資料為 SN2 data 
						5: 表示所送的資料為 MO_NUMBER data




CONFIGLength=18				設定客戶組態的bar code 長度,會由prod\systemBOM.INI中讀USI PN 相對應客戶的資料長度
					取出之後會存在 barcode.ini 中[code] CONFIG 以供程式判斷使用.



CONFIG=ON				設定是否要使用客戶不同組態所要對應的程式


FCTCAPTION=USI FCT TESTER		設定 FCT CAPTION 顯示字串
FCTEXEName=PUSIGB.exe			設定 FCT Command 的執行程式名稱
FCTEXEParameters= D:\LOG\PATH\		設定FCT EXE 的需的參數
BarcodeFormname=PBarcodeFM.exe          設定 barcode form 的執行程式的名稱
CloseAPCaption='USI APP'		設定所要關掉的AP 其Caption名稱,這個會在使用Productver.exe時產生動作
 					如果沒有在選project前要關掉的AP 則這個項目可以不用設定,這個動作會試
					圖關掉 AP並提出警告,要求重新執行PROJECT VERSION SELECT AP
					例如:可設定多個caption中間用 # 號隔開 前後要加'  '如此才能在頭尾加空
					     白的字元

CloseAPCaption='AEX Sequencer - 1 x 32mb#AEX Sequencer - 2 x 32mb#AEX Sequencer - 4 x 32mb'
					

	

WaitFCTTime=2				設定 SFC Server 回應等待時間,以秒為單位
ShopFlow=OFF				設定是否要使用 SFC 系統

RDID1=B65D7763				Check sum 所加的檢查值,針對fctcommand.txe
RDID2=1179D371				DIO.INI
RDID3=9ECAAE2C				COM.INI
RDID4=C7A51634				BARCODE.INI


[MultiMAC]				當要輸入多個MAC時,這裡會放前 N-1個的資料,第N個還是放在原本的[code]
1=22222222				MAC= 之中
2=23333333



[MACRange]  當有使用MAC code時可以給其範圍值以供控管其是否在所給的範圍內
CheckMAC= OFF       設定on off 來設定是否要比對範圍值,default和該項不存在時是off
Start=A950A         設定開始範圍值
End=F059F           設定結束的值   
 
                    其值的長度要配合 [control] MACCodeLength=5 不則會error



[code]  備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
Barcode=ExitExitExitExitExitEx
MAC=ExitE
GUID=Ex
EMP_NO=ExitE
;FixtuerID=EXIT
;LINE_NO=0
CONFIG=MC3000-KK0MBBBA200

多個輸入視窗時所用的格式
   barcode,MAC code, GUID, SUBID(caption), PASS or fail data
1=1111111111111111111111,11111,11,1,1234
2=9999999999999999999999,99999,99,2,pass

[restore] 	備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
Barcode=246011901r01gc012cb01b
MAC=42343
GUID=24

[VersionPath] 備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
;control version FCTcommand file path

[RDTEST]    RD 程式所用的資料,請保留不要刪除,供multi- barcode input form 使用
EMP_NO=ExitE



[MAINFORM]   可由程式控制所要顯示的 主FORM 的寬度和字形大小
WIDTH= 700
FONT= 10

[MESSAGEFORM] 可由程式控制所要顯示的 MESSAGE BOX的大小和寬度
WIDTH=280
HEIGHT=100
FONT=16
***************************************************************************
*                              DIO.INI                                    *
***************************************************************************
[KEY]  使用DIO連到KEYBOARD 的INPUT 將KEY Matrix 轉成16進位值     放在 \prod\ 專案\版本 目錄下
A=4A			a的16進位值
B=74

[ALLKEY]		設定keyboard 測試的順序,需配合[KEY]中的名稱
; SEQUENCE  NAME
0=          A
1=          B
2=          C

[GPIBConfig]     提供GPIB Config的控制,可設定多個device 的值,以控制多個GPIB介面 ConfigID<=5
;name              BoardID   PrimaryAddress   SecondAddress   
PowerSupply=           0            1                0            

[HPPOWERSET]    設定 POWER SUPPLY 的供給電壓和限電流值
;name            voltage       電流      
SET37V=            3.7            3        

[GPIBDATA]      設定讀取GPIB 介面的值,並和後面的UP~LOW值比較,是否在範圍內,是傳回 TRUE,否傳回FALSE
                TYPE=1是設定讀電流, =2 是設定讀電壓  
;type==> VOLATGE=1  Current=2
;name            Type      UP       LOW       
HPCurrent=         2       1.3      -1.3          


[VARRANGE]    用來設定和 VAR.INI中的[VARREAL] 做比較,取出其中的值來和UP LOW 比對是否在範圍內,但二邊名
              稱要相同 COMMAND  可參考 readmec.txt中的 VARRANGE 
;name               UP       LOW
HPCurrent=          2       1.3     

[COUNTER]	會經由NI COUNTER讀回全波和半波的比值,看是否是在範圍UP~LOW之間,是傳回TRUE,否傳回FALSE
name可自行取有意義的名稱,CHANEL:定義由NI COUNTER的那一個 CHANEL 讀回,
PORT & LINE 在使用USI GB board 時設定由那一個擴充port line 讀回,
UP~LOW  設定讀回值的範圍
SLEEP   設定在USI GB Board設定時,每一個指令idle 時間

; 0:脈寬,1:頻率,2:FallingEdge,3:HiPulseWidth,4:LoPulseWidth
;
;ModeWidth= 31;
; name     CHANEL   PORT    Line    UP     LOW      SLEEP     MeasurementType
VGAMODE=      1       3       4      0.4     0.7      1000       1
SPK1=         0       3       4      0.4     0.7      100        1

[DAC]	會經由NI DAC 送出訊頻率訊號目前提供 sine wave,plus 日後增加功能可用
name可自行取有意義的名稱,CHANEL:定義由NI DAC的那一個 CHANEL 送出,
PORT & LINE 在使用USI GB board 時設定由那一個擴充port line 送出,
Wavetype ==> 設定輸出訊號的格式 sine ,plus
SAMPLE RATE==> 取樣數
Frequence==> 設定頻率
AMP==>       電壓範圍
; name       CHANEL   Port   Line   WaveType    SAMPLE RATE    Frequence   AMP
SINWAVE=     0        3      0      sine        18000          1000         3
SINWAVE1=    0        3      0      sine        2000           10           3
MYPLUS1=     0        3      0      plus        2000           1000         1


[PULSE] 會經由 NI GPCTR 輸出一組頻率設定
name可自行取有意義的名稱Counter:定義由NI GPCTR的那一個 LINE 送出,6025E只有二個 0和1
PORT & LINE 在使用USI GB board 時設定由那一個擴充port line 送出,
Frequence==> 設定頻率
; name      Counter    Port   Line   Frequence 
P200=        0           0     3        200

[DACPOINT]  會經由NI DAC 送出固定電壓訊號name可自行取有意義的名稱,CHANEL:定義由
NI DAC的那一個 CHANEL 送出,PORT & LINE 在使用USI GB board 時設定由那一個擴充
port line 送出, VOLTAGE==> 送出固定維持一個定電壓
; name       CHANEL   Port   Line     VOLTAGE
V3P7=        0        3      0         3.9


[SMB]    設定 SMB Board 的資料值,前面名稱不能改,由RD工程師設定
SMB ==> (2.5V * 6.09)/255 =0.0597  表0~255階每一階的值 如要8V 則用 8/0.0597=134.0
故階數可設成 134 即可得 8V的輸出最多只到15.2V, 但還要依供應的電壓最大值的80% 
VDISDegree==> Discharge degree (放電輸出)
VCHADegree==> charge degree    (充電門檻)
SMB ==> (2.5V * 1.4484)/255 =0.0142  表0~255階每一階的值 如要3A 則用 3/0.0142=211
故階數可設成 211 即可得 3A的限電流,最大容納電流約3.6A
IDegree==> 
   
;POWER MODE SET
VDISDegree= 0.0597
VDISSub=1.25 (for SMB2使用,即設定電壓要減的值,再除上Degree值得到階數)
VCHADegree= 0.0597
IDegree= 0.0142 (充電限電流)
IProtectDegree= 0.0142 (保護電流)

[ACHWAVE]  讀取ACH WAVE 的資料,去取得峰對峰的值差,並與UP~LOW值相比在範圍內為TURE否則傳回FALSE
SAMPLE_RATE==> 取樣數量        Frequence==>WAVE 的頻率設定
CHANEL==> 使用NI CARD的那一個Chanel來量測.  port,line==> 使用GB Card時的擴充port line 的指定        

; differential mode set SINGLE=0 , single mode set SINGLE=1
; name       CHANEL   Port   Line   SINGLE   SAMPLE_RATE    Frequence  SLEEP   UP     LOW   
AUDIO=        0        0      1       0         100            2000       50    2       3 



[ACHFREQ] 可以判斷 頻率, offset, 峰對峰的值差, 次頻率傅利頁轉換的大小值
  Frequence最好取要量測頻率10倍以上較佳,不得少於二倍,範圍在4k以內較佳,二倍則Frequence可設到8k
Frequp , Freqlow ==>所要測量頻率的上下限值
SubFup , SubFlow ==>副頻的傅利葉轉換值的大小範圍
Offsetup,Offsetlow==> 所量測的offset的上下限值
Vup    , Vlow    ==>所量測振幅的上下限值,其值為最大值減最小值 3-(-3)=6 
FilterUP, FilterLow=> 想要取那一個範圍之間的頻率, 其它均率掉不取. filterUp 要小於 frequence/2 否則做率波時會錯誤
scannumber ==> 決定所要取樣的資料數,如果和掃除頻率相同,則精確度最高,否則會成一個比值決定誤差範圍 Frequence / scannumber = 誤差大小
               scannumber <= 10,000 再大不合用,一方面會秏時很久,一方面記憶體會不夠用,程式會 down 掉


; name       CHANEL   Port   Line   Frequence   Frequp     Freqlow   SubFup    SubFlow   Offsetup     Offsetlow     Vup    Vlow  FilterUP   FilterLow   scanNumber
FEI=          0        1      1       2000       1000        800      0.01        0        2.5           0          4.5   3.5       3000       500          2000
   
[ACHV]  透過NI CARD的ACH來量測UUT的電壓,並與UP~LOW值相比在範圍內為TURE否則傳回FALSE
MULTIPLE==>透過GB CARD可量測大於10V 以上的電壓,加上乘數可得正確值,NI CARD只能量10V以內的電壓
;         CHANNEL   PORT   LINE   SINGLE  SLEEP  UP     LOW   MULTIPLE
MAIN_DC=      8     0      6      1       50     3.6    3.0   1
VCC5=         0     0      1      1       50     5.25   4.75   1


[ACHI]利用壓差來算電流值,DisCharge-DIFF  Charge-DIFF     DisCharge-SING    Charge-SING來設定各種TPYE的倍率  
SW1,SW2,SW3,SW4==>CURRENT sensor

;SW set for read current, the voltage divide resistance value*** DON'T CHANGE NAME
;NAME   resistance   DisCharge-DIFF  Charge-DIFF     DisCharge-SING    Charge-SING   
SW1=    1            1               1                  1               1
SW2=    0.1          -1              -1                 -1              -1
SW3=    100          -1              -1                 -1              -1
SW4=    1000         -1              -1                 -1              -1

透過GB CARD& NI CARD的 Channel port,line,single來設定其值,SW表使用那一組Current sensor來量測,DisCharge on off的開關,Trikle慢充
VD2 電壓門檻(外部電壓要大於電壓門檻才能對SMB充電),VD1輸出電壓,current==>設定最大充電電流限制
ProtectCurrent  為設定最大輸出電流,做過電流保護,類似 HP Powre supply protect
;                      CHANNEL   PORT   LINE  SINGLE  SLEEP        UP      LOW     SW     DisCharge  battery   Trikle   VD2   current  VD1  ProtectCurrent             
OperaTionChargeTest1=    7        2      7     0       1000       1       -2.8     SW2      OFF       1         OFF     3.7     0.2    3.5      3


#######################################   刪除了,不再使用
[RJDATA] 配合[DIO]中的設定來存取DIO取回值是否正確.
;item    dioname    data
0=       RJSend1    0
1=       RJReceive1 0
2=       RJSend2    0
3=       RJReceive2 0
#######################################    刪除了,不再使用

[DIO]設定DIO的PORT,Start line ,line bit number,
ON,OFF,0,1是設定COMMAND的ON OFF 0 1表示的意義
ON=0    
OFF=1
0=ON
1=OFF
;name可自行取有意義的名稱
PORT 在使用USI GB board 或 NI card時設定由那一個port 送出,
STARTLine 設定啟始的line即那一個port的第幾個line開始,可向後設定多少個line即Bitnumber,Bitnumber最多不可超過8
;name          PORT    STARTLine   BITNUMBER
DIOPORT=        0        0            8
PORTA=          2        0            8
PORTB=          3        0            8

[NIDIODIRECT]
; DATA:=1 OUTPUT  DATA:=0 INPUT  
; 如果  DATA=15  0x00001111  則 Low 4bit is ouput,  up 4bit is input
; SETLINE:=1 LINE SET    O PORT SET  =1時表示是以line來設定,=0時表示是以整個port來設定
; port 表示要設定的port 的選擇
;name可自行取有意義的名稱

;NAME        PORT   SETLINE   DATA
PORTDIR0=        0       1       242
PORTDIR2=        2       0       0


[DIOMACRO]
;Name    名稱    sleep 各個dio資料所要間隔的時間,  DATA==>DIO command的組合,用','號分隔
DATA的部分下的指令如同 DIO COMMAND 所下的相同,維不用加 DIO這個字串,但該項資料必需存在在
[DIO] Setion 之中

POWERON=  1000,PORTA 22,PORTB 33,PORTC 44

[UIMACRO]
NAME 為這個MACRO的呼叫名稱,各個命令由 % 符號隔開,可以使用 FCTCOMMAND所提的所有的命令
例如:  UIMACRO  POWERON 最後一個 , 之後的數字為 ms 用來間隔各命令的delay time

NAME   DATA
POWERON=  DIO PORTDIR0 22 % ACHV V3P7 % WAIT ABC,2000



[LAB]
;NAME 名稱,  L  A B  分別為LAB的中間平均值.
COLOR1 =    220  1   -2




[DIO48DEVICE]   給DIO48的卡使用,編號要從1 開始,如果有多張卡可依續  1,2,3
; 1卡的編號     2.每一個Port方向 0:write  1:read    3.所要設定初始值之 section name      
; CardID  Port-direction   Initial-name
1=  0       000111            MYDIO48


[MYDIO48]  依DIO48中所設定各卡號所要設定初始值的Section name 來設定write port的初始值
;前面的ID-KEY要按1,2,3...的方式編寫
;   1.port number    2.初始值
;  portnumber    initial-data
1= 1                    255
2= 2                    211
3= 4                    0





***************************************************************************
*                              VAR.INI                                    *
***************************************************************************
FCTCOMMAND中存變數的位置   放在 \prod\ 專案\版本 目錄下
[VARREAL]

[VARBOOL] //目前沒有使用

[VARSTRING]

[SAVEVAR]//當command中有使用 >> 時會將變數值存放到這,最後作一次的輸出所要的變數值
	 方便資料蒐集和統計
0=ITEM1 11.0000
1=ITEM2 12.0000

[ERROR] 存放失敗的資料集合,以便在錯誤時提供所有錯誤的LIST(在不希望測試中斷時使用)
	CS-RP 勾選後除了電系部份不會讓其通過一般的錯誤可以繼續執行

[ERRORDATA] 存放有關電系錯誤存放的值

[SAVETIME] 存放每一個測項測試時間
0=20:55:18
1=20:55:20
2=20:55:20
3=20:55:25

[RETRY]  存放每一個測項重測了多少次
CM002=14
SD005=8
USB13=8

***************************************************************************
*                              Version.INI                                *
***************************************************************************
該ini file 需放在各個project的目錄下,不要放入各project的版本目錄裏面去   放在 \prod\ 專案\ 目錄下
[number]
BarCodeNumber= 22  	 設定BARCODE的長度
CheckLength= 9      	設定用多少個字元來判斷版本資訊
START=1		    	從USI BARCODE的START位置取CheckLength長度來比對
BatchNumber= 123345679 	如果version的選擇是透過掃barcode就會產生一個依據 start,checklength所抓出來的字串
			提供後續產品barcode的比對,避免不同批次但用相同目錄測試的板子混料,這個程式會自動作 

[barcode]
barcode  根據上面CheckLength來比對barcode的資料
QC 是區分是QC的測試或著是產線的測試
PATHNAME 是各個PROJECT的子目錄名稱
Explain 文字描述這個目錄的版本資料

;    barcode        QC        PathName                        Explain 
1=   246102401       N         Ver2.01                         8100VER3.0
等號後面要有空白,不能用TAB 鍵來空格,資料格式會錯誤

***************************************************************************
*                              product.txt                                *
***************************************************************************
第一行是描述產品所在位置:  在執行目錄下
D:\ibmbeta\usi\usiGBTool\prod\Apollo\v1.1\
第二行是描述是否為QC使用版本 是為 Y  不是為 N
Y




***************************************************************************
*                              systemBOM.INI                              *
***************************************************************************
[config]   放在 \prod\ 專案\systembom.ini  目錄
USIBARCODE  客戶組態編號
810001-00=MC3000-KK0MB2BA200

用來處理當客戶組態複雜時的自動對應檔,檔案來源為USI PE
也可以用來設定barcode or guid等資料所要取得的目錄資料,可借由GETSYSTEMBOM
  FCT Command來取得.取得後會放到 var.ini 中的 VARSTRING section中的ID
MYBOM 中
目前有使用的是在設定不同的ID 會取得不同的路徑資料

[Control]
SFISBOM = ON    ON表示要從SFIS取得CONFIG DATA, Default 是OFF
***************************************************************************
*                              systemBOM2.INI                              *
***************************************************************************
[config]   放在 \prod\ 專案\systembom.ini  目錄
USIBARCODE  客戶組態編號
810001-00=MC3000-KK0MB2BA200

用來處理當客戶組態複雜時的自動對應檔,檔案來源為USI PE
主要作用在當出貨前要更換各種版本,重新下載image用以結省不必要的下載時間,
要配合systemBOM.INI 和 barcode.ini中的設定 
如果有使用則:
1.systemBOM2.INI 為原本測試時的barcode
2.systemBOM.INI 為要出貨時要設的barcode

詳細設定看 barcode-readme.txt
                              
[control]
RDID6=66B10494  Check Sum所寫入systembo.ini的值
SFISBOM=ON	使用SFIS 所提供的 BOM 而不使用自身定義的BOM


***************************************************************************
*                              Symbol.ini                                 *
***************************************************************************
[COM] 用在多個COM PORT 的對應程式  放在 \prod\  目錄下
;   comport          comrate       readIntervalTimeOut
1=     29               38400                10
2=     4               38400                10

[USB] 用在SYMBOL IMAGE 下載對應的 USB ID
; USB ID 
delay=10
1=6&25e66231&0&5
2=6&25e66231&0&6
3=6&25e66231&0&7
4=6&25e66231&0&8

DEVICEID= 6&25e66231&0&8    這個值是在設定由PUSIGB.EXE 呼叫時取代 # 內容使用

[DeviceCheck] 用來計數測試板使用次數
0=1000   檢查板子的上限值,到了這個值就會顯示紅色的字,並且會提出警告視窗
1=2		各板子使用次數
2=3
3=3
4=4



[FixtureID]  用來設定每一台治具的ID 做為送到 SFIS 的識別使用,如果沒有這個Section
             就會以電腦名稱做為 ID 值
IDHead= PD3-L1			可以設定每一台治具相同的部份,可以手動事先設定,也可以不需要這項
NumberBox= OFF			這個參數可以設定是否要跳出Fixtrue ID 的序號輸入視窗,如果在IDHead
				己全部設完可以不用再設定. Default 值是 ON,一定要輸入OFF字串才會
				不顯示.
		 



IDNumber=2349803294		這裡的值會由Productver.exe 程式來負責輸入,User 不用設定



自定 SECTION & NAME 可以提供FCTCOMMAND 以GETINI COMMAND 來使用GETINI 有三個參數
GETINI   SECTION NAME VARNAME    第一個是section 名稱例: MAC 
                                 第二個是 name   例: 1, 2
                                 第三個是 fctcommand 中要存的變數名稱
                                 詳細內容可參考 readmec.txt							
  [MAC]
   1= ABCD12345678
   2= TESTABC
					如此我們可以將FCTCOMMAND 一致化不用每台PC要設定不同的流程

[SFIS]
SUBMIT = OFF			當設定為OFF時,測試完後不會自動按SUBMIT按鍵,讓USER自己選.沒設定時為ON



***************************************************************************
*                              SCAN.ini                                   *
***************************************************************************
[SCANCOM]
SCANCOM = COM18			用來設定自動SCAN BARCODE的檔案

***************************************************************************
*                              COM.INI                                    *
***************************************************************************
放在 \prod\ 專案\版本 目錄下



[SYMBOL]
SymbolUSB=ON					是否要開啟symbol Multi Load的程式
APPath=D:\ibmbeta\GetWinH\Multi-Flash\MultiLoad.exe	Multi Load or Hexloader等程式位置
MCaption=MultiLoad					Multi Load程式的caption



[IMAGE]  各種IMAGE 的位置 配合SYMBOL的燒錄軟體所要的COMMAND 來設定其位置
         在命令中如果打入 # 號則會依Muti form的編號將symbol.ini中的[USB]的相對
	對應號碼代入, 如 form1 會導入 1= 的值,form2 會導入 2= 的值
Monitor= /u # /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XMon00.21.hex
Partition= /u # /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XPTbl440001.hex
Application= /u 0 /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XApp440004.hex

Platform1= /u 0 /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XPlat440284.hex
Platform2= /u 0 /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XPlat440384.hex
Platform3= /u 0 /d 3 "d:\MC3000\DVT\BSP4.4.004"\30XXc42XPlat440484.hex

Splash1= /u 0 /d 3 "d:\MC3000\DVT\BBSP4.4.004"\30XXc42XSplC001.hex
Splash2= /u 0 /d 3 "d:\MC3000\DVT\BBSP4.4.004"\30XXc42XSplM001.hex


[NONUSI]		主要是給NONUSI.EXE 使用的Section,其它AP可以不使用
			用在取得的error code和USI Error code 的對應
Error #64 =  USI001
Error #65 =  USI002








***************************************************************************

                           自動化更新

***************************************************************************
*                           SERVER.INI                                    *
***************************************************************************
放在 C:\USI\ 目錄下   用來連線到自動更新的server 利用 productver.exe執行時做更
新動作

[Server]
 ServerID=  \\W13-2\USIPROJECT ,  \\127.25.1.46\USIPROJECT   ;設定SERVER分享路徑
 USERNAME= AAA      ;登入分享目錄的使用者名稱
 PASSWORD=  12345   ;登入分享目錄的使用者密碼
 INIPATH= UPDATE\PROJECT   ;用來比對INI file 是否是最新的資料,專案所使用的INI 路徑 
 UPDATE= ON / OFF   ;決定是否要連上 SERVER去更新資料

 LogServer= \\172.11.13.88\SYSLOG  可以指定LOG SERVER路徑,但這個路徑必需存在,使用者
                                   密碼是固定,會連接到 U:
                                   不存在這個KEY值時就不會設定
                                   存在時可將測試的log 指向  U:\

***************************************************************************
*                            UPDATE.INI                                   *
***************************************************************************
放在 C:\USI\ 目錄下   用來決定在何時下載何目錄的檔案 利用 productver.exe執行時做更
新動作
路徑規則:
     1.前後不需要加 \ 
     2.server.ini的serverID即為Source所在目錄
     3.*.* 表示只複製本身目錄,不含子目錄
     4. +表以所選 project名稱取代,但不可用在 FolderBulid 和 StartCheck
     5. #表以所選的 version名稱取代,只能用在 VersionCheck中
     6.各目錄資料更新的細項資料會依更的目錄放在 c:\USI 目錄下,依年月日區分
     7. 如果要複製到不同的目錄, 則用 ; 號隔開並在分號後面指定所設的的目錄
          1= PROD\PROJECT  ; D:\MYFOLDER\ 

   [FolderBulid] 只在建立空目錄(含子目錄) 會在程開啟時執行
    1= PROD\ PROJECT        ;C:\USI\PROD\PROJECT  會針對不同目錄建立子目錄         
    2= PROD\ PROJECT2
    3=IMAGE\PROJECT
    4=CPLD\PROJECT
    5=UUTAP\PROJECT
	:
     
   [StartCheck] 最後為*.*則為本身目錄不包含子目錄 (為在沒選擇project之前所要檢驗的目錄)
		會在程開啟時執行(依需要來設定) 
    1=*.*
    2= JTAG\*.* ; D:\JTAG\JTAG.BOARD
   [ProjectCheck] 最後為*.*則為本身目錄不包含子目錄,如果有+號,則以所選的PROJECT 名稱取代,project 不可使用version的取代符號 #

    1= PROD\ PROJECT                  
    2= PROD\ +
    3=IMAGE\*.*
    4= JTAG\+ ;D:\JTAG\JTAG.BOARD\+
    5= JTAG\+\INI\*.* ;C:\Bst32\aexman     主要在複製aexman.ini的資料 

   [VersionCheck] 最後為*.*則為本身目錄不包含子目錄(為在選擇Version後所要檢驗的目錄) 如果有#號,則以所選的version 
                  名稱取代,如果有+號,則以所選的PROJECT 名稱取代,用project的取代符號一定要配合version的取代符號,因
                  為各project未必有指定的version存在,

    1=*.*
    2=PROD \PROJECT          PROD\+\#
    3=PROD\ PROJECT2\TEST
    4=IMAGE\PROJECT
    5= JTAG\+\#  ; D:\JTAG\AEXMANGER\+\#
    


***************************************************************************
*                            CHANGE.INI                                   *
***************************************************************************
[Logfile]				設定基本測試資料
ProductLine=1				設定 生產線--產線名稱

[host]     設定與SFC的控制設定
port=1024				設定與SFC的通訊PORT
IPAddress=172.25.6.225			設定SFC SERVER IP Address

[SYMBOL]
PATH = C:\TEMP\SYMBOL.INI    		新增項目,可讓USER自行設定SYMBOL.INI存放的位置,
					沒設定的話,即會存放在USIPROJECT\PROD\ 中
					路徑要給完整路徑加檔名.


//Version.ini 中移過來
將會變動的資料放在這個INI 中以免在版本比對時產生誤判,當這個檔案不存在時,會延用舊的規則,以向前相容
[number] 
BatchNumber= 123345679 	如果version的選擇是透過掃barcode就會產生一個依據 start,checklength所抓出來的字串
			提供後續產品barcode的比對,避免不同批次但用相同目錄測試的板子混料,這個程式會自動作 


//barcode.ini 中移過來的
[MultiMAC]				當要輸入多個MAC時,這裡會放前 N-1個的資料,第N個還是放在原本的[code]
1=22222222				MAC= 之中
2=23333333


[code]  備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
Barcode=ExitExitExitExitExitEx
MAC=ExitE
GUID=Ex
EMP_NO=ExitE
;FixtuerID=EXIT
;LINE_NO=0
CONFIG=MC3000-KK0MBBBA200

多個輸入視窗時所用的格式
   barcode,MAC code, FIX, SUBID(caption), PASS or fail data
1=1111111111111111111111,11111,11,1,1234
2=9999999999999999999999,99999,99,2,pass

[restore] 	備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
Barcode=246011901r01gc012cb01b
MAC=42343
GUID=24

[VersionPath] 備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
;control version FCTcommand file path

[RDTEST]    RD 程式所用的資料,請保留不要刪除,供multi- barcode input form 使用
EMP_NO=ExitE


[ActiveSync]   如果有設定這個,則在發現caption所屬的視窗存在時,會主動縮小它(可以設定二個)
CAPTION= Windows Mobile 裝置中心
CAPTION2= ABCD...