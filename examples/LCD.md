# Library-Manual<br>
Like the "Arduino-IDE" MyIDE comes with a folder called "../MyIDE/libraries".<br>
These subfolders are intended for user-libraries which you create or<br>
got from other sources.<br>
Create a subfolder for the user-library and add the *.h and *.o files.<br>
The library-files will be automatically included in the compile- and<br>
link-process.<br>

**LCD Library**<br>
I developped this library in order to make debugging easier.<br>
I followed some ideas from the Arduino-library.<br>

**C++ & Arduino compatibility**
> This libray can not used in C-language, because I used<br>
> overwriting of functions which is a feature of C++<br>

**LCD initialize functions**<br>

void lcd_init( volatile uint8_t* _LCD_PORT_RS_EN, uint8_t _LCD_RS, uint8_t _LCD_EN,<br>
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;volatile uint8_t* _LCD_PORT, uint8_t _DB4, uint8_t _DB5, uint8_t _DB6, uint8_t _DB7);<br>

| **LCD functions**                           |                                         |
| :------------------------------------------ | --------------------------------------- |
| void lcd_clear();                           | clear display                           |
| void lcd_home( void );                      | home cursor                             |
| void lcd_display_on( void );                | display on                              |
| void lcd_display_off( void );               | display off                             |
| void lcd_cursor_on( void );                 | cursor on                               |
| void lcd_cursor_off( void );                | cursor off                              |
| void lcd_blink_on( void );                  | cursor blink on                         |
| void lcd_blink_off( void );                 | cursor blink off                        |
| void lcd_autoscroll_on( void );             | display moves, cursor still             |
| void lcd_autoscroll_off( void );            | display still, cursor moves             |
| void lcd_leftToRight( void );               | cursor left to right                    |
| void lcd_rightToLeft( void );               | cursor right to left                    |
| void lcd_scrollDisplayLeft( void );         | scroll display left                     |
| void lcd_scrollDisplayRight( void );        | scroll display right                    |
| void lcd_setcursor( uint8_t x, uint8_t y ); | set cursor to column x, line y (0 or 1) |

**LCD print number functions**<br>

* void lcd_print(int);<br>
* void lcd_print(unsigned int);<br>
* void lcd_print(long);<br>
* void lcd_print(unsigned long);<br>
* void lcd_print(double);<br>
* void lcd_print(float);<br>

**New print character functions<br>**
* void lcd_print(char*);<br>

* void lcd_print(char);<br>

* void lcd_print_xy( uint8_t x, uint8_t y, char *data );<br>

  

  **Example<br>** 

  ------

  #include &lt;avr/io.h&gt;<br>
  #include &lt;util/delay.h&gt;<br>
  #include &lt;string.h&gt;<br>
  #include "LCD.h"&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;// customized for ATmega328P<br>
  #include "LCD_PRINT.h";&ensp;&ensp;&ensp;&ensp;// include header for LCD print-functions<br>

  #include &lt;avr/io.h&gt;<br>
  #include &lt;util/delay.h&gt;<br>
  #include &lt;string.h&gt;<br>
  #include "LCD.h"&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;&ensp;// customized for ATmega328P<br>
  #include "LCD_PRINT.h";&ensp;&ensp;&ensp;&ensp;// include header for LCD print-functions<br>

