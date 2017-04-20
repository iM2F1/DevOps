[Unit Test] Method Stub
===

[Method Stub](https://en.wikipedia.org/wiki/Method_stub)

### 題目 : 使用 Mehtond GetNowString() 取得時間字串，並驗證其是否為現在時間。
    
    使用 Interface 段開，Dependency Injection 斷開直接使用 DateTime.now 的相依性。
    
    模擬物件取時間，取得的時間會是使用時真正取得的時間，再與現在時間做比較。
    
    以上是我模糊的心得，有錯請指證。
    
    下面是我的範例
    
    

### TimeClass.cs
```

    public class TimeClass : ImyTime
    {
        string ImyTime.GetNowString()
        {
            return DateTime.Now.ToString("yyyy-MM-dd hh:mm:ss.zz");
        }
    }
    interface ImyTime
    {
        string GetNowString();
    }


```

### UnitTest.cs
```

    [TestClass]
    public class UnitTest1
    {
        private string ExpectNowString { get;  set; }
        [TestMethod]
        public void TestMethod1()
        {
            ImyTime NTime = new TimeClass();
            ExpectNowString = string.Format("{0}-{1}-{2} {3}:{4}:{5}.{6}", DateTime.Now.ToString("yyyy"),
                DateTime.Now.ToString("MM"), DateTime.Now.ToString("dd"), DateTime.Now.ToString("hh"), 
                DateTime.Now.ToString("mm"), DateTime.Now.ToString("ss"), DateTime.Now.ToString("zz"));
            Assert.AreEqual(ExpectNowString, NTime.GetNowString());
        }
    }


```
