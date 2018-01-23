Command         add-data                 discription

COM		dos command    		經由 com port送資料到 UUT端(含enter) 如
					果要送空白字可以下 COM SPACE (只有一個
					空白不含enter) 
					COM OFF , COM ON 可開關 COM PORT 
					COM ON 38400  COM2 
					在ON 時可以設定 COM PORT的傳輸率和指定
					RTS CONTROL的控制
					COM ON 38400 COM2 ON
					COM ON 38400 COM2 OFF
					最後的ON OFF是決定RTSControl是否開啟可在
					這做動態修改,如果要固定可在GB.INI中設定
					ON 表示使用RTSControl
					OFF 表示不使用RTSControl

					那一個com port 輸出入
			   		COM =  字串變數名稱
					
					程式中有二個COM Device可設定,不指定則使
					用第一個COM Device 設定可由 COM ON/OFF 
					的過程來指定使用 @@1 or @@2  來區隔
					COM OFF @@2    COM ON 38400 COM2  @@2
					COM =  字串變數名稱 @@2
					COM ABCD.EXE  @@2


COMFILE		data    		經由 com port送TXT檔案資料到 UUT端,但必
					需COM PORT要先打開,才可以執行這個命令,
					DATA的字串分成二個部份用 , 號分隔.  
					第一個部份:為每一行之間要延遲多少 ms 
					第二個部份:為所要傳輸的txt file 的路徑和
					檔名
					
					COMFILE  50,D:\123.TXT 



                                                          
COMHEX 		ASCII-CODE		可經由 COM PORT送16進位的字串到UUT端.
					COMHEX  313A00  

					程式中有二個COM Device可設定,不指定則使
					用第一個COM Device 設定可由 COM ON/OFF 
					的過程來指定使用 @1 or @2  來區隔
					COMHEX  313A00 @2    
					



GETHEX		ON | OFF		可經由 COM PORT 收進來的資料以16進位顯
					示,控制以ON OFF 來控制
					GETHEX ON 表示將COM PORT的資料改以16進
						    位值收入
					GETHEX OFF 表示將COM PORT的資料以字串形
						    式收入


DIO		name  value		參考 DIO.INI  [dio] setion & name==>
					     DIO DATA1 255
					name 可在DIO.INI中自行設定所需的資料
					如果只有一個bit也可用 DIO data1  ON   
					; DIO data1 OFF 來做開關的動作

DIOMACRO	name			參考DIO.INI [DIOMICRO] Setion & name可在
					DIO.INI中自行設定所需的資料name 
					DIOMICRO  POWERON
                                        
DIOREAD		name  data		參考DIO.INI [dio] setion-name 設定name &
					比較資料data 如果NI DIO 取回的資料和data 
					相同則TRUE 否則回傳 FALSE 可以存到變數中
					來判斷 DIOREAD  DATA1 = ABCD再以 
				   IF ( ABCD > 234 ) THEN @ERROR1 ELSE @ERROR2

					DIOREAD  DATA1 = ABCD >> 
					則會將資料也存到VAR.INI中的savevar
					section 的變數資料,最後會加到
					testlog.txtvar之中 



ACHV		name			參考 
					DIO.INI [ACHV] setion & name==>ACHV V3P7
					name 可在DIO.INI中自行設定所需的資料如果
					有等號則會存到var.ini中的實數變數中,不判
					斷對錯
					ACHV  TEST1 = MYTEST 
					結果會存到 VAR.INI中的MYTEST變數中

					ACHV  TEST1 = MYTEST >> 
					則會將資料也存到VAR.INI中的savevar
					section 的變數資料,最後會加到
					testlog.txtvar之中,不判斷對錯 

					ACHV  TEST1  >> 則會將資料也存到VAR.INI
					中的savevar section的變數資料用errorcode
					為名稱,最後會加到testlog.txtvar之中,會
					判斷對錯 

ACHI		name			參考 DIO.INI [ACHI] setion & name==> 
					ACHI   OperaTionChargeTest1
					如果有等號則會存到var.ini中的實數變數中,
					不判斷對錯
					ACHI  TEST1 = MYTEST  
					結果會存到VAR.INI中的MYTEST變數中

					ACHI  TEST1 = MYTEST >> 
					則會將資料也存到VAR.INI中的savevar
					section 的變數資料,最後會加到
					testlog.txtvar	之中,不判斷對錯

					ACHI  TEST1  >> 則會將資料也存到VAR.INI
					中的savevar section 的變數資料用
					errorcode為名稱,最後會加到
					testlog.txtvar之中,會判斷對錯 


SAVEWAIT	ON / OFF		可以設定是否要將等到的字串行存在變數中,
					以供解析字串使用,需要配合WAIT來使用
					SAVEWAIT ON   打開等待字串行存檔
					WAIT GOOD = MYDATA 會將等到GOOD字串的那
						    一行存到VARINI中的varstring
						    變數名稱為 MYDATA 的資料中
					SAVEWAIT OFF    關掉等待字串行的存檔
					

                
WAIT		waitstring,timeout	等待COM port送過來的資料核對,timeout等待
					時間(1000)表1秒	Default 是3分鐘: 
					例: WAIT C:>,1000
				WAIT (crc32 is 0xAB744A4C~crc32 is 0x87F536A4) 
					可以等待多個字串 

					~ 表or,  & 表 and
					當等待字串有 , 時可用下面例題設定
 					WAIT (crc32,4,),2000  這時候後面一定要
					設TIME OUT 的時間,不能設=和>>

					WAIT crc32 is 0xAB744A4C = TEST,2000 會
					將找到或找不到寫到字串變數
					TEST 中 TEST= TRUE  or  TEST= FALSE可用
					IF來做判斷在有 = 號的狀態下等到時間超過
					時不會停止,只會設定變數為FALSE然後繼續往
					下測試
					
				WAIT ABC = TEST >>,2000 WAIT ABC >>,2000
					沒有= 號的錯鋘時直接停止,  >> 則會將資料
					也存到VAR.INI中的savevar section 的變數
					資料最後會加到testlog.txtvar之中

					WAIT 後不接任何字串,則UUT傳來的字串會暫
					時保存在BUFFER中不送出來處理等到下一個 
					WAIT waitstring 字串的command出現時才會
					將之前的字串送出用以防止大量快速資料處
					理速度的問題

                                        
