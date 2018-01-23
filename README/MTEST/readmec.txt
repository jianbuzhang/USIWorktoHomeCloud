Command         add-data                 discription

COM		dos command    		經由 com port送資料到 UUT端(含enter) 如
					果要送空白字可以下 COM SPACE (只有一個
					空白不含enter) 
					COM OFF , COM ON 可開關 COM PORT 
					
					那一個com port 輸出入
			   		COM =  字串變數名稱
					COM 的設定在symbol.ini [COM] ID
					

COMHEX 		ASCII-CODE		可經由 COM PORT送16進位的字串到UUT端.
					COMHEX  313A00  

GETHEX		ON | OFF		可經由 COM PORT 收進來的資料以16進位顯
					示,控制以ON OFF 來控制
					GETHEX ON 表示將COM PORT的資料改以16進
						    位值收入
					GETHEX OFF 表示將COM PORT的資料以字串形
						    式收入



MCOM		dos command    		經由 com port送資料到 UUT端(含enter) 如
MCOM2					果要送空白字可以下 MCOM SPACE (只有一個
					空白不含enter) 
					MCOM OFF , MCOM ON 可開關 MCOM PORT 
					
					那一個com port 輸出入

			   		MCOM =  字串變數名稱
					
					MCOM 的設定在symbol.ini [COMMON] 


MCOMHEX 	ASCII-CODE		可經由 MCOM PORT送16進位的字串到UUT端.
MCOM2HEX				MCOMHEX  313A00  

								

GETMHEX		ON | OFF		可經由 MCOM PORT 收進來的資料以16進位顯
GETM2HEX				示,控制以ON OFF 來控制
					GETMHEX ON 表示將MCOM PORT的資料改以16進
						    位值收入
					GETMHEX OFF 表示將MCOM PORT的資料以字串形
						    式收入






LAN             dos command    		經由 lan送資料到 UUT端ON / OFF用來設定
					LAN的開關
					LAN ON     / LAN OFF 
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

				LAN 的設定在symbol.ini [LAN] ID

CLAN             DATA	    	經由 lan送資料到 SERVER 

  注意新版的CLAN 不需要再下 CLAN ON  ,CLAN OFF,直接下達想要傳的字串就好.
  當收到Server回應後,會自動關掉.送的時會自動開啟 CLAN

					CLAN  SEND-COMMAND-String
					也可以用 = 後面接變數的方式來傳送
					

				VARSTRING FEI = 'C:\ABC\ABC.EXE '+ BARCODE
					CLAN = FEI  用字串變數來送參數

				其SERVER IP PORT會和BARCODE FORM使用一致的設定
				會在BARCODE.INI 或著在CHANGE.INI[HOST]中設定
				SFIS的IP和PORT的地方 

                                

   範例:
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




ECHO		DATA			可將DATA 的文字顯示到 LOG FILE 中; 如果
					用 ECHO = ABC表示顯示變數值,不存在會顯
					示 NON DATA,如果MESSAGE ON的話,也會顯示
					到其中在字串中加 ~ 會自動換行  
					ECHO ABCD~ABCD


SLEEP		delay-time		delay ms times ==> SLEEP 1000   
					(1000 =  1 second)不作任何事


YESNO		data			設定message box 讓使用者確認 YES OR NO,
					按YES會送'YES'到 log file並且繼續執行下
					面的指令,按NO 會送'NO'到log file並且顯
					示錯誤碼,停止執行其它指令,data為顯示字
					串

					YESNO  = ABC 可單純顯示變數字串,但需存
					在 VAR.INI之中
					如不存在則會顯示 ABC: OK


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



@NAME					Label 給jump 時使用

