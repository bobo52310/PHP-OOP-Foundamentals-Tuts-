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
