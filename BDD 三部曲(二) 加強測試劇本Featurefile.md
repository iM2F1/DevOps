BDD 三部曲(二) 加強測試劇本Featurefile
===

[Specflow Config說明文件](http://go.specflow.org/doc-config)

[Specflow 支援的語言Key Word](https://github.com/cucumber/gherkin/blob/master/gherkin-languages.json)

### 1.想用全中文寫 Feature 檔? (沒問題!!)
    新增 Header 在 Feature 最前面 (供台語抹通歐)
    # language: zh-TW
    

### 2.認識一下關鍵字
    讓英文不好的同學也可以寫測試。(我在說自己...)
    但是我們下面，關鍵詞還是用英語講解，避免代溝(老了...
```
"zh-TW": {
    "and": [
      "* ",
      "而且",
      "並且",
      "同時"
    ],
    "background": [
      "背景"
    ],
    "but": [
      "* ",
      "但是"
    ],
    "examples": [
      "例子"
    ],
    "feature": [
      "功能"
    ],
    "given": [
      "* ",
      "假如",
      "假設",
      "假定"
    ],
    "name": "Chinese traditional",
    "native": "繁體中文",
    "scenario": [
      "場景",
      "劇本"
    ],
    "scenarioOutline": [
      "場景大綱",
      "劇本大綱"
    ],
    "then": [
      "* ",
      "那麼"
    ],
    "when": [
      "* ",
      "當"
    ]
  }

```

### 3.使用scenarioOutline重複測試
一般的 scenario，長這樣。
```
Scenario: Add two numbers
	Given I have entered 50 into the calculator
	And I have entered 70 into the calculator
	When I press add
	Then the result should be 120 on the screen
```

因為我們要測試很多不一樣的例子，所以改用 scenarioOutline + examples 重複測試

```
scenarioOutline: Add two numbers
	Given I have entered <number1> into the calculator
	And I have entered <number2> into the calculator
	When I press add
	Then the result should be <result> on the screen
	Examples: 
	| number1 | number2 | result |
	| 50      | 70      | 120    |
	| 100     | 200     | 300    |
```
基本上這樣看起來就沒問題了。(其實還有個大坑...，但是這樣排版比較漂亮)
os:想踩我的坑嗎？想要的話可以全部給你，去踩吧！我把所有的坑都挖好在那裡了。


### 4.background
如果每個 Scenario 有共同的前置作業，就可以放到 background 執行。
```
Feature: Multiple site support
  As a Mephisto site owner
  I want to host blogs for different people
  In order to make gigantic piles of money

  Background:
    Given a global administrator named "Greg"
    And a blog named "Greg's anti-tax rants"
    And a customer named "Dr. Bill"
    And a blog named "Expensive Therapy" owned by "Dr. Bill"

  Scenario: 1

  Scenario: 2

  Scenario: 3
```

### 5.Step 呼叫另一個 Step
[在 Step 中呼叫 Step](http://specflow.org/documentation/Calling-Steps-from-Step-Definitions/)

##### 在 Step 中呼叫另一個 Step
```
[Binding]
public class CallingStepsFromStepDefinitionSteps : Steps
{
    [Given(@"the user (.*) exists")]
    public void GivenTheUserExists(string name)
    {
        // ...
    }

    [Given(@"I log in as (.*)")]
    public void GivenILogInAs(string name)
    {
        // ...
    }

    [Given(@"(.*) is logged in")]
    public void GivenIsLoggedIn(string name)
    {
        Given(string.Format("the user {0} exists", name));
        Given(string.Format("I log in as {0}", name));
    }
}   
```
##### 在 Step Definiction 想呼叫 Step 也是可以的歐。
```
[Given(@"A simple expense report")]
public void GivenASimpleExpenseReport()
{
    string[] header = {"account" , "description", "amount"};
    string[] row1 = {"INT-100" , "Taxi", "114"};
    string[] row2 = {"CUC-101" , "Peeler", "22"};
    var t = new Table(header);
    t.AddRow(row1);
    t.AddRow(row2);
    Given("an expense report for Jan 2009 with the following posts:", t);
}
```

### 6.Hooks
[hooks](http://specflow.org/documentation/Hooks/)

### 7.Scoped Bindings
前面的坑要在這裡的土填。
[Scoped Bindings](http://specflow.org/documentation/Scoped-Bindings/)

### 8.Sharing-Data-between-Bindings
[Sharing-Data-between-Bindings](http://specflow.org/documentation/Sharing-Data-between-Bindings/)


## 三部曲參考
[BDD 三部曲(一) 用"實例"來說明"程式"](https://hackmd.io/GwBgLAZgxgRlUFoxQIYiWGBTBBOKAJgOwICMKUAHAExYzXVpRA==)
