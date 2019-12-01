# HC-05-using-MSP432P401R-
Interfacing two boards over bluetooth, baremetal code 

1 To enter AT mode apply 3.3 V to Enable Pin - APPLY 3.3V to Vcc after that, the LED should go ON-OFF every 2 seconds

2 To enter communication mode remove 3.3V from EN - and APPLY 3.3V to Vcc after that

The HC-05 is connected to MSP432 through EUSCI_A2 

The Master Device takes input from EUSCI_A0 and transmits it across EUSCI_A2

The Slave Device takes input via EUSCI_A2 and transmits it to the PC via EUSCI_A0 

The AT commands are included in the AT_commands.h file, to use them put the device in AT mode. And use the UART2_string function in uart.c to transmit it, make the following change in the code. 

In the EUSCI_A2 interrupt remove the comments from the while statement and EUSCI_A0->TXBUF=EUSCI_A2->RXBUF, by doing so you can receive the OK from the device 

NOTE: I have configured my Bluetooth devices at 38400 baud rate, and my UARTS are also configured at 38400, using the parameters 19 and 8 in MCLW and someother register - (I forgot) you can change it to 9600 by using 78 and 2 or any other baud rate - there is a simple calculation.  


