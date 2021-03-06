>PHP-OOP-Foundamentals 系列教材(TutsPlus) 
>
>Bobo 的練習紀錄+課堂筆記
>
>時數：2H 20M (共18集)

-
課程章節：

* 02 what is oop
* 03 classes vs objects
* 04 class constants and internal reference
* 05 public vs private scope
* 06 copying vs cloning
* 07 single responsibility principle
* 08 magic methods
* 09 autoloading through spl
* 10 namespaces
* 11 autoloading with psr 0
* 12 class inheritance and protected scope
* 13 overriding parent methods
* 14 abstract classes
* 15 interfaces
* 16 statics
* 17 traits
* 18 dependency injection

-
## Chapter 1~5
OOP 因為可將 property 設定為 private ，始外界無法直接存取，達到了封裝的功能。
所以需要藉由 `set()` 和 `get()` 來存取，
且因為太常用了封裝成魔術方法 `__set()` 和 `__get()` 來存取。

在存取的過程中，為了避免外界不知道此 class 有哪些 methods 而輸入錯誤
因次需要先在 class 定義 `$fillable` 來確認有哪些方法可以被 set

例如 private $fillable = array('email', 'password'); 
定義 $accessible 來確認有哪些方法可以被 get
例如 private $accessible = array('email');，

建構式(construct)用途：

* 設置類別預設屬性值。
* 預載類別特定函式。

private 成員，通常習慣在名稱開頭加上一個_(底線)來區別。

## Chapter 06 copying vs cloning

* PHP Object copy 預設為 by reference。

* 若是要 by value 需要使用 clone 指令。

## Chapter 07 single responsibility principle
依據 `single responsibility principle` (SRP,單一職責)
每個 class 只負責一個職責而且職責必須要被封裝在這個 class 內， have only one reason to change
原本在 User 內的 Validation 應該要抽出來，可以 reuse。

## Chapter 08 magic methods
兩個底線開頭的就是 `魔術方法`，介紹這些：

* `__construct()`
* `__set()`
* `__get()`
* `__toString()`
魔術方法讓你的物件更神奇，可以關注到特定事件(eg. 物件被建立/刪除時..等) 詳見範例。

## Chapter 09 autoloading through spl
使用 `spl_autoload_register()` 註冊 load 方法，來達到 autoloading

## Chapter 10 namespaces  命名空間
PHP5.3才加入的功能，最主要的目的是用來組織類別與函數，並且避免名稱的衝突
例如：
`use Symfony\Component\Console\Input\ArrayInput;`

表示使用 位在目錄 Symfony\Component\Console\內的檔名叫ArrayInput 的 class檔案

使用 require 將檔案載進來，再配合 namespace\方法 (若有自動載入，就不需要再各自include了方便!)

關鍵字 (keyword) `use` 可替過長的命名空間中的類別 (class) 取別名 (alias)

例如：
`use Name01\Name02\Name03\Demo as Another;`
`__NAMESPACE__`   // 使用此魔術常數 取得目前的 namespace

如果檔案沒有使用命名空間，則此檔內所有的 class、method 常數... 皆為全域
要使用這些 全域 class、method 可使用 `\` 反斜線開頭，代表這是定義在`global namespace` 中的東西

`\` 白話解釋就是從跟目錄開始找啦

## Chapter 11 autoloading with PSR-0
autoload function 請直接使用 PSR-0 的規範，直接貼上即可
這函數其實就是依照 PSR-0 大家約定好的命名方式，來把 Class 的檔名給切出來

autoloading 機制，原理其實很簡單。在程式產生一個類別實體時，如果找不到類別定義，就會來呼叫使用者定義的 autoloading 函數，把完整的類別名稱當做參數丟給他。

> 2014/10之後，建議使用 PSR-4 取代 PSR-0

## Chapter 12 class inheritance and protected scope
無須對外界公開的方法都應該設定為 private，才有利於封裝。

封閉性
private > protected > public

繼承：
繼承代表一種 "is-a" 的關係。

## Chapter 13 overriding parent methods
父類別的方法可以被子類別覆寫。

## Chapter 14 abstract classes
抽象 class 無法被實體化，主要用來繼承用的。

## Chapter 15 interfaces
* 功能1.介面就像是個合約，定義與規範必須實做那些方法，並且可以實現OOP的重要特色(多形)。
* 功能2.把相同操作的 class 給解耦合。

`PostJsonRepository`、`PostRssRepository`
這兩個 class 實作 PostRepository 這個介面，分別可讀入 `Json` 和 `Xml` 檔
讀入檔案分別使用 file_get_contents() 與 simplexml_load_file() 函數

## Chapter 16 statics
Using static properties and methods can help you write less verbose code. But bear in mind, statics do not behave like true objects(因為static關係，即使你new 2個物件出來，實際上存取的還是同一個物件，這點必須要注意).

## Chapter 17 Traits
替 class 加入特定的一組方法，讓這些方法可以在不同物件之間 reuse
例如加入 Accessible 這個 class 有 __set() , __get() 方法

使用方法：`在 class 內`(注意不是在外面喔)使用 `use` 就是使用 `traits`

## Chapter 18 dependency injection
DI 主要用來解耦合，真正有效的降低模組間耦合的作法
Address class 接受 不同的 `Repository` 介面注入，例如 `AddressArrayRepository`，且實作 `AddressRepositoryInterface `介面

實作
原本 AddressArrayRepository 是在 Address 內直接進行實體化(在 __construct 那)，這導致了這兩個 class 產生了耦合，

-
這個系列看完後建議繼續學習 TutsPlus 的 **Object - Oriented Design in PHP**
