# Programming
If you don't have or don't want to buy Segger J-Link you can use cheap ST-LINK V2 programmer ($5). Many ST boards like Nucleo have them embedded.

You have to connect:
  - power (3V3 and GND)
  - SWD IO: (nRF) SWD<->SWCLK(link)
  - SWD IO: (nRF)SWIO<->SWDIO(link)
  
If you have Nucleo power can be taken from 3V3 and GND on arduino/morpho headers on main board. SWCLK is 2nd and SWDIO is 4th (counting from blue dot - usb connector side) pin of CN4 connector.
Dont't forget to take out ST-LINK/NUCLEU jumpers (CN2) - or you will be programming nucelo instead of external device.

Best results with flashing - OpenOCD.

More details on how to flash will be published soon. 
Temporal dirty commandline: ```openocd -f stlink-v2.cfg -c "transport select hla_swd; set WORKAREASIZE 0x4000;" -f nrf51.cfg -c "init ; reset halt ; nrf51 mass_erase ; sleep 500 ; program s110.hex verify; program app.hex verify reset"```