WAITVAR  DATA				將VARSTRING 中的變數 DATA名稱取出來換成
					WAIT waitstring,timeout的格式
                                        例如:
                			VARSTRING DATA = 'ABC >>,2000'
					WAITVAR DATA
					會變成:
					WAIT ABC >>,2000
 
VARSTRING TEST = 'ABC = GOOD,10000'     如果UUT 傳送的字串是 ABC HELLO
SAVEWAIT ON				則等到的字串GOOD內容值是
WAITVAR TEST				GOOD = ABC  HELLO
SAVEWAIT OFF
ECHO = GOOD                                     


FINDPCFILE     TimeInterval filename	尋找檔案是否存在,是否是在指定的秒數中產生的
					TimeInterval: 允許在多少時間範圍內,以秒為單位
					filename: 要找尋的檔案路徑和名稱.

					例:
					FINDPCFILE  60 C:\TD.TXT
					
					表示尋找 TD.TXT檔案是否存在,是否是在60秒內所
					產生的檔案.
					VARSTRING TEST = '60 C:\TD.TXT'
					FINDPCFILE = TEST
					結果和上述相同.
					找到的話
					VARSTRING BFINDPCFILE = TRUE
					沒找到的話,或著超過時間
					VARSTRING BFINDPCFILE = FAIL

                                        可以使用*號,但只會使用第一個找到的FILE做比對
					FINDPCFILE 60  C:\T*.TXT
 

WAITFILE	waitstring,timeout	是等待某個目錄內是否有waitstring的檔案名
					稱出現,timeout等待時間(1000)表1秒Default
					是3分鐘: 
					例: WAITFILE C:\TEMP\TEST.TXT,1000  
					表示等TEST.TXT這個檔案一秒鐘,超過時間就
					FAIL,如果要以這個通知錯誤,可用
					UUT_FAIL.DAT
					來告知其失敗:  
					要放在同宣告的相同路徑中C:\TEMP\ 

					例: WAITFILE = ABC,1000
  					表示要從VAR.INI中的字串變數ABC取出檔案路
					徑,可以用此來驗證某個檔案是否存在




