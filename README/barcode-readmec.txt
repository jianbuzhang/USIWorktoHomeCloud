
一. 在image download 使用 muti com 動作,注意下面事項:
  1. 在目錄 \PORD\SYMBOL.INI
     其[COM] 主要在設定多個 COM PORT的對應資料,目前只能設到 COM9
     [USB] 主要是針對 SYMBOL的案子每一個COM PORT 所對應的USB ID為何,避免對應錯誤,1<-->1
  
  2.在目錄 \PORD\PROJECT\ 下可以設定 SYSTEMBOM.INI 
     [CONFIG] 主要在設定USI的料號對應到客戶的組態,也可以用來設定自己想要的組態,以提供在
		FCTCOMMAND 中做為判斷的依據
     
	\PORD\PROJECT\VERSION\Barcode.ini
		USI barcode要從那個位置來取出,要由barcode.ini中的[Position]
		START=1 和 LENGTH=8 來設定
                而 barcode.ini 中的[Config] 就是依據所對應出來的值來取出放到變數值中,也就
		是會放到var.ini中的[VARSTRING] 中,依其後的名稱來放入,fctcommand也由var.ini
		取出來判斷
		
		要使用config 的功能在barcode.ini [control] CONFIG=ON 要設定為ON
		CONFIGLength=18 長度也要設定,其SYSTEMBOM.INI 中的長度要和其一致
		
		[USIADD] 主要在當客戶的組態不足以包含全部的控制時,可以加入USI的BARCODE來加以控
			制,以增加彈性,
			要使用還要在 barcode.ini [Position]中加入  USIADD= ON
			要注意其名稱不要和 barcode.ini 中[Config] 名稱相同,因為會互相蓋掉

		
 
 3.在目錄 \PORD\PROJECT\ 下可以設定 SYSTEMBOM2.INI 
		主要用在取出系統之前所設定的值,以供新的BARCODE 產生互相對應,以決定是否需要
		再做同樣的動作,例如IMAGE是否要重新download.
       		其對應的設定有:
	(1).\PORD\PROJECT\VERSION\Barcode.ini
    	    當要輸入第二組 barcode來供判斷時要設定下面的資料
	    a.在 使用PBarcodeFM.exe 時  要勾選,才會跳出視窗供使用者輸入第二組的barcode,但在多台
		操作時,每一台必需是同一個組態.
	    

	    b.輸入barcode後,會從SYSTEMBOM2.INI取出相對應的組態,要從那個位置來取出,
		要由barcode.ini中的[Position2] START=1 和 LENGTH=8 來設定

                而 barcode.ini 中的[Config2] 就是依據所對應出來的值來取出放到變數值中,也就
		是會放到var.ini中的[VARSTRING] 中,依其後的名稱來放入,fctcommand也由var.ini
		取出來判斷其名稱要和 ***[Config]*** 中相同且對應,之後會以 相同名稱加一個 2來放到
		var.ini中 例如 varsion2= abc 等等
		
		
		[USIADD2] 主要在當客戶的組態不足以包含全部的控制時,可以加入USI的BARCODE來加以控
			制,以增加彈性,
			要使用還要在 barcode.ini [Position2]中加入  USIADD2= ON
			要注意其名稱不要和 barcode.ini 中[Config2] 名稱相同,因為會互相蓋掉


  目前這個功能用在 PMCom.exe 和 PBarcodeFM.exe 的組合中