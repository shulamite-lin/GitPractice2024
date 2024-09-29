##### 筆記-.net framework_版本，謝謝自己沒有放棄
今天繼續在類似的錯誤裏鬼打牆，Could not load file or assembly System.Diagnostics.Debug, Version=4.1.2.0' ，用昨天的方法無效，我把原本在dll中的System.Diagnostics.Debug刪除，再使用NuGet時安裝時發現bin中沒有System.Diagnostics.Debug，所以看不到它的版本，google 找不到接近的問題，後來在資料夾中找System.Diagnostics.Debug，在D:\1000Hceb\Study\study\packages\System.Diagnostics.Debug.4.3.0\ref中有三個資料夾有，分別是netstandard1.0，netstandard1.3，netcore50，前者版本是4.0.0.0，後兩者是4.0.10.0是，將以下的newVersion改成4.0.10.0失敗，改4.0.0.0就成功了。
``` csharp
    <bindingRedirect oldVersion="0.0.0.0-4.1.2.0" newVersion="4.0.0.0" />
```

程式再繼續推進到新增資料到活動掃碼，出現了類似上面的錯誤，dll換成System.Collections.dll，去bin翻有這個元件，於是將它移除，使用NuGet安裝，和上述一樣bin中沒有NuGet安裝的dll，因此照上面的做法處理，處理完後有不同的錯誤(忘了先截圖)，但我判斷這次是因為ActivityDataModel.dll和現在的程式不相容，因此在study下重做了一個ActivityDataModel，study的bin中移除core3的ActivityDataModel.dll改成一樣.net framework4.8的ActivityDataModel.dll，經過這些修改，資料已經成功的透過API傳送出去了。　
但發現問題，單位是教育處身份無法新增到掃碼報到系統，我把自己的單位改成東門國小才能新增，但實質上沒有東門的身份，所以進到掃碼報到系統看不到自己新增的資料。

bbbbb