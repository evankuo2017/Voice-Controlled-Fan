## 摘要
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
  '''
  在cmd執行nano ~/.bashrc
  在檔案末端添加：sudo python3 snowboyDetection.py之絕對路徑 &
  '''
3.Arduino需依照程式碼內容將輸出信號接角接上電風扇作為各種功能對應的控制線
4.這些聲音辨識的pmdl檔案來源為經由snowboy技術訓練後的結果，本專題訓練樣本採自行錄製並未上傳
訓練方法可見 https://github.com/rhasspy/snowboy-seasalt

其餘成果展示及實作說明可見專題報告書.pdf
