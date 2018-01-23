command           data                 discription

COM  		dos command    		set dos command to UUT via COM port, if you want send
                                         space, you can write ==> COM SPACE (only space no 
                                         enter command)                  
DIO		name  value		refrence DIO.INI  [dio] setion & name==>DIO DATA1 255
ACHV            name			refrence DIO.INI [ACHV] setion & name==>ACHV ACHV0
ACHI		name			refrence DIO.INI [ACHI] setion & name==> 
                                         ACHI   OperaTionChargeTest1
WAIT            waitstring,timeout	wait string from COM port data,timeout is wait time 
					by ms ==> WAIT C:>,1000    (1000 is 1 second)
SLEEP		delay-time		delay ms times ==> SLEEP 1000   (1 second)
SMB             name			set power data, refrence DIO.INI [ACHI] setion & name
					==> SMB OperaTionChargeTest1 
KEY             data			send one key via UUT keyboard ==> KEY A
KEYSTRING       data			send key string via UUT keyboard ==> KEYSTRING  test? 
                                         (?is enter) 
DAC		name			send DAC data refrence DIO.INI [DAC] setion & name
					==> DAC SINWAVE ON  (ON | OFF)
ALLKEYTEST      NON 			NO data need but you can updat DIO.INI [ALLKEY] setion 
					value for your test sequence
POST		data 			set wait post code data==> POST A0  (data is HEX mode)
RJ1145          NON			NO data need but you can updat DIO.INI [RJDATA] setion 
					value for your test data
END		NON			END for test,you must add this string in your file end,  
					when you test the end ==> END
ERRORCODE       data			set next test file error code ==> ERRORCODE 0001
SENDBARCODE 	NON			Send barcode via UUT keyboard ==> SENDBARCODE
YESNO   	data			set data for YESNO message box, and return 'Y' or 'N' 
					from COM port
CLOSESMB	NON			close power data setting	


COUNTER         name                   refrence DIO.INI  [COUNTER] setion & name==>VGAMODE 
                                        return TRUE / FALSE
DIOREAD         name  data             set dio name & compare data, if DIO-GET-DATA = data then 
                                        return TRUE else return FALSE,  name-->refrence DIO.INI  
                                        [dio] setion-name 

SENDMAC         Dos-command            MAC data get from barcode.ini, Dos-command by chipset 
                                        support
SENDGUID        Dos-command            GUID data get from barcode.ini, Dos-command by chipset 
                                        support
GPIBCONFIG      name                   refrence DIO.INI [GPIBConfig] setion & name==>GPIBConfig
                                        PowerSupply
SETHPPOWER      name                   refrence DIO.INI  [HPPOWERSET] setion & name==>SET37V
READGPIBDATA    name                   refrence DIO.INI  [GPIBDATA] setion & name==>HPCurrent, 
                                        you can set Voltage or Current to compare UP & LOW data
HPOUTPUT        ON/ OFF                ON-Set GPIB output on  OFF- Set GPIB output off
COUNTERFALL     name                   get full frequence data uses DIO.INI [COUNTER] 
                                         setion-name
ACHWAVE         name                   get ACH wave top and low interval. Uses DIO.INI [ACHWAVE] 
                                        setion & name
DACPOINT        name                   set DAC data to fix on some value. Uses DIO.INI 
                                        [DACPOINT] setion & name

NIDIO           name  value	       refrence DIO.INI  [dio] setion & name==>NIDIO DATA1 255
NIDIOREAD       name  data             set dio name & compare data, if DIO-GET-DATA = data then 
                                        return TRUE else return FALSE,  name-->refrence DIO.INI  
                                        [dio] setion-name 

NIDIODIR        name                   refrence DIO.INI [NIDIODIRECT] setion & name you can
                                       control DIO direction by name ---> NIDIODIR PORT0 
                                       NIDIODIR PORT1 ,  NIDIODIR PORT3

