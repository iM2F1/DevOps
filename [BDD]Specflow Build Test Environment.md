[BDD]Specflow Build Test Environment 
===
# Two Session that we need to talk 1.Feature 2.Steps 3.Test Orders
- if you have something for the whole feature 
- otherwise write in the Steps 

## 1.In Feature File
    Just like all the other scenerios;
    You can give some props for the Feature, and 
    it will execute once when the feature start. 
- Background
- Given
- And

#### 1.1 in Feature File
~~~
Background: Init The Test Env
Given Create TestEnv Dir
And Create TestFile in Dir
~~~
#### 1.2 in Step Definition
~~~
        [Given(@"Create TestEnv Dir")]
        public void GivenCreateTestEnvDir()
        {
            //your code here
        }
        
        [Given(@"Create TestFile in Dir")]
        public void GivenCreateTestFileInDir()
        {
            //your code here
        }
~~~

## 2.Steps
[Reference](https://github.com/techtalk/SpecFlow/wiki/Hooks)

#### [BeforeTestRun]
#### [AfterTestRun]
    Automation logic that has to run before/after the entire test run
    Note: As most of the unit test runners do not provide a hook for executing logic once the tests have been executed, the [AfterTestRun] event is triggered by the test assembly unload event. The exact timing and thread of this execution may therefore differ for each test runner.
    The method it is applied to must be static.
#### [BeforeFeature]
#### [AfterFeature]
    Automation logic that has to run before/after executing each feature
    The method it is applied to must be static.
#### [BeforeScenario] or [Before]
#### [AfterScenario] or [After]	
    Automation logic that has to run before/after executing each scenario or scenario outline example
    Short attribute names are available from v1.8.
#### [BeforeScenarioBlock]
#### [AfterScenarioBlock]	
    Automation logic that has to run before/after executing each scenario block (e.g. between the "givens" and the "whens")
#### [BeforeStep]
#### [AfterStep]	
    Automation logic that has to run before/after executing each scenario step
    You can annotate a single method with multiple attributes.

```
        [BeforeScenario]
        public void AfterScenario()
        {
            //your code here
        }
```
or with @tag
```
        
        [BeforeScenario(@"RemoteFile")]
        public void AfterScenario()
        {
            //your code here
        }
```


## 3.Test Orders
    User Hook Execution Order to decide the order of your test.
    Otherwise, you cannot predict the testing order.
    
```
[BeforeScenario(Order = 0)]
public void CleanDatabase()
{
    // we need to run this first
}

[BeforeScenario(Order = 100)]
public void LoginUser()
{
    // we can perform login based on a clean database
}
```
