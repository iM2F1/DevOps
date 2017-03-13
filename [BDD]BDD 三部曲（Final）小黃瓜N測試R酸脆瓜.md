BDD 三部曲（Final）小黃瓜N測試R酸脆瓜
===
### 1.更改 unitTestProvider to Nunit
更改App.config
```
<unitTestProvider name="Nunit"></unitTestProvider>
```


### 2.安裝 nunit3-console，取得測試報告。
#### [方法一]透過 NuGet，安裝於 Project 中。
安裝 NUnit3-ConsoleRunner
![NUnit3-ConsoleRunner](https://i.imgur.com/XVNFi0p.png)


#### [方法二]透過 NUnit GitHub，直接下載。
[Nunit](https://github.com/nunit/nunit-console/releases)
![NunitGitHub](https://i.imgur.com/aUiy3rC.png)


### NUnit3-Comsole 產出測試
#### [方法一] Nunit3-Console 在 Package 下
```
.\packages\NUnit.ConsoleRunner.3.6.1\tools\nunit3-console.exe .\BDDDemo2.Test\bin\Debug\BDDDemo2.Test.dll
```
使用 Package Manager Console 執行指令
![BeforeTest](https://i.imgur.com/Oht2vq5.png)
執行結果
![AfterExec](https://i.imgur.com/WHVjgUW.png)

取得測試結果。
![TestReport](https://i.imgur.com/NeKkcmr.png)


#### [方法二] NUnit3-Console 自行下載
切換到下載目錄，執行指令。
```
.\nunit3-console.exe D:\ArchPrograms\PlayGround\BDDDemo2\BDDDemo2.Test\bin\Debug\BDDDemo2.Test.dll
```
![執行指令](https://i.imgur.com/PcBrvEP.png)
執行結果
![Result](https://i.imgur.com/6k3BC6A.png)


取得測試報告
![TestReport](https://i.imgur.com/AaXrpMn.png)



### 3.使用 PicklesUI 產出文件。
![PickelsUI](https://i.imgur.com/CLwOUQg.png)

#### 先安裝 chocolatey:The package manager for Windows
[Chocolatey](https://chocolatey.org/install)

```
1. 使用 Administrator 執行 PowerShell
2. iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
```
![Install Chocolatey](https://i.imgur.com/MHO2PgS.png)

#### 安裝 PicklesUI
![Install PicklesUI](https://i.imgur.com/bzULUL3.png)

#### PicklesUI 設定
    1.Feature Directory: Feature 檔的位置(廢話...........
    2.Output Directory: 輸出報告的位置
    3.Project Name: 專案名稱
    4.Project Version: 版本(隨意，會顯示在報告)
    5.Test Results File: 剛剛產出的檔案
    6.Test Results Format: 這邊要選 NUnit3 (因為我們是用NUnit 生產測試報告)
    7.右邊開關: 選擇想輸出的檔案型態，我用 DHtml，HTML，Word。

![picklesui Setting](https://i.imgur.com/TsIpMYK.png)


#### 測試報告

檔案位置
![檔案位置](https://i.imgur.com/M40vENj.png)

報告形式，自帶'紅叉叉' N '綠勾勾'歐。
![報告](https://i.imgur.com/0VrdjXe.png)




參考網址:
[Pickle SpecFlow 整合 Pickles 產生活文件](https://dotblogs.com.tw/yc421206/2016/04/25/specflow_pickles_live_document)

[PicklesUI 產生活文件](https://www.youtube.com/watch?v=UkoS-KpDi2w)