JUMP		Label			JUMP @123 跳到所標示的位置
					另外也可給其字串變數指示其要跳的位置
					VARSTRING  MYJUMP = @TESTJUMP

					JUMP = MYJUMP
					這個結果會和
					JUMP @TESTJUMP 的作用相同



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
					可以使用()等待多個字串,但不能設 = 和 >>

					~ 表or,  & 表 and
					當等待字串有 , 時可用下面例題設定
 					WAIT (crc32,4,),2000  
					這時候後面一定要
					設TIME OUT 的時間,不能設 = 和 >>

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
				WAIT 
					WAIT 後不接任何字串,則UUT傳來的字串會暫
					時保存在BUFFER中不送出來處理等到下一個 
					WAIT waitstring 字串的command出現時才會
					將之前的字串送出用以防止大量快速資料處
					理速度的問題
                                 WAIT @200       
					每一行時間間隔 0.15秒.如果要自訂間隔時間
					可以下 WAIT @200 表示間隔 0.2秒,在遇到下
					一次空 WAIT會復原成0.15秒

				等到字串時會有一筆字串存在 VARSTRING WAITTEMP中.

                                        
WAITVAR  DATA				將VARSTRING 中的變數 DATA名稱取出來換成
					WAIT waitstring,timeout的格式
                                        例如:
                			VARSTRING DATA = 'ABC >>,2000'
					WAITVAR DATA
					會變成:
					WAIT ABC >>,2000
                                       


                                       

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
			doscmd  cmd /c dir/w d:\
			doscmd  f:\battloop.txt

                     DOSCMD D:\USIPROJECT\IMAGE\NCR\Release-0410_TDD\flashall.bat

                                        另外如果工作目錄太長,不好設定可以使用下面方
					法先產生WORKPATH 再下達 DOSCMD
					但要注意下次要使用時要記得將其變成空的或指定
					新的目錄,不然會永遠指在最後設定的 WORKPATH
		   例:
原本
DOSCMD D:\USIPROJECT\IMAGE\WT6000\Fedex_20160530\Eng\fastboot.exe flash bootloader u-boot-imx6q.imx -s 16110523025026                   
可以改成
  DOSCMD WORKPATH D:\USIPROJECT\IMAGE\WT6000\Fedex_20160530\Eng\
  DOSCMD fastboot.exe flash bootloader u-boot-imx6q.imx -s 16110523025026
  但是使用 WORKPATH 其路徑中不能包含 "." 否則會出現錯誤
  使用 WORKPATH其路徑會一直指向設定的路徑,直到下次更改為止 
  

DOSCMD2					可以使用DOS 相關的命令,會取得回應值,例如:
					其為獨站資源,快速回應,可節省反應時間.其餘功能與
					DOSCMD相同.
					如回應資料很多建議不要使用這組命令,因其獨站資源的
					特性,其它的Form會停滯.


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




/*					大範圍的mark,其功能同c++的功能,需配合 */
					作為結束

RUNPCEXE	DATA			DATA為執行檔在pc端的路徑,檔案名稱,如果
					該程式己經存在可配合Pfindexe.exe來找程
					式來執行可避免重複執行
					RUNPCEXE  Pfindexe.exe 要執行的exe 其
					程式的caption
	==>RUNPCEXE  Pfindexe.exe   C:\WINDOWS\system32\calc.exe "小算盤"
	==> RUNPCEXE = ABC    則會到 var.ini找字串變數ABC來代入執行
        ==> RUNPCEXE "C:\PROGRAM FILE\ABC B.EXE " 如果路徑有空格要用" 包起來
        ==> RUNPCEXE "C:\PROGRAM FILE\AA.EXE ;/A/B"有參數的話也要包起來並在參
					數前加上分號以為區分



EXECLOSE	DATA			參考ctrl-alt-delete中工作管理員-應用程式顯示
					的字串.也就是只需輸入執行檔的檔名,不用加exe


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
		1=ABC
	
		RUNSTR Monitor
		會產生執行
		Runpcexe D:\HexLoader.exe /u ABC /d 3 \IMAGE\MC3000\30XXc50AenMO0133XX.hex


***********  各各變數名稱宣告不能相同******************************************



VARREAL		DATA			可事先宣告實數變數,或用來做實數的計算
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
	


					

