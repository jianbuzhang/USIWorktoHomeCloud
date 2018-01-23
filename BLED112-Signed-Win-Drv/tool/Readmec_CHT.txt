在呼叫時如果有附文字檔的參數則會以開啟所給參數的文件
如使用PUSIGB.EXE 下

RUNPCEXE  F:\Delphi-AP\BGLibScanner.exe  4200 COM17

表示使用CLAN  Port 4200和 LAN SERVER 連接,後續即可使用 LAN來控制
Default Server IP address  127.0.0.1
COM17 則為BLE  所顯示的COM PORT 

會回傳
UUT-BLELINK


Command         add-data                 discription

CLOSE		NON   			關掉應用程式
					

SCANON		NON			開始SCAN 附近的BLE會回傳
          ble_evt_gap_scan_response:
          rssi=-84, bd_addr=[6fda6c726a2d]
                                        可以取得rssi值和 ble mac address

   


SCANOFF		NON			停止BLE的掃瞄