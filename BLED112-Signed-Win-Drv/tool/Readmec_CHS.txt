在呼叫时如果有附文字档的参数则会以开启所给参数的文件
如使用PUSIGB.EXE 下

RUNPCEXE  F:\Delphi-AP\BGLibScanner.exe  4200 COM17

表示使用CLAN  Port 4200和 LAN SERVER 连接,后续即可使用 LAN来控制
Default Server IP address  127.0.0.1
COM17 则为BLE  所显示的COM PORT 

会回传
UUT-BLELINK


Command         add-data                 discription

CLOSE		NON   			关掉应用程式
					

SCANON		NON			开始SCAN 附近的BLE会回传
          ble_evt_gap_scan_response:
          rssi=-84, bd_addr=[6fda6c726a2d]
          可以取得rssi值和 ble mac address

   


SCANOFF		NON			停止BLE的扫瞄
