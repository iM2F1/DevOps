[Unit Test] Method Stub
===

[Method Stub](https://en.wikipedia.org/wiki/Method_stub)

### 題目 : 使用 Mehtond GetNowString() 取得時間字串，並驗證其是否為現在時間。

- 建構子帶 Mock 時間，UnitTest 測試 Mock 的時間是否正確。

- 建構子沒有帶時間，就以現在時間，取得現在時間比對。
    
    以上是我模糊的心得，有錯請指證。
    
    下面是我的範例
    
    

### TimeClass.cs
```

    public class TimeProvidor
    {
        private static DateTime current = DateTime.Now;

        public string GetNowString()
        {
            return current.ToString("yyyy-MM-dd hh:mm:ss.zz");
        }
        public TimeProvidor(string MockDateTime)
        {
            current = DateTime.Parse(MockDateTime);
        }
        public TimeProvidor()
        {
            current = DateTime.Now;
        }
    }


```

### UnitTest.cs
```

        private string ExpectNowString { get;  set; }
        [TestMethod]
        public void MockDateTime()
        {
            string MockDateTimeStr = "2017-04-20 20:22:39.21";
            TimeProvidor TP = new TimeProvidor(MockDateTimeStr);
            DateTime mockDT = DateTime.Parse(MockDateTimeStr);
            ExpectNowString = mockDT.ToString("yyyy-MM-dd hh:mm:ss.zz");
            Assert.AreEqual(ExpectNowString, TP.GetNowString());
        }
        [TestMethod]
        public void CurrDateTime()
        {
            TimeProvidor TP = new TimeProvidor();
            DateTime mockDT = DateTime.Now;
            ExpectNowString = mockDT.ToString("yyyy-MM-dd hh:mm:ss.zz");
            Assert.AreEqual(ExpectNowString, TP.GetNowString());
        }


```
