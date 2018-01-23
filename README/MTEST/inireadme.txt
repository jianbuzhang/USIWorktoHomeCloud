***************************************************************************
*                                       GB.INI                            *
***************************************************************************
放在 \prod\ 專案\版本 目錄下


[COUNT]			在設定程式中所需限制的計數器.
Retest= 5		設定retest 按鈕只能設定重測5次,多測了則會自動結束回到barcode 
			form 沒有設定default值為99次
			
Retry= 3		設定retry 按鈕只能設定重測3次,多測了則會自動結束回到barcode 
			form 沒有設定default值為99次


			分成4個FORM 來各自做自己的POWER RESET
[POWERRESET]
 如果有會累加造成資源大增,可以在此設定要清除的命令,它會在所有測試form回到barcode時執
行一次,另外在關掉 MTEST.EXE時會執行一次.僅慎使用,非必要不要使用.
例如:
1= WAIT
2= DOSCMD taskkill /F /IM fastboot.exe 
3= WAIT DOSCMD-END,10000
4= WAIT
5= DOSCMD taskkill /F /IM adb.exe 
6= WAIT DOSCMD-END,3000
7= WAIT
8= DOSCMD taskkill /F /IM cmd.exe 
9= WAIT DOSCMD-END,3000


[POWERRESET1]		可以在此加入UUT COMMAND ,可以讓使用者按下電源關閉按鈕時會先執行
1=FLAG ON MCOM		的UUT COMMAND,其執行會依號碼依序執行.設定和fctcommand 同,但不要
2=ECHO HELLO1		加入errorcode 結尾也不要加入END,共用資源需加入Flag取得資源.
3=ECHO HI1              它的主要原理:
4=FLAG OFF MCOM		把各個form所需的reset寫成各自的reset,按reset key時會將這段code取
			代目前的fctcommand內容來執行,所以即始按rtest也是執行替換過的reset
			內容.但error code or pass fail會保持原有的 pass fail不會變更


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
放在 \prod\ 專案\版本 目錄下

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

	

BarcodeFormname=MTest.exe

ShopFlow=OFF				設定是否要使用 SFC 系統

RDID1=B65D7763				Check sum 所加的檢查值,針對fctcommand.txe
RDID2=1179D371				DIO.INI
RDID3=9ECAAE2C				COM.INI
RDID4=C7A51634				BARCODE.INI

Version=00-00-00-00

***************************************************************************
*                              DIO.INI                                    *
***************************************************************************

[VARRANGE]    用來設定和 VAR.INI中的[VARREAL] 做比較,取出其中的值來和UP LOW 比對是否在範圍內,但二邊名
              稱要相同 COMMAND  可參考 readmec.txt中的 VARRANGE 
;name               UP       LOW
HPCurrent=          2       1.3     


[UIMACRO1]
NAME 為這個MACRO的呼叫名稱,各個命令由 % 符號隔開,可以使用 FCTCOMMAND所提的所有的命令
各個FORM 要使用的內容是對應自己的[UIMACRO1] [UIMACRO2] [UIMACRO3] [UIMACRO4]
例如:  UIMACRO  MYSTRING 這樣在 FCT COMMAND可以使用同一個 UIMACRO 名稱,但內容
可以不同


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
FCTCOMMAND中存變數的位置   放在 \prod\ 專案\版本 目錄下
[VARREAL]


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
3=     17                115200               50
4=     18                115200               50

COMENTER= 0D0A		這個選項在為COM PORT決定送出字串後要下何字串為結尾,當這個選項不存在時
			標準的COM PORT會在結尾加上0D0A ,目前這個設定表示在COM PORT送出字串時
			只加上 0D 這個16進位的字元,字元一定要是偶位數,不可以只下 A0D 這樣會產
			生錯誤 
IgnoreNullChar= ON	不設定則為ON,可設成 OFF會取消忽略空白字元的功能
RtsControl=ON		不設定則為ON RTS control Enable功能,設成 OFF會disable RTS Control控制功能
DataSwitch=1            設定輸出log 的間隔,最大不要超過 100,default = 1;

[LAN]
;  lan port
1=4000
2=4002
3=4003
4=4004




[USB] 用在RUNSTR 中COM.INI中的# 號的取代字元
; USB ID 
delay=10
1=6&25e66231&0&5
2=6&25e66231&0&6
3=6&25e66231&0&7
4=6&25e66231&0&8



[COMMON]
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

[COMMON2]
COMRate=38400		設定COM PORT 的傳輸率	
COMPORT=COM2		設定使用那一個COM PORT ,COM1  COM2 COM3
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


[GPIBConfig]
;name    PrimaryAddress   
DMM=        22               


[VISAConfig]
;name    source-name
DMM= USB0::0x164E::0x0DAD::TW00004773::INSTR   


[FixtureID]  用來設定每一台治具的ID 做為送到 SFIS 的識別使用,如果沒有這個Section
             就會以電腦名稱做為 ID 值
IDHead= PD3-L1			可以設定每一台治具相同的部份,可以手動事先設定,也可以不需要這項

IDNumber=2349803294		這裡的值會由Productver.exe 程式來負責輸入,User 不用設定

 NUMBERBOX=OFF				
 
[SFIS]
SUBMIT = OFF			當設定為OFF時,測試完後不會自動按SUBMIT按鍵,讓USER自己選.沒設定時為OFF


[FORM]
SHOW = 0

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



***************************************************************************
*                            CHANGE.INI                                   *
***************************************************************************


[Logfile]				設定基本測試資料
LOGPATH=d:\D7800\D7800-SYS-IMAGE\
Filename=testlog.txt
ProductLine=D7800			設定 生產線--產線名稱
ErrorVersion=1



[host]     設定與SFC的控制設定
port=1024				設定與SFC的通訊PORT
IPAddress=172.25.6.225			設定SFC SERVER IP Address
TimeOutSec= 180				設定 SFC Server 回應等待時間,以秒為單位


[MULTIMAC]	當要輸入多個MAC時,這裡會放前 N-1個的資料,第N個還是放在原本的[code]
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

//Version.ini 中移過來
將會變動的資料放在這個INI 中以免在版本比對時產生誤判,當這個檔案不存在時,會延用舊的規則,以向前相容
[number] 
BatchNumber= 123345679 	如果version的選擇是透過掃barcode就會產生一個依據 start,checklength所抓出來的字串
			提供後續產品barcode的比對,避免不同批次但用相同目錄測試的板子混料,這個程式會自動作 




[code]  備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
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


[restore] 	備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
1=1111111111111111111111,111111111111,11
2=22222,333333333333
3=22222,333333333333
4=22222,111111111111
CONFIG1=7800LWQ-GC211XE,7800LWQ-GC211XE
CONFIG2=7800LWQ-GC211XE,7800LWQ-GC211XE
CONFIG3=7800LWQ-GC211XE,7800LWQ-GC211XE
CONFIG4=7800LWQ-GC211XE,7800LWQ-GC211XE

[VersionPath] 備份目前正在執行的UUT資料,為程式控制使用,使用者不用更動,也不能刪除
;control version FCTcommand file path

[RDTEST]    RD 程式所用的資料,請保留不要刪除,供multi- barcode input form 使用
EMP_NO=ExitE

[SYMBOL]
PATH = C:\TEMP\SYMBOL.INI    		新增項目,可讓USER自行設定SYMBOL.INI存放的位置,
					沒設定的話,即會存放在USIPROJECT\PROD\ 中
					路徑要給完整路徑加檔名.



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
    


