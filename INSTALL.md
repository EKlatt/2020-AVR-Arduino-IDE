## Installation of MyIDE:<br>
* You may download the ready to use Beta-release. 
* Or creating your own version. Follow the instructions below.<br>
After downloading "2020-AVR-Arduino-IDE-main.zip" unzip it.<br>
Paste the downloaded folder where ether you want.<br>
Rename it to e.g. MyIDE.<br>
* Download and install the toolchain into folder "toolchain":
* In order to do this, follow these steps:<br>
* Open the folder "toolchain"
* Read the explanations in file "What to do.txt"<br>
1. Download https://blog.zakkemble.net/download/avr-gcc-10.1.0-x64-windows.zip
2. Unpack avr-gcc-10.1.0-x64-windows.zip
3. Find the folder ..\avr-gcc-10.1.0-x64-windows
4. Copy (only the contents) from "avr-gcc-10.1.0-x64-windows" to ..\MyIDE\toolchain<br><br>

* Download and install Progammer's Notepad into folder "PNP":
* In order to do this, follow these steps:<br>
* Open the folder "PNP"
* Read the explanations in file "What to do.txt"<br>
1. Download https://github.com/simonsteele/pn/releases/download/v2.4.2/portable-pn2421440.zip
2. Unpack portable-pn2421440.zip
3. Copy (only the contents) from "portable-pn2421440" to ..\MyIDE\PNP
4. Locate ..\MyIDE\PNP\settings
5. Delete the file "UserTools.xml" 
5. Rename the file "UserTools.xml.new" to "UserTools.xml"<br><br>

* Download and install the Unix tools into folder "utils":
* In order to do this, follow these steps:<br>
* Open the folder "utils"
* Read the explanations in file "What to do.txt"<br>
1. Download http://unxutils.sourceforge.net

2. Unpack UnxUtils.zip

3. Find the folder ..\UnxUtils\usr\local\wbin

4. Copy wbin-files to ..\MyIDE\utils<br><br>

* Download and install Gerd's AVR Simulator
* In order to do this, follow these steps:<br>
* Open the folder "avr_sim"
* Read the explanations in file "What to do.txt"<br>

1. Download: http://www.avr-asm-tutorial.net/avr_sim/23/avr_sim_23_win64_debug.zip
2. Unpack: avr_sim_23_win64_debug.zip
3. Copy avr_sim.exe to ..\MyIDE\avr_sim<br><br>

* Download and install Atmel Studio 7.0 in order to get avrasm2.exe
* In order to do this, follow these steps:<br>
* Open the folder "avrasm2"
* Read the explanations in file "What to do.txt"<br>
1. Download: https://www.microchip.com/content/dam/mchp/documents/parked-documents/as-installer-7.0.2542-full.exe
2. Install Atmel Studio 7.0
3. Look for "Your Path"\Atmel\Studio\7.0\toolchain\avr8\avrassembler\avrasm2.exe
4. Copy avrasm2.exe to "your path"\MyIDE\avrasm2\avrasm2.exe

<br>
Have fun.