SUBSTRING    TYPE  NAME  Position Token  可將VAR.INI中的 VARREAL or VARSTRING的
					字串截取出來再存到VAR.INI中
					1.TYPE  = R | S  R:表VARREAL資料 
							 S:表VARSTRING的資料
					2.NAME  表在VAR.INI  VARREAL 或著 
						VARSTRING的變數名稱
					3.Position  表示要存取的字串所在的位置
					4.Token 表示用這個字串當分隔字串, 不填
						則當成以空白字串來分隔,TAB 鍵以
						\t 來表示

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
      6.SYSTEMBOM.INI
      



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


SaveINIData  Section  name  TYPE  INITYPE	
    原則只允許針對SYMBOL.INI 做存入的動作,其它的不希望有存取動作.



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
					
                         
SELECT		data			設定 select box 讓 USER 選擇要使用那一
					個,USER 選擇後會依選的順序存到 VAR.INI 
					中的[VARSTRING] 中的 SELECT 變數中要顯
					示的項目用 ' , ' 來分隔,依順序會存成 
					1,2,3...的值
					SELECT  test1,test2,test3 會產生三個選
					項 test1~3
					



	
					

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



                                          

SAVEBARCODE	NON			會存在VAR.INI中的 VARSTRING section中,
					以變數名稱BARCODE,MAC,GUID的名稱存字串
					變數,如果有多個MAC的參數存在 MultiMAC 
					section 會存到MAC1,MAC2...的變數中.
					最後SCAN的 Mac code 會在Control中,其它
					的會放在MultiMAC 按輸入的順序存放

					2.2.5.9版本以後會多存一個系統目前時間
					會放在TIMENOW





SAVELOG		NON			會將目前的LOG 資料先行存檔,不用等到最
					後按完成才存檔
                                        如果NON 為檔案路徑和檔名,則會將LOG存到
					指定的目錄中.

CLEARLOG	NON			清除目前的所有LOG 並依Barcode和Time來存
					檔




SAVEVARTXT	TYPE*NAME,...		可將變數存到一個檔案之中,可於程式中設定,
					在結束後會存放在TEST LOG的最後面
					 TYPE*NAME, TYPE*NAME,  ......
					
					1.TYPE*NAME, TYPE*NAME,  ......(
						R:表VARREAL資料 
						S:表VARSTRING的資料)
					SAVEVARTXT  R*DATA1,S*DATA2,R*DATA3
					
VARREAL TEST = 1
VARREAL TEST2 = 2
VARREAL TEST3 = 3

					SAVEVARTXT TEST,TEST2,TEST3
					SAVEVARTXT R*TEST,R*TEST2,R*TEST3

會附加在TEST LOG後面:
					TEST  TEST2  TEST3
					1     2      3





FLAG  ON/OFF FLAG-TYPE,TIMEOUT
     以下資源要使用必需先使用FLAG取得資源後,才能使用.

      ON  VISA | GPIB | MCOM | USB | MCOM2 ,180000 TIMEOUT要大於100  1000表1秒
  FLAG ON VISA,timerout
  FLAG OFF VISA


  在 FLAG ON 之後,在 FLAG OFF 之前的 FAIL都會回到 FLAG ON那一行的ERRORCODE
重新開始測試,需要注意相關設定,原因是要將所佔用的共用資源放掉.


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
                                        7.CONFIG dmm
1. FindResource 為尋找本機是否有相關可連線的 VISA Device,會將所找到的資源放到 
		LOG 中,以供判斷是否要做後續控制 VISA的動作.

                VISA FindResource

2. RsrcName DATA	為所找到的 resource 字串設定,其為指定VISA Device 使用
			,Data要設定成所要連結的sorce 字串,一定要先設定之後才能
			使用 OPEN CLOSE, WRITE,READ等命令,不然無法使用以下四個
			命令

                VISA RsrcName  DATA 表示由VARSTRING中找出名為DATA的字串來替代



