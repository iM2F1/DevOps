[BDD]MSTest 的，索引在陣列的界限之外。
===

### 1.為了練習 BDD 開始建 Demo 專案。
#### 1.1 所以專案就叫做 BDDDemo XD
    專案建好了，MSTest 也成功綠燈(什麼也沒寫)
    接著想用 Command Line 執行測試，之後要搬到 CI 才方便。
    
#### 1.2 一個原本以為會很順利的動作。
- MSTest /help //查詢指令用法
- MSTest /testcontainer:TestProject.dll //我執行的測試
![索引在陣列的界限之外。](https://i.imgur.com/Juew6Q4.jpg)

- 索引在陣列的界限之外。
- 索引在陣列的界限之外。
- 索引在陣列的界限之外。

#### 這甚麼低級的錯誤!!!? 問題是我甚麼都還沒做啊 !?


### 2. 這時想起剛學 BDD 的時候有做了一個 Demo 範例。
#### 還是叫做 BDDDemo
- 馬上挖出來執行。

#### 結果竟然讓人傻眼。
![成功了!!?](https://i.imgur.com/H0YEehR.jpg)

#### 失敗的專案設定
![失敗的專案設定](https://i.imgur.com/RaXUH2W.png)

#### 成功的舊專案
![成功的舊專案](https://i.imgur.com/wBc2qT0.png)

#### 試著改用 Nunit 執行測試 (成功
![Nunit 執行測試](https://i.imgur.com/UgGNKLV.png)



### 3. 開始檢查 Nuget 安裝的套件。
- MSTest 沒裝
- Nunit 裝了好幾個東西
- Specflow 2.2.0 成功的專案還是 Preview 版

### 4. 最後比對 reference 發現，缺了
- Microsoft.VisualStudio.QualityTools.UnitTestFramework

#### 安裝後怎麼執行怎麼成功。

#### 雖然還是有疑問，沒有安裝 MSTest 套件，卻可以用 MSTest 執行。
- 感覺還是有些雷沒踩到。
- 以後再請各位大大指教。
- 希望這個坑，我踩就好。
- 踩到也沒關係，這邊有解答。
- 我發誓我真的是開 Unit Test Project。

