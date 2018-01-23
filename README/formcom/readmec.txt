Command         add-data                 discription

COM		dos command    		經由 com port送資料到 UUT端(含enter) 如果要送空白字
					可以下 COM SPACE (只有一個空白不含enter) 
					COM OFF , COM ON 可開關 COM PORT 
					COM ON 38400  COM2 在ON 時可以設定 COM PORT的傳輸率
							   和指定那一個com port 輸出入
					COM =  字串變數名稱

COMHEX 		ASCII-CODE		可經由 COM PORT送16進位的字串到UUT端.
					COMHEX  313A00  

GETHEX		ON | OFF		可經由 COM PORT 收進來的資料以16進位顯示,控制以ON OFF
					來控制
					GETHEX ON   表示將COM PORT的資料改以16進位值收入
					GETHEX OFF  表示將COM PORT的資料以字串形式收入


                                                          
WAIT            waitstring,timeout	等待COM port送過來的資料核對,timeout等待時間(1000)表1秒 
					Default 是3分鐘: 例: WAIT C:>,1000
SLEEP		delay-time		delay ms times ==> SLEEP 1000   (1 second)不作任何事

END		NON			測試結束時要加這個資料,才能得到測試完成的結果  
					例 ==> END
ERRORCODE       data			如果UUT端沒有定義錯誤碼,可自行設定測試流程中的錯誤碼 
                                        ==> ERRORCODE 0001, UUT端可透過COM port送error code到
                                        HOST 格式如後 ERROR-CODE:0001  ,ERROR-CODE:會被忽略只
                                        保留 0001
SENDBARCODE 	NON			透過NI DIO 將Barcode經由 UUT keyboard 送到 UUT  端
                                        ==> SENDBARCODE
YESNO   	data			設定message box 讓使用者確認 YES OR NO,按YES會送'YES'到 
					COM port並且繼續執行下面的指令,按NO 會送'NO'到COM port
                                        並且顯示錯誤碼,停止執行其它指令,data為顯示字串


RUNPCEXE	data			執行電腦上的應用程式,取com.ini IMAGE section 中的名稱,如果
					其中有要取代的字串可用 # 號表示,則會到SYMBOL.INI中的USB Section
					中按form 的caption取得其值,取代# 這個符號所在的位置

RUNSTR		DATA			DATA有這個參數是存在com.INI中的IMAGE section 中的名稱字串
					程式會主動到Com.ini 中找到 SYMBOL section  的APPATH名稱    
					將 APPATH 和  DATA 所指的資料結合變成所需要的版本來執行
					其中有要取代的字串可用 # 號表示,則會到SYMBOL.INI中的USB Section
					中按form 的caption取得其值,取代# 這個符號所在的位置

					RUNSTR Monitor
					會產生執行
					D:\ibmbeta\GetWinH\Multi-Flash\MultiLoad.exe  (APPATH)
					d:\MC3000\DVT\BSP4.1.002\Hex Images\MC3000C42B\MC30XXC42XMon0115.bin
					(Monitor)

COPYDIR		data			DATA有這個參數是存在com.INI中的IMAGE section 中的名稱字串
					程式會主動到Com.ini 中找到 SYMBOL section  的APPATH名稱    
					將 APPATH 和  DATA 所指的資料結合變成所需要的版本來執行
					在 SYMBOL section 中所設定的為磁碟機 代號,為所要存放的目的
					磁碟機,而 APPATH 是固定的為PDDEClient.exe 使用DDE Protocol
					和 pmcom.exe 溝通.

					COPYDIR FEI
					會將 COM.INI中的[IMAGE] FEI= 檔案路徑 下所有資料複製到相對
					應 SYSBOL.INI中所對應的磁碟機中去.
					

SDCOPY	DATA			


SYMBOLIMG	data			設定symbol usb load程式,data為com.ini [IMAGE] section 中的ID
					名稱例如: SYMBOLIMG Monitor   ; SYMBOLIMG  Partition 等則會
					將所指定的路徑COPY 到所屬的項目中,並按執行

WAITALL         NON                     等所有開啟的視窗都到這時才繼續執行

USBDELAY	delay-time		設定當等到所有視窗時每個視窗往下執行中間的間隔	

SINGLEON	NON			針對Image download比較快速無法同步下載可以配合WAITALL 來使其一起開
SINGLEOFF	NON			始,然後一個一個執行,在 Download完畢後要寫 SINGLEOFF才能使下一個繼
					續 Download,二個command 要配合使用


***********  各各變數名稱宣告不能相同*****************************

VARREAL		DATA			可事先宣告實數變數,或用來做實數的計算
					VARREAL  ABC,DEF
					VARREAL  HILL = DEF + (ABC -1) / 2
					用於運算時變數必需先前宣告過,但結果變數 HILL則不必

VARSTRING	DATA			可事先宣告字串變數,或用來做字串的運算
					VARSTRING   ABC,DEF
					可存字串變數 VARSTRING  ABC = DEF + '1234567'其結果為 字串變數DEF加
					上1234567的結果存到 ABC的變數字串中,如果DEF不存在則是給空字串



VARRANGE	NAME			可用於由先前存的變數值和 DIO.INI中[VARRANGE]中的值做比對,看是否在範
					圍之內,但名稱必須要相同才能比較
					VARRANGE ABC   必須在DIO.INI和VAR.INI中都存在 ABC這個變數才能
					比較
*************************************************************************
@NAME					Label 給jump 時使用

JUMP		Lable			JUMP @123 跳到所標示的位置



CASE		DATA			DATA值為字串變數存在在VAR.INI中的VARSTRING中可依據DATA來找要JUMP的Lable
					如果要組合字串可用 VARSTRING FEI = VAR1 + VAR2 + VAR3 然後用
					CASE  FEI
					如果DATA 的字串變數值不存在則會跳到 @ELSE
                                        所以其後一定要設定一個 @ELSE 的 Lable

ECHO		DATA			可將DATA 的文字顯示到 LOG FILE 中; 如果用 ECHO = ABC表示顯示變數值,不存在
					會顯示 NON DATA,如果MESSAGE ON的話,也會顯示到其中                            

				