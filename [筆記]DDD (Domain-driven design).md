DDD (Domain-driven design)
===

### DDD由內而外展開
### TDD由外而內

### 為什麼要有架構?
- 協作更順暢
- 讓程式碼重複利用率更高
- 變成公司資產

### 為什麼台灣公司無法成長
- 因為台灣公司只想 work around
- 該多花一些時間檢討架構與程式碼的重用姓

### 從無到有的 DDD
1. User Story Mapping
2. DDD Model
3. Class Diagram
4. Sequence Diagram

#### 1.先用 User Story Mapping 把需求蒐集、展開、分類
#### 2.DDD Model 劃出功能的關聯圖
#### 3.把 DDD Model 轉成 Class Diagram
##### 3.1 Class 統一命名
##### 3.2 除了 Repository 需要的參數，其他下放至各類別。
#### 4.使用 Sequence Diagram 來表示功能的順序與關聯。
#### 5.無法歸類的參數方法，另外獨立 Service

### 盡量累積 Domain 才能讓公司成長，不然永遠是剪剪貼貼。