WAITNOW	        waitstring,command,type,number
					
					等待COM port,Lan 送過來的資料核對,如果存
					在所收到的字串,則由type所定義的傳輸方法,
					將字串回傳回去,並傳送多少次number
 					
					
					type: 1,2表com port 傳輸, 3表 Lan 傳輸

					例:  WAITNOW  {,d,1,20
					==> 等到 { 字串, 使用 com port 送出 d 這
					    個字元 20次
					例:  WAITNOW  {,d@2,1,20
					==> 等到 { 字串, 使用 com2 port 送出 d 
					   這個字元 20次

					在後面需要等到某個字串收到後要下
 					
					WAITNOW OFF  才會關掉這個功能





SLEEP		delay-time	  delay ms times ==> SLEEP 1000   
					(1000 =  1 second)不作任何事

SMB		name			設定usi smart battery borad電源 
						refrence 
					DIO.INI [ACHI] 
					setion & name ==>
					 SMB OperaTionChargeTest1 

KEY		data			由dio介面送 key值到 UUT 鍵盤 ==> KEY A 
					不含ENTER,參考DIO.INI [KEY]鍵值 和
					[DIO] KEYDATA 的DIO port 設定

KEYSTRING	data			由dio介面送字串到 UUT keyboard 
					==> KEYSTRING  test? 
					(?is enter) 其餘設定同 KEY的資料
					透過dio介面送資料,一個字元一個字元的傳
					送

DAC		name			設定 DAC資料參考DIO.INI [DAC] setion & 
						name
					==> DAC SINWAVE ON  (ON | OFF),即NI 
					analog 輸出設定


PULSE           NAME  ON/ OFF		設定COUNTER 輸出方波訊號,可設定所需的頻
					率,設定資料參考
					DIO.INI [PULSE]  setion 
					==> PULSE  P200 ON 輸出名稱為P200的頻率.
					    PULSE  P200 OFF 結束關閉P200的輸出




ALLKEYTEST	delay-time		可以修改 DIO.INI [ALLKEY] setion
					的值來產生輸入順序
                                        
POST		data,timeout		經由LPT PORT接收等待post code data
					==> POST A0,3000  
					timeout等待時間(1000)表1秒Default 是3
					分鐘 

LPTW		data			寫資料到LPT PORT,分為二種格式,寫Line 
					and 寫 port
				port => 0:data port; 
					1:Status port 
					2:control port
					要寫line則要有三個資料:
					LPTW  port,line,data  
					==>  LPTW  0,2,1    
					data只能為0,1
					寫 port 則只有二個資料
 					LPTW  port,data  ==>  LPTW 0,234         
					data < 255


LPTR		data = varName		寫資料到LPT PORT,分為二種格式,寫Line 
					and寫 port
			port => 0:data port; 1:Status port 2:control port
					要寫line則要有三個資料:
				LPTR  port,line = varName  
					==>  LPTR  0,2 = MYTEST   Line只能為
					0-7寫 port 則只有二個資料
 				LPTR  port = varName
					==>  LPTW 0 = mydata    
					會存到變數mydata中可以再配合varrange來
					判斷對錯或著用if-then-else來決定
					
					目前只支援EPP MODE,請先將BIOS的設定改成
					EPP MODE 這個command才能用

#這個命令拿掉不用了
# RJ1145	NON			經由 DIO.INI [RJDATA] setion 的設定,要配
#					合function Board來產生 loop back 功能,用
#					在IBM UUT


END		NON			測試結束時要加這個資料,才能得到測試完成
					的結果  
					例 ==> END

ERRORCODE	data			如果UUT端沒有定義錯誤碼,可自行設定測試流
					程中的錯誤碼 
				==> ERRORCODE 0001, UUT端可透過COM port送
				        error code到HOST格式如後ERROR-CODE:0001
					,ERROR-CODE:會被忽略只保留 0001
					如果加 > 號後面的字將會在 buglist中出現
					其錯誤的資訊
					ERRORCODE 0001 > TEST FIRST


TDERRCODE	data			這個是TD設定的ERRORCODE,這個ERROR CODE和
					ERRORCODE 的定義相同,都會送到SFIS,但不參
					與程式的Retry動作,程式的retry還是以
					ERRORCODE 為主,不會跳到往前的
 					TDERRCODE
 
				==> TDERRCODE 0001, 
					
					如果加 > 號後面的字將會在 buglist中出現
					其錯誤的資訊
					TDERRCODE  0001 > TEST FIRST
					



SENDBARCODE	NON		透過NI DIO 將Barcode經由 UUT keyboard 
					送到 UUT  端
				==> SENDBARCODE

YESNO		data			設定message box 讓使用者確認 YES OR NO,
					按YES會送'YES'到 log file並且繼續執行下
					面的指令,按NO 會送'NO'到log file並且顯
					示錯誤碼,停止執行其它指令,data為顯示字
					串

					YESNO  = ABC 可單純顯示變數字串,但需存
					在 VAR.INI之中
					如不存在則會顯示 ABC: OK

SELECT		data			設定 select box 讓 USER 選擇要使用那一
					個,USER 選擇後會依選的順序存到 VAR.INI 
					中的[VARSTRING] 中的 SELECT 變數中要顯
					示的項目用 ' , ' 來分隔,依順序會存成 
					1,2,3...的值
					SELECT  test1,test2,test3 會產生三個選
					項 test1~3
					



CLOSESMB	NON			關閉所有smart battery board的電源設定	


COUNTER		name			參考 DIO.INI  [COUNTER] setion & name
					==>COUNTER VGAMODE 
					主要在量取全波和半波的比值,由上下限來判
					斷正確與否
					COUNTER  VGAMODE = MYTEST 結果會存到 
					VAR.INI中的MYTEST變數中
					COUNTER  VGAMODE = MYTEST >> 則會將資料
					也存到VAR.INI中的savevar section 的變數
					資料,最後會加到 testlog.txtvar之中,不判
					斷對錯 
			
					COUNTER  VGAMODE >> 則會將資料也存到
					VAR.INI中的savevar section的變數資料用
					errorcode為名稱,最後會加到
					testlog.txtvar之中,會判斷對錯 


SENDMAC		Dos-command		經由 barcode.ini取得 MAC data ,
					Dos-command 是UUT端要寫入MAC資料的 DOS 
					指令(by chipset	support),指令會透過com 
					port結合Dos-command 和MAC 資料來執行,如
					果COMMAND要和MAC連在一起則下 Command~
					則指令會成為CommandMAC不然是成為
					Command  MAC
					

SENDGUID	Dos-command		經由 barcode.ini取得 GUID data ,
					Dos-command 是UUT端要寫入GUID資料的 DOS 
					指令(by chipset support),指令會透過com 
					port 結合Dos-command 和GUID 資料來執行,
					如果COMMAND要和GUID連在一起則下Command~ 
					則指令會成為CommandGUID 不然是成為
					Command  GUID 


WRITEBARCODE	Dos-command		經由 barcode.ini取得 BARCODE data , 
					Dos-command 是UUT端要寫入BARCODE 資料的 
					DOS指令(by chipset support),指令會透過
					com port結合Dos-command 和BARCODE 資料
					來執行,如果COMMAND要和BARCODE連在一起則
					下 Command~ 則指令會成為CommandBARCODE 
					不然是成為
					Command  BARCODE 
					exp:
					WRITEBARCODE  UUT /A/B ,2,5  
					==> UUT /A/B 
					為UUT 端的命令,而,2,5表示barcode 由第
					二位取長度5來送就會成為 UUT /A/B 23456
					送出去




FAILSTOP				由FCTCOMMAND 主動呼叫的fail stop.沒有參
					數

DOSCMD					可以使用DOS 相關的命令,會取得回應值,例如:
                                        DOSCMD ipconfig
					DOSCMD ping 127.0.0.1
					DOSCMD adb devices
                                        可以使用變數名稱:
					VARSTRING MYIP = 'ipconfig'
					DOSCMD = MYIP
					其效果等同
					DOSCMD ipconfig
                                        呼叫BAT FILE 時需給全部路徑
                                        注意事項:
                                        1.給路徑時要給磁碟機代號
                                        2.路徑名稱中不要有空白和 . (點)的符號,會
  				          誤判
					3.bat file一定必需加入.bat的附檔名,因為這
					  是判斷是否為bat file的標準

			doscmd   adb push f:\battloop.txt  /storage/sdcard0/DCIM
			doscmd  dir/w d:\
			doscmd  f:\battloop.txt

                     DOSCMD D:\USIPROJECT\IMAGE\NCR\Release-0410_TDD\flashall.bat

SAVETOFILE command data			可將所要的文字存成檔案,command有下列幾個
					CLEAR 清除之前所寫的資料
					ADD   加入所要的文字
					NAME  要存的檔案名稱.


					ON 從這個命令後的字串等同使用ADD 加入
					OFF　結束自動加入的命令
					ON/OFF只作用在LAN, COM等從外來輸入的字串

					,例如:
                                        SAVETOFILE CLEAR   
					SAVETOFILE ADD  DIR/W C:\
					SAVETOFILE ADD  ECHO TEST
					SAVETOFILE NAME C:\MYTEST.BAT
					SAVETOFILE ON
					SAVETOFILE OFF

					上面的功能
   					1.清除資料
					2.加入字串 DIR/W C:\
					3.加入字串 ECHO TEST
					4.將加入的文字,存成檔案名稱C:\MYTEST.BAT
					5.開始加入字串
					6.結束加入字串
command data 也可以使用字串取代
varstring test1 = 'ADD DIR/W C:\'
varstring test2 = 'NAME C:\MYTEST.BAT'
SAVETOFILE = Test1
SAVETOFILE = Test2





LOADFILE  data			可將所要的文字檔案,從檔案載入到FCT COMMAND的目錄
                                例:
                                 LOADFILE F:\MYTEST.TXT
                                 LOADFILE F:\MYTEST.BAT

                                如果要等文字檔中的資料可用下列方法.
				WAIT
				LOADFILE F:\MYTEST.TXT
				WAIT B0:05:94:FD:B2:96,5000
 

*********************** GPIB FUNCTION******************************************
POWERSAFE	ON/OFF			設定ON 時,一但電源測試錯誤立即斷電,OFF時
					可以重試,default為OFF


GPIBCONFIG	name			經由 DIO.INI [GPIBConfig] setion & name
					==>GPIBConfig AAA
					透過GPIB來設定 PowerSupply或GPIB介面的設
					備

SETHPPOWER	name			經由DIO.INI  [HPPOWERSET] setion & name
					資料來設定GPIB
					PowerSupply ==>SETHPPOWER SET37V

READGPIBDATA	name			經由 DIO.INI  [GPIBDATA] setion & name的
					資料來設定比較值==>READGPIBDATA HPCurrent,
					可借由TYPE 選擇是要讀取電壓或電流值再與 
					UP & LOW 值比較後回傳TRUE OR FASLE
					READGPIBDATA HPCurrent = ABC 
						可將回傳的資料存到變數中
					READGPIBDATA HPCurrent = ABC >> 
						則會將資料也存到VAR.INI中的
					savevar section 的變數資料,最後會加到
					testlog.txtvar之中,不判斷對錯 
					
					READGPIBDATA HPCurrent  >> 會自行判斷對
					錯,會將資料存到VAR.INI中的
					savevar section 的變數資料用errorcode為
					名稱,最後會加到testlog.txtvar之中會判斷
					對錯


HPOUTPUT	ON/ OFF			經由 GPIB介面設定POWER 輸出是ON or OFF
					==> HPOUTPUT ON

GPIBSTR		DATA			DATA字串透過GPIB PORT來送到GPIB DEVICE

					GPIBSTR  =  字串變數名稱
					可借由變數來產生命令列
 					VARSTRING  MYDATA = '*IDN?';
					GPIBSTR = MYDATA 

					

GETGPIBSTR	DATA = varName		DATA為要對GPIB PORT下達要回傳資料的
					COMMAND,需給變數參數名稱
					GETGPIBSTR CURR:STATE = ABC 
					    等號前面為DEVICE COMMAND,後面為要
						存的變數名稱ABC
					GETGPIBSTR CURR:STATE = ABC >> 
						則會將資料也存到VAR.INI中的
					savevar section 的變數資料,最後會加到
					testlog.txtvar之中,不判斷對錯 
					
					如果沒有= varName就會直接將讀到的資料放
					到VARSTRING 中的 GPIBQuery中

GPIBCOMPARE    DATA			DATA為要比對的資料,由GETGPIBSTR 傳到
					VARSTRING 中的 GPIBQuery.會自動比對
					如果DATA 中的資料存在 GPIBQuery中
					就會傳回pass,否則的話會引發UUT-FAIL

					GETGPIBSTR *IDN?
					    因為沒有= 到變數所以會存在
					VARSTRING GPIBQuery中
					再下:

					GPIBCOMPAR 6632B 
						則會比對GPIBQuery中的字中是否
					包含有6632B這個字串
					
					
*********************** VISA  FUNCTION****************************************

VISA  Command  DATA			主要是透過NI VISA界面來控制所有可由VISA
					存取的界面,如COM ,GPIB,USB...等等

                                        Command 區分為
                                        1.FindResource
  					2.RsrcName 
					3.OPEN
					4.CLOSE
					5.WRITE
					6.READ
1. FindResource 為尋找本機是否有相關可連線的 VISA Device,會將所找到的資源放到 
		LOG 中,以供判斷是否要做後續控制 VISA的動作.

                VISA FindResource

2. RsrcName DATA	為所找到的 resource 字串設定,其為指定VISA Device 使用
			,Data要設定成所要連結的sorce 字串,一定要先設定之後才能
			使用 OPEN CLOSE, WRITE,READ等命令,不然無法使用以下四個
			命令

		VISA RsrcName  USB0::0x0957::0x0507::MY44003692::INSTR
		VISA RsrcName  ASRL3::INSTR
                VISA RsrcName  = DATA 表示由VARSTRING中找出名為DATA的字串來替代



3. OPEN		為打開所指定的設備,沒有 DATA 參數
		
		VISA OPEN


4. CLOSE		為關閉所指定的設備,沒有 DATA 參數
		
		VISA CLOSE

5. WRITE  DATA	為依據所打開的 Device 使用手冊下達其相關的指令 
		
		VISA WRITE  *IDN?
                2.3.5.6 版本支援
                VARSTRING TEST = 'WRITE *IDN?'
                VISA = TEST
                等同 VISA WRITE *IDN?


6. READ   varName  需配合 WRITE 來操作,沒有WRITE 不會有READ的資料可讀
		  VISA PORT 下達要回傳資料的COMMAND,需給變數參數名稱 varName
		  VISA READ = ABC 後面為要存的變數名稱ABC,會存入VARREAL 變數
				中,所以一定要是實數資料如果不是實數資料要配合 
				  SAVEWAIT來做

		  VISA READ = ABC >> 則會將資料也存到VAR.INI中的savevar 
				     section的變數資料,最後會加到
				     testlog.txtvar之中,不判斷對錯 			


******************************************************************************

ACHWAVE		name  			經由 DIO.INI [ACHWAVE]取得ACH wave 高點
					和低點差值是否在top<->low的區間內
					==> ACHWAVE AUDIO 
					可存到變數名稱中 ACHWAVE AUDIO = ABCD 
					ACHWAVE AUDIO = ABC >> 
					則會將資料也存到VAR.INI中的savevar 
					section	的變數資料,最後會加到
					testlog.txtvar之中,不判斷對錯 
					
					ACHWAVE AUDIO   >> 會自行判斷對錯,會將
					資料存到VAR.INI中的savevar section 的變
					數資料用errorcode為名稱,最後會加到
					testlog.txtvar之中


ACHFREQ		name			經由 DIO.INI [ACHFREQ]的設定可以判斷 頻
					率,offset, 峰對峰的值差,次頻率傅利頁轉
					換的大小值
						ACHFREQ  FEI
                                        
					可存到變數名稱中 ACHREQ FEI = ABCD 會自
					動以ABCD產生四組資料
						ABCD1 = 峰對峰的值差
						ABCD2 = OFFSET
						ABCD3 = 頻率
						ABCD4 = 次頻率的傅利頁轉換的值

					ACHREQ FEI = ABCD >> ,不判斷對錯,會將資
					料也存到VAR.INI中的
					savevar section的變數資料,最後會加到
					testlog.txtvar之中但只存二個值Offset&頻
					率
						ABCDO = OFFSET
						ABCDF = 頻率
 
					
					ACHREQ FEI  >>會自行判斷對錯,會將資料存
					到VAR.INI中的savevar section 的變數資料
					用errorcode為名稱,最後會加到
					testlog.txtvar之中但只存二個值 Offset & 
					頻率
						errorcodeO = OFFSET
						errorcodeF = 頻率

         



DACPOINT	name 	ON/OFF		經由 DIO.INI [DACPOINT] setion & name來
					設定固定的DAC輸出電壓
					===>  DACPOINT V3P7 ON /OFF
					也可以使用VARREAL的變數來設定其值
					 DACPOINT V3P7 = MYDATA       
					MYDATA是實數變數,可在設定前給定
					例如 VARREAL MYDATA = 3.55

                                        

//以下為直接控制NI CARD DIO
NIDIO		name  value		參考 DIO.INI  [dio] setion & name
					==>NIDIO DATA1 255
					name 可在DIO.INI中自行設定所需的資料


NIDIOREAD	name  data		參考DIO.INI [dio] setion-name 設定name 
					& 比較資料data 如果NI DIO 取回的資料和
					data 相同則 TRUE 否則回傳 FALSE 
					   NIDIOREAD  MYDIO 233
					可以存到變數中來判斷 
					NIDIOREAD  name = ABCD
					再以 
			IF ( ABCD > 234 ) THEN @ERROR1 ELSE @ERROR2

					NIDIOREAD  name = ABC >> 
					則會將資料也存到VAR.INI中的
					savevar section的變數資料,最後會加到
					testlog.txtvar之中,不判斷對錯
	
					NIDIOREAD  name DATA1 >> 會自行判斷對錯
					,會將資料存到VAR.INI中的savevar section
					的變數資料用errorcode為名稱,最後會加到
					testlog.txtvar之中


NIDIODIR	name			參考 DIO.INI  [NIDIODIRECT] setion & 
					name 可以直接控制NI CARD的IN OUT 
					的方向 ---> 
					NIDIODIR PORT0 
					NIDIODIR PORT1 
					NIDIODIR PORT3

/*					大範圍的mark,其功能同c++的功能,需配合 */
					作為結束

RUNPCEXE	DATA	DATA為執行檔在pc端的路徑,檔案名稱,如果
					該程式己經存在可配合Pfindexe.exe來找程
					式來執行可避免重複執行
					RUNPCEXE  Pfindexe.exe 要執行的exe 其
					程式的caption
	==>RUNPCEXE  Pfindexe.exe   C:\WINDOWS\system32\calc.exe "小算盤"
	==> RUNPCEXE = ABC    則會到 var.ini找字串變數ABC來代入執行
        ==> RUNPCEXE "C:\PROGRAM FILE\ABC B.EXE " 如果路徑有空格要用" 包起來
        ==> RUNPCEXE "C:\PROGRAM FILE\AA.EXE ;/A/B"有參數的話也要包起來並在參
					數前加上分號以為區分



EXECLOSE	DATA	如果以Data為 caption 的視窗存在的話,將其
					程式關閉


RUNSTR		DATA			DATA為存在COM.INI中[IMAGE] section 中KEY名
					稱程式會主動到Com.ini 中找到 [SYMBOL] section  
					的APPATH名稱將 APPATH 和  DATA 所指的資料結
					合變成所需要的版本來執行其中有要取代的字串可
					用 # 號表示，則會到SYMBOL.INI中的USB Section
					中按form 的caption取得其值，取代# 這個符號所
					在的位置
		例如:
		COM.INI
		[SYMBOL]
		APPath=D:\HexLoader.exe	
		[IMAGE]
		 Monitor= /u # /d 3 \IMAGE\MC3000\30XXc50AenMO0133XX.hex
		SYMBOL.INI
		[USB]
		DEVICEID =ABC
	
		RUNSTR Monitor
		會產生執行
		Runpcexe D:\HexLoader.exe /u ABC /d 3 \IMAGE\MC3000\30XXc50AenMO0133XX.hex



IF					
					每一個數之間要有空白, 字串前後要加 ' 號 
					=> 'abcd' 要有跳
					的位置 THEN @abc ELSE @123  運算符號間
					要有空白區隔其找尋是從最前開始往後找所以
					要避免重覆.

				IF ( BOX1 = 'ABC' ) THEN @ABC ELSE @ERROR  
						字串比對BOX1是字串變數
				IF ( BOX1 = BOX2 ) THEN @ABC ELSE @ERROR  
						字串比對BOX1,BOX2是字串變數    

	IF ( ( USB5V_1 > 4.75 ) AND ( USB5V_1 <  5.25 )  )  THEN @USB5V_11   
					還支援下列組合:
					 NOT * / AND + - OR XOR >  <  >=  <=  
					<>  =
					<> 表示不等於

	使用變數	
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

	使用字串
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



FLAG		DATA 			主要使用在Retest 時當做啟始位置的判斷
					可以減少已做過的項目重覆再做,但編流程
					的人必需自行針對
					FLAG 0 
					FLAG 1
                                     

@NAME					Label 給jump 時使用

JUMP		Label			JUMP @123 跳到所標示的位置
					另外也可給其字串變數指示其要跳的位置
					VARSTRING  MYJUMP = @TESTJUMP

					JUMP = MYJUMP
					這個結果會和
					JUMP @TESTJUMP 的作用相同

***********  各各變數名稱宣告不能相同******************************************

LAB      Source  Distiation		這個功能在計算color LAB的 Delta E,回傳
					的資訊會放在 VARREAL LABTEMP中,以供後續
					判斷Source 是在DIO.INI section [LAB]中
					的名稱,其存放中間值的 L A B 以空白區隔
					Distianation 是以 VARSTRING 所組合出來
					的L A B字串變數以空白區隔
 


VARREAL		DATA	可事先宣告實數變數,或用來做實數的計算
					VARREAL  ABC,DEF
					VARREAL  HILL = DEF + (ABC -1) / 2
					用於運算時變數必需先前宣告過,但結果變數 
					HILL則不可做16進位運算
					VARREAL TEST1 = 0x1101
					VARREAL TEST2 = 0x101
					VARREAL TEST3 = TEST1 AND TEST2
					
					可以使用動態變數名稱宣告
  					TEST1 是VARSTRING 或著 VARREAL的內存值
					例如 VARSTRING TEST1 = 'MYVAR' + '1'  '2' '3'
					則 TEST1 字串會變成 MYVAR1 如果後面使用
					COUNT 來逐次加則會出現 MYVAR2 MYVAR3 

					VARREAL  TEST1 << DEF + (ABC -1) / 2
 					則上一行式子會存到 VARREAL 變數中以 
					MYVAR1 為名稱存檔
                                        例:
                      VARREAL ICOUNT = 2
                      VARSTRING TEST = 'MYVAR'+ ICOUNT 
                      
                      VARREAL TEST <<  ( 20 * 2 )

                      這時會產生一個 MYVAR2的 VARREAL 變數值為40
                      使用 ECHO = MYVAR2 會顯示 40




STRHEX          DATA			沒有變數和字串時為設定目前所要設定HEX的
					長度,
					STRHEX 12   表示所得的結果都是以12位的資
						    料長度來存,除非下次再修正
					其它的規則同VARREAL 的運用.
					只有在需要得到HEX 字串時才需要使用
					
					VARREAL ABC = 123                  
					STRHEX 12
					STRHEX HEX = ABC
					ECHO = HEX
					結果=> 00000000007B
					因為123為10進制的資料


					
					VARREAL ABC = 0X123                  
					STRHEX 12
					STRHEX HEX = ABC
					ECHO = HEX
					結果=> 000000000123
					因為123為16進制的資料


					16進制的要如下的算法前面為 零X 不是英文字O
					STRHEX  12
					VARREAL HEX1 = 0X000FFF
					VARREAL HEX2 = 0X00F
					STRHEX HEX3 = HEX1 + HEX2
					ECHO = HEX3
					會顯示  00000000100E
	


VARSTRING	DATA			可事先宣告字串變數,或用來做字串的運算
					VARSTRING   ABC,DEF
					可存字串變數 
					VARSTRING  ABC = DEF + '1234567'
					其結果為 字串變數DEF加上1234567的結果存
					到ABC的變數字串中,如果DEF不存在則是給空
					字串可以使用動態變數名稱宣告
  					TEST1 是VARSTRING 或著 VARREAL的內存值
					例如 VARSTRING TEST1 = MYVAR + '1'

					VARSTRING  TEST1 << DEF + '1234567'
 					則上一行式子會存到 VARSTRING 變數中以 
					MYVAR1 為名稱存檔

 					如果需要加號可用#來取代 + 例:  
					VARSTRING DATA = 'ABC# 234'
					則 ECHO = DATA 會顯示出 ABC+ 234
 					如果需要#號可用2個# 例:  
					VARSTRING DATA = 'ABC##234'
					則 ECHO = DATA 會顯示出 ABC#234

					VARSTRING S1 = 'ABCD'+0X27
                                        ECHO = S1
					得到的值是 ABCD' 
					0X只能設定一個字元.不能使用0X4142
					要用的話只能 VARSTRING S1 = 0X41 + 0X42


                                        

VARRANGE	NAME			將先前存的變數值和 DIO.INI [VARRANGE]的設
					定值比對，看是否在範圍之內，但名稱必須要
					相同才能比較		
					DIO.INI
					[VARRANGE]
					ABC =  1  10
					VARRANGE ABC   
					則會去比較ABC這個值是否在1-10之間
					VARRANGE ABC >>
					會將資料存到VAR.INI的[savevar] section 
					Key值以變數名稱ABC儲存

					 


COMVAR		VARNAME   LINE		可將 COM OR LAN 傳回來的資料存到VARREAL 
					的變數中,如果為數字則可用VARRANGE 來做判
					斷,如果為字串則要使用 IF THEN ELS 的 
					COMMAND 來判斷 LINE 為要抓傳回的字串第幾
					行字串存到 VARNAME 所指定的變數中,此時如
					使用 WAIT 等待字串則會無法使用,必需要等
					到
					**SAVE COMVAR OFF**
					才會恢復正常
					COMVAR  MYTEST   2       
						抓回傳的第二行字串存到變數中
					COMVAR  MYTEST           
						抓回傳的第一行字串存到變數中

					

SUBSTRING    TYPE  NAME  Position Token  可將VAR.INI中的 VARREAL or VARSTRING的
					字串截取出來再存到VAR.INI中
					1.TYPE  = R | S  R:表VARREAL資料 
							 S:表VARSTRING的資料
					2.NAME  表在VAR.INI  VARREAL 或著 
						VARSTRING的變數名稱
					3.Position  表示要存取的字串所在的位置
					4.Token 表示用這個字串當分隔字串, 不填
						則當成以空白字串來分隔

                                        SUBSTRING  R  ABC  3  #        
					    ==>表示 VARREAL 中的ABC 變數以# 
					    來分隔取第三個
                                        SUBSTRING  S  ABC  3  #        
					    ==>表示 VASTRING 中的ABC 變數以# 
					   來分隔取第三個
                                        SUBSTRING  S  ABC  3  # = TEST  
					     ==>表示 VASTRING 中的ABC 變數以#
					     來分隔取第三個,然後存到 TEST變數中

                                        SUBSTRING  S  ABC  3   = TEST  
					    ==>表示 VASTRING 中的ABC 變數以'空白'
					    來分隔取第三個,然後存到 TEST變數中

SUBSTRING2   TYPE  NAME  Start Length  可將VAR.INI中的 VARREAL or VARSTRING的字
				      串截取出來再存到VAR.INI中
				1.TYPE  = R | S R:表VARREAL資料 
						S:表VARSTRING的資料
				2.NAME  表在VAR.INI  VARREAL 
					或著 VARSTRING的變數名稱
				3.Start  表示要存取的字串起始位置
				4.Length 表示從起始位置取多長的資料

                                        SUBSTRING2  R  ABC  3  3        
					==>表示 VARREAL 中的ABC 變數從3開始取長
					度3
	 					
                                        SUBSTRING2  S  ABC  3  3       
					==>表示 VASTRING 中的ABC 變數從3開始取長
					度3
					   
                                        SUBSTRING2  S  ABC  3  3 = TEST  
					==>表示 VASTRING 中的ABC 變數從3開始取長
					度3然後存到 TEST變數中
                                        SUBSTRING2  R  ABC  3          
					==>表示 VARREAL 中的ABC 變數從3開始取到
					結尾
					  

					  


REPLACESTR  NAME  OLDSUB  NEWSUB	可將VAR.INI 中VARSTRING的字串截取出來更換
					子字串後回存.
					1.NAME 在VARSTRING中字串變數的名稱
					2.OLDSUB 在字串中想要取代的字串
					3.NEWSUB 在字串中替換OLDSUB的字串


				VARSTRING  TEST = 'OK7,ESN_NUMBER=S09174521100049'
				REPLACESTR TEST =  *
				ECHO = TEST

				會變成  OK7,ESN_NUMBER*S09174521100049
				
                             如果沒有給 NEWSUB參數,則表示從字串中刪除 OLDSUB字串




SAVEVARTXT	TYPE*NAME,...		可將變數存到一個檔案之中,可於程式中設定,
					在結束後會存放在TEST LOG的最後面
					 TYPE*NAME, TYPE*NAME,  ......
					
					1.TYPE*NAME, TYPE*NAME,  ......(
						R:表VARREAL資料 
						S:表VARSTRING的資料)
					  SAVEVARTXT  R*DATA1,S*DATA2,R*DATA3
					

TIMESTRING     Formate			可依格式取得系統時間,放於 VARSTRING MYTIME中,
					要使用時可呼叫 MYTIME 取得變數.
 					例:
					TIMESTRING   mm/dd/yyyy hh:nn:ss
					MYTIME = 11/10/2015 14:54:40
 					可用格式如下:

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
例:
d/m/y = 5/6/00
dd/mm/yy = 05/06/00
d of mmm yyyy = Mon 5 of Jun 2000
  

//主要用在希望借由程式自動校正每一台機台不同參數時使用.
GetINIData    Section  name  TYPE  INITYPE			
  					可由symbol.ini 中的section 和 
					name 中取出資料放到 var.ini 中的
					VARSTRING or VARREAL 的 section中
					以相同的名稱name 來存放 
					
					TYPE :  R  / S   R:表示放 VARREAL 中
							 S:表示放到 VARSTRING中
					
				GetINIData   VCC  VCC3  R 
					==>表示從 symbol.ini 中的VCC Section 
					取名稱為VCC3的值放到 var.ini 中的 
					VARREAL Section 中名稱為  VCC3
				GetINIData  VCC  VCC3  S 
					==>表示從 symbol.ini 中的VCC Section取
					名稱為VCC3的值放到 var.ini 中的 
					VARSTRING Section 中名稱為   VCC3


      INITYPE 表示要從那一個INI FILE 來抓資料,不給就只會從Symbol.ini中抓
      1:Barcode.ini
      2:change.ini
      3.GB.INI
      4.DIO.INI
      5.COM.INI
      



SaveINIData   Section  name  TYPE	可由var ini 中的 TYPE 和 name 中取出資
					料放到 symbol.ini 中的 SECTION中以相同
					的名稱 name 來存放
					TYPE :  R  / S   
						R:表示從 VARREAL 中取出
						S:表示從 VARSTRING 中取出
					
				SaveINIData  VCC  VCC3  R 
					==>表示從 var.ini中的VARREAL Section 
					取名稱為VCC3的值放到 symbol.ini 中的
					VCC Section 中名稱為 VCC3 的地方
				SaveINIData  VCC  VCC3  S 
					==>表示從 var.ini中的VARSTRING Section 
					取名稱為VCC3的值放到 symbol.ini 中的 
					VCC Section 中名稱為 VCC3 的地方


		


					  
******************************************************************************


UIMACRO		NAME			可事先於 DIO.INI中的 [UIMACRO] 中定義所
					要的COMMAND,如此可以簡單的命令來下達,可
					參考
					INIREADME UIMACRO  PORWRON


TIMESTOP	DATA			可設定其多久程式要停止,當其時間到時會將
					VAR.INI中的 字串  TIMESTOP=TURE
					DATA ==>  ON stoptag  其stoptag 以分為
					計算單位  TIMESTOP ON 3 
					==>表示計時到三分鐘後結束
					TIMESTOP OFF 則即時關掉計時
					主要使用在AUTO RUN時做LOOP 要做多久的
					設定要設定AUTO時要設定Barcode.ini中的
					[logfile] 中的 AUTO=TRUE;


ECHO		DATA			可將DATA 的文字顯示到 LOG FILE 中; 如果
					用 ECHO = ABC表示顯示變數值,不存在會顯
					示 NON DATA,如果MESSAGE ON的話,也會顯示
					到其中在字串中加 ~ 會自動換行  
					ECHO ABCD~ABCD


MESSAGE		ON / OFF		可以將訊息視窗顯示,可透過 ECHO的 Command
					來更改示窗資料    

INPUTBOX	CAPTION = VARNAME,length
				 	可在INPUTBOX中將輸入的字串存到 VARNAME
					的變數中,CAPTION是要顯示的說明字串
					INPUTBOX  MY BARCODE = BARCODE 則輸入的
					資料會存到VAR.INI中的VARSTRING中的
					BARCODE變數中.  

					INPUTBOX  TEST = MYVAR,20
					表示輸入的CAPTION 是 TEST
						  存到變數  MYVAR
						  變數長度  20 
					長度沒輸表示沒有限制,也不會限時輸入完畢
					有長度時必需在1sec 內輸完,含enter key
					
                         

LAN             dos command   經由lan送資料到 UUT端ON / OFF用來設定
					LAN的開關
					LAN ON  4000    / LAN OFF 
					在on 時可改變lan 的port 值,在ON的後面加
					上Port的值即可
					LAN  SEND-COMMAND-String
					也可以用 = 後面接變數的方式來傳送
					SAVEBARCODE

				VARSTRING FEI = 'C:\ABC\ABC.EXE '+ BARCODE
					LAN = FEI  用字串變數來送參數

					
					程式中有二個以上的Client連接PUSIGB可設定
					@@1, @@2, @@3 等來表示要將資料傳給那一個
					Client,不指定則是傳給第一個連上來的
					Client.
				LAN ABCDEFG  @@2  
					表示把 ABCDEFG 字串傳給第二個連上來的
					Client	

CLAN            DATA  經由lan送資料到 SERVER 端ON / OFF用來設定
					CLAN的開關
					CLAN ON  4000    / LAN OFF 
					在on 時可改變lan 的port 值,在ON的後面加
					上Port的值即可
					CLAN ON 4000 127.0.0.1可以改變所要連的
					SERVER IP

					CLAN  SEND-COMMAND-String
					也可以用 = 後面接變數的方式來傳送
					

				VARSTRING FEI = 'C:\ABC\ABC.EXE '+ BARCODE
					CLAN = FEI  用字串變數來送參數

				其SERVER IP PORT會和BARCODE FORM使用一致的設定
				會在BARCODE.INI 或著在CHANGE.INI中設定SFIS的IP
				和PORT的地方

   範例:
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




	
					

TOBARCODEFORM   Type,Data   		經由 TCP/IP 送資料到 Barcode form
					1: 表示所送的資料為 MAC data 
					2: 表示所送的資料為 GUID data 
					3: 表示所送的資料為 SSN data
					
					4: 表示所送的資料為 SN2 data
					5: 表示所送的資料為 MO_NUMBER data
					
					TOBARCODEFORM  1,123456789012


					也可以用 = 後面接變數的方式來傳送
					VARSTRING FEI = '1,'+ MACCODE
					TOBARCODEFORM = FEI 用字串變數來送參數

					1)測試前若 GUID欄位有輸入,會送給 SFIS
					作檢查
					2)可用 TOBARCODEFORM 命令直接於
					FCTCommand 內編輯送 MAC 或 GUID 及其後
					之欄位資料給 SFIS 的字串
					(記得要 LAN ON)
					Example:
  					a. 送單一MAC:  
     					TOBARCODEFORM = 1,123456789012
     
     					送多個MAC:  
     	VARSTRING PATH = '1,MAC1=000000000001 MAC2=000000000002 MAC_CNT=2'
     	TOBARCODEFORM = PATH
 
	VARSTRING PATH1 = '1,MAC1=' + GUID + ' MAC_CNT=1' + ' OTHER_MAC1=' + WLAN_SFIS
 	VARSTRING PATH = '1,MAC2=' + MAC + ' OTHER_MAC1=' + WLANMAC
 
  					b. 只送GUID:  
     					TOBARCODEFORM = 2,1234567890123456
     
     					GUID後的欄位也送:(這部份各專案要跟SFIS 
					討論哪個欄位能填資料，以 D9900	為例，
					SFIS提供 GUID 後一欄位送其他資料，記得
					要用逗號隔開)
VARSTRING PATH = '2,0010207318112233,CSN1=00000000000001 CSN2=00000000000002'
    TOBARCODEFORM = PATH
 
					PS. 以上功能適用於 SendBarcodeOnly=OFF
					及 ShopFlow=ON 的情況
 

					
					在Barcode form 收到資料後會回傳DATA的值
					可依這個來判斷Barcode from是否收到



CASE		DATA			DATA值為字串變數存在在VAR.INI中的
					VARSTRING中可依據DATA來找要JUMP的Lable
					如果要組合字串可用 
				VARSTRING FEI = VAR1 + VAR2 + VAR3 
					然後用
				CASE  FEI
					如果DATA 的字串變數值不存在則會跳到 
				@ELSE
                                        所以其後一定要設定一個 @ELSE 的
					Lable
                                          

SAVEBARCODE	NON			會存在VAR.INI中的 VARSTRING section中,
					以變數名稱BARCODE,MAC,GUID的名稱存字串
					變數,如果有多個MAC的參數存在 MultiMAC 
					section 會存到MAC1,MAC2...的變數中.
					最後SCAN的 Mac code 會在Control中,其它
					的會放在MultiMAC 按輸入的順序存放

					2.2.5.9版本以後會多存一個系統目前時間
					會放在TIMENOW



HOSTIP		DATA			會將HOST IP Address 存到 VAR.INI中的 
					VARSTRING section中,以變數 DATA 為名稱
					存在變數中 ==> HOSTIP  MYIP  會將 
					IP address 存到 MYIP的變數中 


GETINI		SECTION	NAME VARNAME	會將Prod\symbol.ini 中的 section- name
					的資料存到字串變數 VARNAME 之中,以提供
					程式中來存取使用,在symbol.ini中主要設
					定和local pc相關的變動資料,因為可能每
					台pc值會不同,所以單獨設定在此供 
					fct command 使用,
					例如 usb id , com port BT MAC 等等
					GETINI MAC 1  MYMAC ==>這段是到 
					Symbol.ini 中的MAC section ,名稱為 1 
					的值存到var.ini的字串變數  MYMAC 中
  		在SYMBOL.INI 中的設定
 		 [MAC]
   		1= ABCD12345678
   		2= TESTABC
					如此我們可以將FCTCOMMAND 一致化不用每
					台PC要設定不同的流程



GETSYSTEMBOM    NAME			會取得所在PROJECT 中SYSTEMBOM.INI中
					CONFIG section 的相關資料,取得資料後
					會放到 var.ini中字串變數 MYBOM 中
					
					例:
  					 GETSYSTEMBOM  0001
       
					表示由 systembom.ini中的config section
					中取ID 為0001的資料放到var.ini中字串變
					數MYBOM 中

					例:
  					 GETSYSTEMBOM  = ABC
       
					ABC 為VAR.INI中的字串變數,將其取出給其
					當作ID 再由 systembom.ini中的
					config section中取ID 的資料放到var.ini
					中字串變數MYBOM中



SAVELOG		NON			會將目前的LOG 資料先行存檔,不用等到最
					後按完成才存檔
                                        如果NON 為檔案路徑和檔名,則會將LOG存到
					指定的目錄中.

CLEARLOG	NON			清除目前的所有LOG 並依Barcode和Time來存
					檔

GETTIME		ON/OFF 			當以 GETTIME ON時系統會開始計時,到
					GETTIME OFF時會將其間的時間存到
					[VARREAL]中GETTIME變數中以ms為單位

********************************************************************************

UUT 端可利用 COM PROT 或 LAN  回傳以下列為起始的資料,則 HOST會當成單獨處理資訊

*******************************************************************************
ERROR-CODE:0001				會在主程式顯示UUT目前測到那個ERROR 項目
ERROR-UUT:0001				會將主程式的ERROR CODE 改成 0001

UUT-FAIL				會通知主程式測試失敗,做結束的動作

VARSTRING  ABC = 'TEST DATA'		會將Client端送過來的 TEST DATA 存到 
					VAR.INI的 VARSTRING中的 ABC中,設定方法
					可參考 VARSTRING 的 COMMAND
VARREAL    ABC = 23			會將Client端送過來的 23 存到 VAR.INI的 
					VARREAL中的 ABC中,設定方法可參考 
					VARREAL 的 COMMAND

