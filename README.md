## 摘要
本專題改裝了HERAN的電風扇，型號HDF-12AH710，對其電路板進行焊接(焊上單心線)
電路板上的單心線會經由杜邦線轉接到Arduino，以實現Arduino(Arduino uno R3)對電風扇的控制，因此Arduino作為對電風扇的控制模組，而Arduino連接著樹梅派(RaspberryPi 4)，樹梅派在此系統作為聲音感測模組，接收聲音辨識使用者需求，並將動作訊號輸出給Arduino。

因此系統架構如下：