3. OPEN		為打開所指定的設備,沒有 DATA 參數
		
		VISA OPEN


4. CLOSE		為關閉所指定的設備,沒有 DATA 參數
		
		VISA CLOSE

5. WRITE  DATA	為依據所打開的 Device 使用手冊下達其相關的指令
		
		VISA WRITE  *IDN?



6. READ   varName  需配合 WRITE 來操作,沒有WRITE 不會有READ的資料可讀
		  VISA PORT 下達要回傳資料的COMMAND,需給變數參數名稱 varName
		  VISA READ ABC 後面為要存的變數名稱ABC,會存入VARREAL 變數
				中,所以一定要是實數資料如果不是實數資料要配合 
				  SAVEWAIT來做

		  VISA READ ABC >> 則會將資料也存到VAR.INI中的savevar 
				     section的變數資料,最後會加到
				     testlog.txtvar之中,不判斷對錯 			

7 CONFIG  DATA			經由 SYMBOL.INI [VISAConfig] 
			;name    source-name
			DMM= USB0::0x164E::0x0DAD::TW00004773::INSTR   
		        透過[VISAConfig] 來設定 PowerSupply或VISA介面的設
			備


******************************************************************************************



*********************** GPIB FUNCTION******************************************
GPIB  Command  DATA			主要是透過NI VISA界面來控制所有可由VISA
					存取的界面,如COM ,GPIB,USB...等等

                                        Command 區分為
                                        1.RsrcName
  					2.CONFIG 
					3.CLOSE
					4.WRITE
					5.READ
					
1. RsrcName DATA	為所找到的 resource 字串設定,其為指定GPIB Device 使用
			,Data要設定成所要連結的sorce 字串,一定要先設定之後才能
			使用 CLOSE, WRITE,READ等命令,不然無法使用以下四個
			命令

                VARSTRING DATA = 'GPIB0::22::INSTR'
                GPIB RsrcName  DATA 表示由VARSTRING中找出名為DATA的字串來替代


2.CONFIG	data			經由 SYMBOL.INI [GPIBConfig] address
						;name    PrimaryAddress   
						DMM=        22            
					==>GPIB CONFIG DMM
					透過GPIB來設定 PowerSupply或GPIB介面的設
					備


3. CLOSE		為關閉所指定的設備,沒有 DATA 參數
		
		GPIB CLOSE

4. WRITE  DATA	為依據所打開的 Device 使用手冊下達其相關的指令
		
		GPIB WRITE  *IDN?



5. READ   varName  需配合 WRITE 來操作,沒有WRITE 不會有READ的資料可讀
		  GPIB READ ABC 後面為要存的變數名稱ABC,會存入VARSTRING 變數
				中
********************************************************************************************	   	

 

STRCOMPARE  VARNAME  DATA		將DATA 中的字串和 VARSTRING 中的變數VARNAME
					比對看其字串中是否有包含DATA的字串
					如果DATA 中的資料存在 VARNAME中
					就會傳回pass,否則的話會引發UUT-FAIL
                 VARSTRING MYDATA = '1234'
                 STRCOMPARE MYDATA 'FF12345'
                 也可以使用二個字串變數做比對
                 VARSTRING DATA1 = '1234'
                 VARSTRING DATA2 = 'FF1234000'
                 STRCOMPARE DATA1 DATA2

					
					
ANDROID		DATA			取得ANDROID ID
                                        如果成功資料會放在 VARSTRING AndroidID


ANDROIDCMD      ADB-COMMAND		利用ANDROID ID先取得ID後,可使用ANDROIDCMD
					會自動在ADB COMMAND中間加入 
					 -s androidID 到 adb command 中,以方便使用                             