int main() {<br>
&emsp;&emsp;// initialize LCD with choosen hardware connections<br>
&emsp;&emsp;// notice one port for RS and EN, and one port for data-connections<br>
&emsp;&emsp;// lcd_init( &lt;PORT of RS and EN&gt;, &lt;RS-pin&gt;, &lt;EN-pin&gt;, &lt;PORT of data&gt;, &lt;DB4-pin&gt;, &lt;DB5-pin&gt;, &lt;DB6-pin&gt;, &lt;DB7-pin&gt;)<br>
&emsp;&emsp;&emsp;// e.g.<br>
&emsp;&emsp;&emsp;// notice &PORTB instead of PORTB; because we need the address<br>
&emsp;&emsp;&emsp;// LCD RS      <-->  PORTB Bit PB0     (RS: 0=data, 1=command)<br>
&emsp;&emsp;&emsp;// LCD EN      <-->  PORTB Bit PB1     (EN: 1-impuls for data ready)<br>
&emsp;&emsp;&emsp;// notice &PORTC instead of PORTC; because we need the address<br>
&emsp;&emsp;&emsp;// LCD DB4     <-->  PORTC Bit PC2<br>
&emsp;&emsp;&emsp;// LCD DB5     <-->  PORTC Bit PC3<br>		
&emsp;&emsp;&emsp;// LCD DB6     <-->  PORTC Bit PC4<br>		
&emsp;&emsp;&emsp;// LCD DB7     <-->  PORTC Bit PC5<br>	
<br>
&emsp;lcd_init( &PORTB, PB0, PB1, &PORTC, PC2, PC3, PC4, PC5);<br>
<br>
&emsp;lcd_print('X');<br>	
&emsp;_delay_ms(2000);<br>
<br>
&emsp;lcd_clear();<br>
&emsp;char str[24];<br>
&emsp;strcpy(str, "Hello world");<br>
&emsp;lcd_print(str);<br>	
&emsp;_delay_ms(2000);<br>
<br>
&emsp;lcd_clear();<br>
&emsp;strcpy(str, "Integer");<br>
&emsp;lcd_print(str);<br>
&emsp;lcd_setcursor(0,1);<br>
&emsp;lcd_print(-32767);<br>
&emsp;_delay_ms(2000);<br>
<br>
&emsp;lcd_clear();<br>
&emsp;strcpy(str, "unsigned Integer");<br>		
&emsp;lcd_print(str);<br>
&emsp;lcd_setcursor(0,1);<br>
&emsp;lcd_print(65535U);<br>
&emsp;_delay_ms(2000);<br>
<br>
&emsp;lcd_clear();<br>
&emsp;strcpy(str, "long");<br>	
&emsp;lcd_print(str);<br>
&emsp;lcd_setcursor(0,1);<br>
&emsp;lcd_print(-2147483647);<br>		
&emsp;_delay_ms(2000);<br>
<br>
&emsp;lcd_clear();<br>
&emsp;strcpy(str, "unsigned long");<br>			
&emsp;lcd_print(str);<br>
&emsp;lcd_setcursor(0,1);<br>
&emsp;lcd_print(4294967295UL);<br>		
&emsp;_delay_ms(2000);<br>
<br>
&emsp;lcd_clear();<br>
&emsp;strcpy(str, "double");<br>			
&emsp;lcd_print(str);<br>
&emsp;lcd_setcursor(0,1);<br>
&emsp;lcd_print(334567.123);<br>		
&emsp;_delay_ms(2000);<br>
<br>
&emsp;lcd_clear();<br>
&emsp;strcpy(str, "Hannover");<br>			
&emsp;lcd_print_xy(1, 1, str);<br>
<br>
&emsp;while(1) {<br>
&emsp;}<br>
&emsp;return 0;<br>
}<br>

------

**Implemented data types:<br>**
Derived from https://learn.sparkfun.com/tutorials/data-types-in-arduino/all<br>

| Type                   | Description                                                  |
| :--------------------- | :----------------------------------------------------------- |
| bool (8 bit)           | int8_t    - simple logical true/false 1/0                    |
| char (8 bit)           | int8_t    - signed number from -128 to 127                   |
| unsigned char (8 bit)  | uint8_t   - unsigned number from 0-255                       |
| int (16 bit)           | int16_t  - signed number from -32768 to 32767                |
| unsigned int (16 bit)  | uint16_t - unsigned number from 0-65535                      |
| long (32 bit)          | int32_t  - signed number from -2,147,483,648 to 2,147,483,647 |
| unsigned long (32 bit) | uint32_t - unsigned number from 0-4,294,967,295              |
| float (32 bit)         | signed number from -3.4028235E38 to 3.4028235E38             |
| double                 | same as float                                                |



