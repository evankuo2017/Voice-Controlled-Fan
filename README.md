<!--## 摘要
本專題改裝了HERAN的電風扇，型號HDF-12AH710，對其電路板進行焊接(焊上單心線)
電路板上的單心線會經由杜邦線轉接到Arduino，以實現Arduino(Arduino uno R3)對電風扇的控制，因此Arduino作為對電風扇的控制模組，而Arduino連接著樹梅派(RaspberryPi 4)，樹梅派在此系統作為聲音感測模組，接收聲音辨識使用者需求，並將動作訊號輸出給Arduino。

因此系統架構如下：

## Arduino
在fansArduino資料夾中包含了Arduino相關的測試程式碼及實際運行於系統中的程式碼fanSystem.ino，將其燒錄至Arduino板中即可運行。

## ResperryPi
在fansResperryPi資料夾中包含了ResperryPi相關的測試程式碼及開機即運行之程式snowboyDetection.py，也就是偵測聲音並跟Arduino通訊的程式。
這個程式要能正常運行需要於樹梅派中下載https://github.com/Kitt-AI 的snowboy專案，將此專案的examples/資料夾中python資料夾複製一份，
命名為snowboytest，然後將snowboyDetection.py及其聲音辨識模型檔案(pmdl資料夾)放到這個路徑下，snowboyDetection.py即可正常運行

## 注意事項：
1.運行snowboyDetection.py前需要正常在ResperryPi設定好麥克風、ResperryPi跟Arduino間需要先接通訊用線(USB type B即可)
2.要使snowboyDetection.py開機自動執行需要做一些設定：
在cmd執行nano ~/.bashrc
在檔案末端添加：sudo python3 snowboyDetection.py之絕對路徑 &
3.Arduino需依照程式碼內容將輸出信號接角接上電風扇作為各種功能對應的控制線
4.這些聲音辨識的pmdl檔案來源為經由snowboy技術訓練後的結果，本專題訓練樣本採自行錄製並未上傳
訓練方法可見 https://github.com/rhasspy/snowboy-seasalt

其餘成果展示及實作說明可見專題報告書.pdf
-->

# Project Summary

This project involves the modification of the HERAN electric fan, model HDF-12AH710, with the soldering of single-core wires onto its circuit board. The single-core wires on the circuit board are connected to an Arduino (Arduino Uno R3) through DuPont wires. The Arduino serves as the control module for the electric fan, and it is connected to a Raspberry Pi 4. In this system, the Raspberry Pi functions as the sound detection module, receiving voice recognition commands from the user and sending action signals to the Arduino.

The system architecture is as follows:

## Arduino
The `fansArduino` folder contains test code and the actual program `fanSystem.ino` for Arduino, which controls the fan. Upload the code to the Arduino board to run the system.

## Raspberry Pi
The `fansResperryPi` folder includes test code and the startup script `snowboyDetection.py` for the Raspberry Pi. This script detects sound and communicates with the Arduino. To run this script successfully, download the Snowboy project from [Kitt-AI](https://github.com/Kitt-AI), copy the `python` folder from `examples/` in this project, name it `snowboytest`, and place `snowboyDetection.py` and its sound recognition model files (`pmdl` folder) in this path. This ensures that `snowboyDetection.py` runs correctly.

## Important Notes:
1. Before running `snowboyDetection.py`, ensure that the microphone is properly configured on the Raspberry Pi, and there is a communication line (USB type B) connecting the Raspberry Pi and Arduino.
2. To run `snowboyDetection.py` on startup, add the following line to the end of `nano ~/.bashrc`:<br>
sudo python3 /path/to/snowboyDetection.py &
3. Follow the instructions in the Arduino code to connect the output signals to the electric fan for various functionalities.
4. The voice recognition models (`pmdl` files) used in this project are trained using Snowboy technology. Training samples are not included, but the training method can be found at [rhasspy/snowboy-seasalt](https://github.com/rhasspy/snowboy-seasalt).

For further details, demonstrations, and implementation explanations, please refer to the project report`專題報告書.pdf`.