ANDROIDLOG      LOG-FILE-PATH		取出由ANDROID UUT回傳的資料格式
					PASS/FAIL , ERRORCODE, MESSAGE
					FAIL的資訊會另存成 
					C:\ANDROID1.BAT or 
					C:\ANDROID2.BAT or
					C:\ANDROID3.BAT or
					C:\ANDROID4.BAT
					取決於是那一個form存檔的
                                        "C:\ANDROID" + FROMID+ ".BAT"

					再由 DOSCMD來執行程式,組成內容由
					FAIL MESSAGE 存入BAT FILE中
                                        並且在VARSTRING UUTFAIL 設成 TRUE
                                        如果全部PASS
					VARSTRING UUTFAIL 設成 FAIL
					 

ANDROIDLOGCAT  Wait string $ grep string $ time interval ,timeout

                                        Wait string:要等待的字串
					grep string:logcat要取回過濾的字串
					time interval:間隔多久取回log 一次
                                        timeout: 多少秒TIME OUT

ANDROIDLOGCAT  SUCCESSFUL$FMX$2000,20000

SAVEWAIT ON
ANDROIDLOGCAT  SUCCESSFUL = MYTEST $FMX$2000,20000
SAVEWAIT OFF
會存到 VARSTRING MYTEST中

savewait on
ANDROIDLOGCAT  voltage = btt $FMX$1000,5000
savewait off
echo = btt

ANDROIDLOGCAT前後不需要使用 WAIT 或著 WAIT SUCCESSFUL它會自己等,Time out會停止.
但可以加入save wait on 和save wait off去存想要的資訊.
它不會清logcat -c 做完要自己清除.




<< checkTag << retry times <<  background test
			
					<< myadbdevice << 2 << doscmd adb devices
					這個會將 myadbdevice當作檢查字元,
					錯誤時只重測
					2次,
					所要在背景執行的command	
					doscmd adb devices

					因此在check list 中會存放
					myadbdevice$2$errorcode$doscmd adb device
					一但下達DUT回傳測試LOG時.會依格式

					$$$myadbdevice$$$pass | fail


					$LOGEND$  做為所有LOG回傳完畢的記號,
					這時會去檢查check list中還有那些沒有測試完畢,
					會再度進入背景測試.
					使用 WAIT $LOGEND$ 做為結束.再用 ANALIST 檢查是否
					測完,沒測完則再下達背景執行程式,回到這個取 LOG的
					 ERRORCODE那去重新取得LOG 


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




ANALIST START | END  做為背景測試回傳結果的判斷
                       START只送重測COMMAND不RETRY
                       END 送重測COMMAND 並RETRY
                       收LOG的過程只傳送到BUFFER,不處理,等到CHECKLIST時才統一處理,收到$$$就送到
			BUFFER 中

ANADUMP     輸出目前存在Buffer中的data

AUTORetry 5


UUT-FAIL

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

					  


GETMHEX		ON | OFF		可經由 MCOM PORT 收進來的資料以16進位顯
					示,控制以ON OFF 來控制
					GETMHEX ON 表示將MCOM PORT的資料改以16進
						    位值收入
					GETMHEX OFF 表示將MCOM PORT的資料以字串形
						    式收入
					如果此時沒有拿到COM FLAG所設定的ON OFF
					沒有效用






******************************************************************************


UIMACRO		NAME			可事先於 DIO.INI中的 [UIMACRO] 中定義所
					要的COMMAND,如此可以簡單的命令來下達,可
					參考
					INIREADME UIMACRO  PORWRON

                                        如果因為控制主板為多個共用設備,需要使用不同
					的值,則可在 UIMACRO中利用FORMID 來定義.
                                        例如:
 
   這個部份可以宣告在 FCTCOMMAND 中   
   VARSTRING MYPOWERON = '!USB'+ FORMID+'_ON'
   VARSTRING MYPOWEROFF = '!USB'+ FORMID+'_OFF'
   
   這個部份可以放在 UIMACRO 中                      
   POWERON=  COM = MYPOWERON % ECHO POWER ON % WAIT ABC,2000
   POWEROFF=  COM = MYPOWEROFF % ECHO POWER OFF % WAIT ABC,2000
   


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

