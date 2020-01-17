# PHP 开发手册1.2.0

[Toc]



# 一、编程规约

## (一) 命名风格

1. 【强制】代码中的命名严禁使用拼音与英文混合的方式，更不允许直接使用中文的方式。 

    <font color="#a38e46">说明:</font> 正确的英文拼写和语法可以让阅读者易于理解，避免歧义。注意，即使纯拼音命名方式 也要避免采用。

    <font color="green">正例:</font> `alibaba / taobao / youku / hangzhou` 等国际通用的名称，可视同英文。 

    <font color="#fe694b">反例:</font> `DaZhePromotion` [打折] / `getPingfenByName() `[评分]

2. 【强制】方法名、参数名、成员变量、局部变量都统一使用 `lowerCamelCase` 风格，必须遵从驼峰形式。

    <font color="green">正例:</font> `localValue / getHttpMessage() / inputUserId`

3. 【强制】常量命名全部大写，单词间用下划线隔开，力求语义表达完整清楚，不要嫌名字长。

    <font color="green">正例:</font> `MAX_STOCK_COUNT`

    <font color="#fe694b">反例:</font> `MAX_COUNT`

4. 【强制】抽象类命名使用 `Abstract` 或 `Base` 开头;异常类命名使用 `Exception` 结尾;测试类 命名以它要测试的类的名称开始，以 `Test` 结尾。

5. 【强制】杜绝完全不规范的缩写，避免望文不知义。

    <font color="#fe694b">反例:</font>  `AbstractClass*` “缩写” 命名成 `AbsClass`; `condition` “缩写” 命名成 `condi`，此类随意缩写严重降低了代码的可阅读性。

6. 【推荐】为了达到代码自解释的目标，任何自定义编程元素在命名时，使用尽量完整的单词组合来表达其意。

    <font color="green">正例:</font> 在 SDK 中，表达原子更新的类名为: `AtomicReferenceFieldUpdater`。

    <font color="#fe694b">反例:</font> 变量 `$a` 的随意命名方式。

7. 【推荐】如果模块、接口、类、方法使用了设计模式，在命名时需体现出具体模式。 说明:将设计模式体现在名字中，有利于阅读者快速理解架构设计理念。

    <font color="green">正例:</font>  `class OrderFactory`;

    ​     	 `class LoginProxy;`

    ​           `class ResourceObserver;`

8. (微服务)接口和实现类的命名有两套规则:
    1)【强制】对于 `Service` 和 `DAO` 类，基于 **SOA** 的理念，暴露出来的服务一定是接口，内部的实现类用 `Impl` 的后缀与接口区别。 

    <font color="green">正例:</font> `CacheServiceImpl` 实现 `CacheService` 接口。

​         2)【推荐】 如果是形容能力的接口名称，取对应的形容词为接口名(通常是**–able** 的形式)。

​			<font color="green">正例:</font> `AbstractTranslator` 实现 `Translatable` 接口。

9. 【参考】各层命名规约:

    A) `Service/DAO`层方法命名规约

    1) 获取单个对象的方法用 `get` 做前缀。

    2) 获取多个对象的方法用 `list` 做前缀，复数形式结尾如: `listObjects`。

    3) 获取统计值的方法用 `count ` 做前缀。

    4) 插入的方法用 `save/insert` 做前缀。

    5) 删除的方法用 `remove/delete`  做前缀。

    6) 修改的方法用 `update` 做前缀。



## (二) 代码格式

1. 【强制】左小括号和字符之间不出现空格;同样，右小括号和字符之间也不出现空格;而左括号前需要空格。

    <font color="#fe694b">反例:</font>  **if (**<font style="background:#cdcdcd">空格</font>**a == b**<font style="background:#cdcdcd">空格</font>**)**

2. 【强制】任何运算符、三目运算符的左右两边都需要加一个空格。

    <font color="#a38e46">说明:</font> 运算符包括赋值运算符=、逻辑运算符&&、加减乘除符号等。

3. 【强制】采用 **4** 个空格缩进，禁止使用 **tab** 字符。

    <font color="#a38e46">说明:</font> 如果使用 **tab** 缩进，必须设置 **1** 个 **tab** 为 4 个空格。**IDEA** 设置 **tab** 为 4 个空格时， 请勿勾选 `Use tab character`;   而在 **eclipse** 中，必须勾选 `insert spaces for tabs`。

4. 【强制】注释的双斜线与注释内容之间有且仅有一个空格。

    <font color="green">正例:</font>  

    ```php
    // 这是示例注释，请注意在双斜线之后有一个空格
    $str = 'demo';
    ```

5. 【强制】方法参数在定义和传入时，多个参数逗号后边必须加空格。

    <font color="green">正例:</font>  下例中实参的 args1，后边必须要有一个空格。

    `method($arg1, $arg2, $arg3);`

6. 【推荐】单个方法的总行数不超过 80 行。 
    <font color="#a38e46">说明:</font>  包括结束右大括号、方法内代码、注释、空行、回车及任何不可见字符的总行数不超过 80 行。 
    <font color="green">正例:</font>  代码逻辑分清红花和绿叶，个性和共性，绿叶逻辑单独出来成为额外方法，使主干代码更加清晰;共性逻辑抽取成为共性方法，便于复用和维护。

7. 【推荐】不同逻辑、不同语义、不同业务的代码之间插入一个空行分隔开来以提升可读性。 说明:任何情形，没有必要插入多个空行进行隔开。

其他代码格式采用 **PSR** 标准规范，本文不赘述；

>PSR 是 PHP Standard Recommendations 的简写，由 [PHP FIG](https://github.com/php-fig) 组织制定的 PHP 规范，是 PHP 开发的实践标准。
>
>[PHP FIG](https://github.com/php-fig)，FIG 是 Framework Interoperability Group（框架可互用性小组）的缩写，由几位开源框架的开发者成立于 2009 年，从那开始也选取了很多其他成员进来（包括但不限于 [Laravel](http://laravel.com/), [Joomla](https://www.joomla.org/), [Drupal](https://www.drupal.org/), [Composer](https://getcomposer.org/), [Phalcon](https://phalconphp.com/en/), [Slim](http://www.slimframework.com/), [Symfony](http://symfony.com/), [Zend Framework](http://framework.zend.com/) 等），虽然不是「官方」组织，但也代表了大部分的 PHP 社区。
>
>项目的目的在于：通过框架作者或者框架的代表之间讨论，以最低程度的限制，制定一个协作标准，各个框架遵循统一的编码规范，避免各家自行发展的风格阻碍了 PHP 的发展，解决这个程序设计师由来已久的困扰。
>
>目前已表决通过了不少套标准，已经得到大部分 PHP 框架的支持和认可。

- [PSR-1 基础编码规范](https://learnku.com/docs/psr/basic-coding-standard/1605)
- [PSR-2 编码风格规范](https://learnku.com/docs/psr/psr-2-coding-style-guide/1606)
- [PSR-3 日志接口规范](https://learnku.com/docs/psr/psr-3-logger-interface/1607)
- [PSR-4 自动加载规范](https://learnku.com/docs/psr/psr-4-autoloader/1608)

## (三) OOP 规约

1. 【强制】避免通过一个类的对象引用访问此类的静态变量或静态方法，无谓增加编译器解析成本，直接用类名来访问即可。

2. 【强制】所有的覆写方法，必须加 `@override`注释。

3. 【强制】外部正在调用依赖的接口，不允许修改方法签名，避免对接口调用方产生影响。接口过时必须加 `@deprecated` 注释，并清晰地说明采用的新接口或者新服务是什么。

4. 【强制】构造方法里面禁止加入任何业务逻辑，如果有初始化逻辑，请放在 `init` 方法中。

5. 【推荐】 类内方法定义的顺序依次是: 公有方法或保护方法 > 私有方法 > `getter/setter` 方法。

    <font color="#a38e46">说明:</font>  公有方法是类的调用者和维护者最关心的方法，首屏展示最好;保护方法虽然只是子类 关心，也可能是“模板设计模式”下的核心方法;而私有方法外部一般不需要特别关心，是一个 黑盒实现;因为承载的信息价值较低，所有 `Service` 和 `DAO` 的 `getter/setter` 方法放在类体最后。

6. 【推荐】`setter` 方法中，参数名称与类成员变量名称一致，`this->成员名 = 参数名`。在 `getter/setter` 方法中，不要增加业务逻辑，增加排查问题的难度。

7. 【推荐】类成员与方法访问控制从严:

    1) 如果不允许外部直接通过`new` 来创建对象，那么构造方法必须是 `private`。 

    2) 工具类不允许有 `public` 构造方法。

    3) 类非 `static` 成员变量并且与子类共享，必须是 `protected`。

    4) 类非 `static` 成员变量并且仅在本类使用，必须是 `private`。

    5) 类 `static` 成员变量如果仅在本类使用，必须是 `private`。

    6) 类成员方法只供类内部调用，必须是 `private`。

    7) 类成员方法只对继承类公开，那么限制为 `protected`。

    <font color="#a38e46">说明:</font>  任何类、方法、参数、变量，严控访问范围。过于宽泛的访问范围，不利于模块解耦。 

    思考:  如果是一个 `private` 的方法，想删除就删除，可是一个 `public` 的 `service` 成员方法或 成员变量，删除一下，不得手心冒点汗吗?变量像自己的小孩，尽量在自己的视线内，变量作用域太大，无限制的到处跑，那么你会担心的。

## (四) 控制语句

1. 【强制】在一个 `switch` 块内，每个 `case` 要么通过 `break/return `等来终止，要么注释说明程 序将继续执行到哪一个 `case` 为止;在一个` switch` 块内，都必须包含一个` default `语句并且放在最后，即使空代码。

2. 【强制】在 `if/else/for/while/do` 语句中必须使用大括号。即使只有一行代码，避免采用单行的编码方式:

    `if (condition) statements`;

3. 【强制】在高并发场景中，避免使用”等于”判断作为中断或退出的条件。

    <font color="#a38e46">说明:</font>  如果并发控制没有处理好，容易产生等值判断被“击穿”的情况，使用大于或小于的区间 判断条件来代替。

    <font color="#fe694b">反例:</font>  判断剩余奖品数量等于 0 时，终止发放奖品，但因为并发处理错误导致奖品数量瞬间变 成了负数，这样的话，活动无法终止。

4. 【推荐】表达异常的分支时，少用 `if-else` 方式，这种方式可以改写成:

    ```php
    if ($condition) {
        ...
        return $obj; 
    }
    // 接着写 else 的业务逻辑代码;
    ```

    <font color="#a38e46">说明:</font>  如果非得使用` if()...else if()...else...`方式表达逻辑，【强制】避免后续代码维护困难，请勿超过 3 层。

    <font color="green">正例:</font>  超过 3 层的 `if-else` 的逻辑判断代码可以使用卫语句、策略模式、状态模式等来实现， 其中卫语句示例如下:

    ```php
    public function today()
    {
        if (isBusy()) {
           echo 'change time';
           return;
        }
    	 if (isFree()) {
         	echo 'go to travel';
         	return;
        }
      
        echo 'staty at home to learn Coding Guidelines';
        return;
    }
    ```

5. 【推荐】除常用方法(如 `getXxx/isXxx`)等外，不要在条件判断中执行其它复杂的语句，将复杂逻辑判断的结果赋值给一个有意义的布尔变量名，以提高可读性。

    <font color="#a38e46">说明:</font>  很多` if `语句内的逻辑相当复杂，阅读者需要分析条件表达式的最终结果，才能明确什么样的条件执行什么样的语句，那么，如果阅读者分析逻辑表达式错误呢?

    <font color="green">正例:</font>  

    ```php
    // 伪代码如下
    existed = (file.open(fileName, "w") != null) && (...) || (...);
    if (existed) {
        ...
    }
    ```

    <font color="#fe694b">反例:</font>  

    ```php
    if (file.open(fileName, "w") != null) && (...) || (...)) {
        ...
    }
    ```

6. 【推荐】循环体中的语句要考量性能，以下操作尽量移至循环体外处理，如定义对象、变量、获取数据库连接，进行不必要的 `try-catch` 操作(这个 `try-catch` 是否可以移至循环体外)。

7. 【推荐】避免采用取反逻辑运算符。 说明:取反逻辑不利于快速理解，并且取反逻辑写法必然存在对应的正向逻辑写法。 

    <font color="green">正例:</font>  使用 `if (x < 628) `来表达` x `小于` 628`。

    <font color="#fe694b">反例:</font>  使用` if (!(x >= 628)) `来表达 `x `小于` 628`。

8. 【推荐】接口入参保护，这种场景常见的是用作批量操作的接口。

    <font color="#a38e46">说明:</font>  接口入参保护, “保护”的是 服务端应用，即接口提供方，最常见的做法就是校验入参的有效值范围和设置批量操作白名单；比如，接口入参中包含日期时，校验日期必须在N天范围内，或者请求返回的记录总数必须在 X 条以内（比如10W条，否则缩小请求查询的记录范围），或者请求返回的记录必须分页查询返回；
    尤其是批量操作，因为批量操作非常耗时耗资源（服务端），批量操作的批量数应该有上限，而不是无限的。
    假如客户端请求一次批量操作10W笔转账订单，服务器应该果断拒绝，而不是忠实执行，会对服务端造成严重影响的批量请求，服务器端应做好保护性编程，必要时应直接失败，并在 `Result` 中返回明确的 `errorCode` 和 `errorMsg`;
    入参保护，一般都是通过卫语句实现：`if（请求记录>10000条） return；`直接返回。

9. 【参考】下列情形，需要进行参数校验:

    1) 调用频次低的方法。

    2) 执行时间开销很大的方法。此情形中，参数校验时间几乎可以忽略不计，但如果因为参数错误导致中间执行回退，或者错误，那得不偿失。

    3) 需要极高稳定性和可用性的方法。

    4) 对外提供的开放接口，不管是 `RPC/API/HTTP`接口。

    5) 敏感权限入口。

10. 【参考】下列情形，不需要进行参数校验:

    1) 极有可能被循环调用的方法。但在方法说明里必须注明外部参数检查要求。

    2) 底层调用频度比较高的方法。毕竟是像纯净水过滤的最后一道，参数错误不太可能到底层才会暴露问题。一般` DAO` 层与` Service` 层都在同一个应用中，部署在同一台服务器中，所 以 `DAO` 的参数校验，可以省略。3) 被声明成`private`只会被自己代码所调用的方法，如果能够确定调用方法的代码传入参 数已经做过检查或者肯定不会有问题，此时可以不校验数。

## (五) 注释规约

1. 【强制】类、类属性、类方法的注释必须使用 **PHPDoc** 规范，使用`/**内容*/`格式，不得使用` // xxx`方式。

    <font color="#a38e46">说明:</font>  在 IDE 编辑窗口中，PHPDoc 方式会提示相关注释，生成 PHPDoc 可以正确输出相应注 释;在 IDE 中，工程调用方法时，不进入方法即可悬浮提示方法、参数、返回值的意义，提高阅读效率。    

2. 【强制】所有的抽象方法(包括接口中的方法)必须要用 **PHPDoc** 注释、除了返回值、参数、 异常说明外，还必须指出该方法做什么事情，实现什么功能。

    <font color="#a38e46">说明:</font>  对子类的实现要求，或者调用注意事项，请一并说明。

3. 【强制】所有的类都必须添加创建者和创建日期。

4. 【强制】方法内部单行注释，在被注释语句上方另起一行，使用`//`注释。方法内部多行注释使用`/* */`注释，注意与代码对齐。

5. 【强制】所有的枚举类型字段必须要有注释，说明每个数据项的用途。

6. 【推荐】与其“半吊子”英文来注释，不如用中文注释把问题说清楚。专有名词与关键字保持英文原文即可。

    <font color="#fe694b">反例:</font>  “TCP 连接超时”解释成“传输控制协议连接超时”，理解反而费脑筋。

7. 【推荐】代码修改的同时，注释也要进行相应的修改，尤其是参数、返回值、异常、核心逻辑 等的修改。

    <font color="#a38e46">说明:</font> 代码与注释更新不同步，就像路网与导航软件更新不同步一样，如果导航软件严重滞后， 就失去了导航的意义。

8. 【参考】谨慎注释掉代码。在上方详细说明，而不是简单地注释掉。如果无用，则删除。 

    <font color="#a38e46">说明:</font> 代码被注释掉有两种可能性:

    ​	1)后续会恢复此段代码逻辑。

    ​	2)永久不用。前者如果没 有备注信息，难以知晓注释动机。后者建议直接删掉(代码仓库保存了历史代码)。

9. 【参考】对于注释的要求:第一、能够准确反应设计思想和代码逻辑;第二、能够描述业务含 义，使别的程序员能够迅速了解到代码背后的信息。完全没有注释的大段代码对于阅读者形同天书，注释是给自己看的，即使隔很长时间，也能清晰理解当时的思路;注释也是给继任者看 的，使其能够快速接替自己的工作。

10. 【参考】好的命名、代码结构是自解释的，注释力求精简准确、表达到位。避免出现注释的一个极端:过多过滥的注释，代码的逻辑一旦修改，修改注释是相当大的负担。

    <font color="#fe694b">反例:</font>  

    ```php
    // put elephant into fridge
    put(elephant, fridge);
    ```

    方法名 `put`，加上两个有意义的变量名 `elephant` 和 `fridge`，已经说明了这是在干什么，语义清晰的代码不需要额外的注释。

11. 【参考】特殊注释标记，请注明标记人与标记时间。注意及时处理这些标记，通过标记扫描， 经常清理此类标记。线上故障有时候就是来源于这些标记处的代码。

    1) 待办事宜(<font style="color:#1d0cfa;font-weight:bold;">TODO</font>):( 标记人，标记时间，[预计处理时间]) 表示需要实现，但目前还未实现的功能。

    2) 错误，不能工作(<font style="color:#1d0cfa;font-weight:bold;">FIXME</font>)):(标记人，标记时间，[预计处理时间])

    在注释中用 **FIXME** 标记某代码是错误的，而且不能工作，需要及时纠正的情况。

## (六) 其它

1. 【推荐】及时清理不再使用的代码段或配置信息。 

    <font color="#a38e46">说明:</font> 对于垃圾代码或过时配置，坚决清理干净，避免程序过度臃肿，代码冗余。

    <font color="green">正例:</font> 对于暂时被注释掉，后续可能恢复使用的代码片断，在注释代码上方，统一规定使用三个斜杠(`///`)来说明注释掉代码的理由。

2. 【强制】`catch` 时请分清稳定代码和非稳定代码，稳定代码指的是无论如何不会出错的代码。 对于非稳定代码的 `catch `尽可能进行区分异常类型，再做对应的异常处理。 

    <font color="#a38e46">说明:</font> 对大段代码进行 try-catch，使程序无法根据不同的异常做出正确的应激反应，也不利于定位问题，这是一种不负责任的表现。 

    <font color="green">正例:</font> 用户注册的场景中，如果用户输入非法字符，或用户名称已存在，或用户输入密码过于 简单，在程序上作出分门别类的判断，并提示给用户。

3. 【强制】捕获异常是为了处理它，不要捕获了却什么都不处理而抛弃之，如果不想处理它，请将该异常抛给它的调用者。最外层的业务使用者，必须处理异常，将其转化为用户可以理解的内容。

4. 【强制】有 `try` 块放到了事务代码中，`catch` 异常后，如果需要回滚事务，一定要注意手动回 滚事务。

5. 【强制】`for` 循环嵌套优化 `for` 循环嵌套相⽐于if嵌套来说更加复杂，阅读起来会更麻烦，下⾯说说⼏点要注意的东⻄：

    1. 最多只能两层`for`循环嵌套 
    2. 提取内层循环到新函数中 
    3. 多层循环时，不要简单地为索引变量命名为`i，j，k`等，容易造成混淆，要有具体的意思 提取复杂逻辑，语义化，有的时候，我们会写出⼀些⽐较复杂的逻辑，阅读代码的⼈看到后可能搞不清楚要做什么，这个时候，就应该提取出这段复杂的逻辑代码。 

# 二、RESTful API 设计规范

## Protocol

客户端在通过 `API` 与后端服务通信的过程中，`应该` 使用 `HTTPS` 协议。

## API Root URL

`API` 的根入口点应尽可能保持足够简单，这里有两个常见的 `URL` 根例子：

- api.example.com/*
- example.com/api/*

> 如果你的应用很庞大或者你预计它将会变的很庞大，那 `应该` 将 `API` 放到子域下（`api.example.com`）。这种做法可以保持某些规模化上的灵活性。

## Versioning

所有的 `API` 必须保持向后兼容，你 `必须` 在引入新版本 `API` 的同时确保旧版本 `API` 仍然可用。所以 `应该` 为其提供版本支持。

目前比较常见的两种版本号形式：

### 在 URL 中嵌入版本编号

```
api.example.com/v1/*
```

这种做法是版本号直观、易于调试；另一种做法是，将版本号放在 `HTTP Header` 头中：

### 通过媒体类型来指定版本信息

```
Accept: application/vnd.example.com.v1+json
```

其中 `vnd` 表示 `Standards Tree` 标准树类型，有三个不同的树: `x`，`prs` 和 `vnd`。你使用的标准树需要取决于你开发的项目

- 未注册的树（`x`）主要表示本地和私有环境
- 私有树（`prs`）主要表示没有商业发布的项目
- 供应商树（`vnd`）主要表示公开发布的项目

> 后面几个参数依次为应用名称（一般为应用域名）、版本号、期望的返回格式。

## Endpoints

端点就是指向特定资源或资源集合的 `URL`。在端点的设计中，你 `必须` 遵守下列约定：

- URL 的命名 `必须` 全部小写
- URL 中资源（`resource`）的命名 `必须` 是名词，并且 `必须` 是复数形式
- `必须` 优先使用 `Restful` 类型的 URL
- URL `必须` 是易读的
- URL `一定不可` 暴露服务器架构

> 至于 URL 是否必须使用连字符（`-`） 或下划线（`_`），不做硬性规定，但 `必须` 根据团队情况统一一种风格。

来看一个反例

- https://api.example.com/getUserInfo?userid=1
- https://api.example.com/getusers
- https://api.example.com/sv/u
- https://api.example.com/cgi-bin/users/get_user.php?userid=1

再来看一个正列

- https://api.example.com/zoos
- https://api.example.com/animals
- https://api.example.com/zoos/{zoo}/animals
- https://api.example.com/animal_types
- https://api.example.com/employees

## HTTP 动词

对于资源的具体操作类型，由 `HTTP` 动词表示。常用的 `HTTP` 动词有下面五个（括号里是对应的 `SQL` 命令）。

- GET（SELECT）：从服务器取出资源（一项或多项）。
- POST（CREATE）：在服务器新建一个资源。
- PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）。
- PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性）。
- DELETE（DELETE）：从服务器删除资源。

其中

1 删除资源 `必须` 用 `DELETE` 方法 2 创建新的资源 `必须` 使用 `POST` 方法 3 更新资源 `应该` 使用 `PUT` 方法 4 获取资源信息 `必须` 使用 `GET` 方法

针对每一个端点来说，下面列出所有可行的 `HTTP` 动词和端点的组合

| 请求方法 | URL                              | 描述                                             |
| -------- | -------------------------------- | ------------------------------------------------ |
| GET      | /zoos                            | 列出所有的动物园(ID和名称，不要太详细)           |
| POST     | /zoos                            | 新增一个新的动物园                               |
| GET      | /zoos/{zoo}                      | 获取指定动物园详情                               |
| PUT      | /zoos/{zoo}                      | 更新指定动物园(整个对象)                         |
| PATCH    | /zoos/{zoo}                      | 更新动物园(部分对象)                             |
| DELETE   | /zoos/{zoo}                      | 删除指定动物园                                   |
| GET      | /zoos/{zoo}/animals              | 检索指定动物园下的动物列表(ID和名称，不要太详细) |
| GET      | /animals                         | 列出所有动物(ID和名称)。                         |
| POST     | /animals                         | 新增新的动物                                     |
| GET      | /animals/{animal}                | 获取指定的动物详情                               |
| PUT      | /animals/{animal}                | 更新指定的动物(整个对象)                         |
| PATCH    | /animals/{animal}                | 更新指定的动物(部分对象)                         |
| GET      | /animal_types                    | 获取所有动物类型(ID和名称，不要太详细)           |
| GET      | /animal_types/{type}             | 获取指定的动物类型详情                           |
| GET      | /employees                       | 检索整个雇员列表                                 |
| GET      | /employees/{employee}            | 检索指定特定的员工                               |
| GET      | /zoos/{zoo}/employees            | 检索在这个动物园工作的雇员的名单(身份证和姓名)   |
| POST     | /employees                       | 新增指定新员工                                   |
| POST     | /zoos/{zoo}/employees            | 在特定的动物园雇佣一名员工                       |
| DELETE   | /zoos/{zoo}/employees/{employee} | 从某个动物园解雇一名员工                         |

> 超出 `Restful` 端点的，`应该` 模仿上表的方式来定义端点。

## Filtering

> 如果记录数量很多，服务器不可能都将它们返回给用户。API `应该` 提供参数，过滤返回结果。下面是一些常见的参数。

- ?limit=10：指定返回记录的数量
- ?offset=10：指定返回记录的开始位置。
- ?page=2&per_page=100：指定第几页，以及每页的记录数。
- ?sortby=name&order=asc：指定返回结果按照哪个属性排序，以及排序顺序。
- ?animal_type_id=1：指定筛选条件

所有 `URL` 参数 `必须` 是全小写，`必须` 使用下划线类型的参数形式。

> 分页参数 `必须` 固定为 `page`、`per_page`

经常使用的、复杂的查询 `应该` 标签化，降低维护成本。如

```
GET /trades?status=closed&sort=sortby=name&order=asc

# 可为其定制快捷方式
GET /trades/recently_closed
```

## Authentication

`应该` 使用 `OAuth2.0` 的方式为 API 调用者提供登录认证。`必须` 先通过登录接口获取 `Access Token` 后再通过该 `token` 调用需要身份认证的 `API`。

Oauth 的端点设计示列

- RFC 6749 /token
- Twitter /oauth2/token
- Fackbook /oauth/access_token
- Google /o/oauth2/token
- Github /login/oauth/access_token
- Instagram /oauth/authorize

客户端在获得 `access token` 的同时 `必须` 在响应中包含一个名为 `expires_in` 的数据，它表示当前获得的 `token` 会在多少 `秒` 后失效。

```
{
    "access_token": "token....",
    "token_type": "Bearer",
    "expires_in": 3600
}
```

客户端在请求需要认证的 `API` 时，`必须` 在请求头 `Authorization` 中带上 `access_token`。

```
Authorization: Bearer token...
```

当超过指定的秒数后，`access token` 就会过期，再次用过期/或无效的 `token` 访问时，服务端 `应该` 返回 `invalid_token` 的错误或 `401` 错误码。

```
HTTP/1.1 401 Unauthorized
Content-Type: application/json
Cache-Control: no-store
Pragma: no-cache

{
    "error": "invalid_token"
}
```

> 开发中，`应该` 使用 [JWT](https://github.com/tymondesigns/jwt-auth) 来为管理你的 Token，并且 `一定不可` 在 `api` 中间件中开启请求 `session`。

## Response

所有的 `API` 响应，`必须` 遵守 `HTTP` 设计规范，`必须` 选择合适的 `HTTP` 状态码。`一定不可` 所有接口都返回状态码为 `200` 的 `HTTP` 响应，如：

```
HTTP/1.1 200 ok
Content-Type: application/json
Server: example.com

{
    "code": 0,
    "msg": "success",
    "data": {
        "username": "username"
    }
}
```

或

```
HTTP/1.1 200 ok
Content-Type: application/json
Server: example.com

{
    "code": -1,
    "msg": "该活动不存在",
}
```

下表列举了常见的 `HTTP` 状态码

| 状态码 | 描述                                                 |
| ------ | ---------------------------------------------------- |
| 1xx    | 代表请求已被接受，需要继续处理                       |
| 2xx    | 请求已成功，请求所希望的响应头或数据体将随此响应返回 |
| 3xx    | 重定向                                               |
| 4xx    | 客户端原因引起的错误                                 |
| 5xx    | 服务端原因引起的错误                                 |

> 只有来自客户端的请求被正确的处理后才能返回 `2xx` 的响应，所以当 API 返回 `2xx` 类型的状态码时，前端 `必须` 认定该请求已处理成功。

必须强调的是，所有 `API` `一定不可` 返回 `1xx` 类型的状态码。当 `API` 发生错误时，`必须` 返回出错时的详细信息。目前常见返回错误信息的方法有两种：

1、将错误详细放入 `HTTP` 响应首部；

```
X-MYNAME-ERROR-CODE: 4001
X-MYNAME-ERROR-MESSAGE: Bad authentication token
X-MYNAME-ERROR-INFO: http://docs.example.com/api/v1/authentication
```

2、直接放入响应实体中；

```
HTTP/1.1 401 Unauthorized
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 10:02:59 GMT
Connection: keep-alive

{"error_code":40100,"message":"Unauthorized"}
```

考虑到易读性和客户端的易处理性，我们 `必须` 把错误信息直接放到响应实体中，并且错误格式 `应该` 满足如下格式：

```
{
    "message": "您查找的资源不存在",
    "error_code": 404001
}
```

其中错误码（`error_code`）`必须` 和 `HTTP` 状态码对应，也方便错误码归类，如：

```
HTTP/1.1 429 Too Many Requests
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 10:15:52 GMT
Connection: keep-alive

{"error_code":429001,"message":"你操作太频繁了"}
HTTP/1.1 403 Forbidden
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 10:19:27 GMT
Connection: keep-alive

{"error_code":403002,"message":"用户已禁用"}
```

`应该` 在返回的错误信息中，同时包含面向开发者和面向用户的提示信息，前者可方便开发人员调试，后者可直接展示给终端用户查看如：

```
{
    "message": "直接展示给终端用户的错误信息",
    "error_code": "业务错误码",
    "error": "供开发者查看的错误信息",
    "debug": [
        "错误堆栈，必须开启 debug 才存在"
    ]
}
```

下面详细列举了各种情况 API 的返回说明。

### 200 ok

`200` 状态码是最常见的 `HTTP` 状态码，在所有 **成功** 的 `GET` 请求中，`必须` 返回此状态码。`HTTP` 响应实体部分 `必须` 直接就是数据，不要做多余的包装。

错误示例：

```
HTTP/1.1 200 ok
Content-Type: application/json
Server: example.com

{
    "user": {
        "id":1,
        "nickname":"fwest",
        "username": "example"
    }
}
```

正确示例：

1、获取单个资源详情

```
{
    "id": 1,
    "username": "godruoyi",
    "age": 88,
}
```

2、获取资源集合

```
[
    {
        "id": 1,
        "username": "godruoyi",
        "age": 88,
    },
    {
        "id": 2,
        "username": "foo",
        "age": 88,
    }
]
```

3、额外的媒体信息

```
{
    "data": [
        {
            "id": 1,
            "avatar": "https://lorempixel.com/640/480/?32556",
            "nickname": "fwest",
            "last_logined_time": "2018-05-29 04:56:43",
            "has_registed": true
        },
        {
            "id": 2,
            "avatar": "https://lorempixel.com/640/480/?86144",
            "nickname": "zschowalter",
            "last_logined_time": "2018-06-16 15:18:34",
            "has_registed": true
        }
    ],
    "meta": {
        "pagination": {
            "total": 101,
            "count": 2,
            "per_page": 2,
            "current_page": 1,
            "total_pages": 51,
            "links": {
                "next": "http://api.example.com?page=2"
            }
        }
    }
}
```

> 其中，分页和其他额外的媒体信息，必须放到 `meta` 字段中。

### 201 Created

当服务器创建数据成功时，`应该` 返回此状态码。常见的应用场景是使用 `POST` 提交用户信息，如：

- 添加了新用户
- 上传了图片
- 创建了新活动

等，都可以返回 `201` 状态码。需要注意的是，你可以选择在用户创建成功后返回新用户的数据

```
HTTP/1.1 201 Created
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Date: Sun, 24 Jun 2018 09:13:40 GMT
Connection: keep-alive

{
    "id": 1,
    "avatar": "https:\/\/lorempixel.com\/640\/480\/?32556",
    "nickname": "fwest",
    "last_logined_time": "2018-05-29 04:56:43",
    "created_at": "2018-06-16 17:55:55",
    "updated_at": "2018-06-16 17:55:55"
}
```

也可以返回一个响应实体为空的 `HTTP Response` 如：

```
HTTP/1.1 201 Created
Server: nginx/1.11.9
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Date: Sun, 24 Jun 2018 09:12:20 GMT
Connection: keep-alive
```

> 这里我们 `应该` 采用第二种方式，因为大多数情况下，客户端只需要知道该请求操作成功与否，并不需要返回新资源的信息。

### 202 Accepted

该状态码表示服务器已经接受到了来自客户端的请求，但还未开始处理。常用短信发送、邮件通知、模板消息推送等这类很耗时需要队列支持的场景中；

> 返回该状态码时，响应实体 `必须` 为空。

```
HTTP/1.1 202 Accepted
Server: nginx/1.11.9
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Date: Sun, 24 Jun 2018 09:25:15 GMT
Connection: keep-alive
```

### 204 No Content

该状态码表示响应实体不包含任何数据，其中：

- 在使用 `DELETE` 方法删除资源 **成功** 时，`必须` 返回该状态码
- 使用 `PUT`、`PATCH` 方法更新数据 **成功** 时，也 `应该` 返回此状态码

```
HTTP/1.1 204 No Content
Server: nginx/1.11.9
Date: Sun, 24 Jun 2018 09:29:12 GMT
Connection: keep-alive
```

### 3xx 重定向

所有 `API` `不该` 返回 `3xx` 类型的状态码。因为 `3xx` 类型的响应格式一般为下列格式：

```
HTTP/1.1 302 Found
Server: nginx/1.11.9
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 09:41:50 GMT
Location: https://example.com
Connection: keep-alive

<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8" />
        <meta http-equiv="refresh" content="0;url=https://example.com" />

        <title>Redirecting to https://example.com</title>
    </head>
    <body>
        Redirecting to <a href="https://example.com">https://example.com</a>.
    </body>
</html>
```

所有 `API` `一定不可` 返回纯 `HTML` 结构的响应；若一定要使用重定向功能，`可以` 返回一个响应实体为空的 `3xx` 响应，并在响应头中加上 `Location` 字段:

```
HTTP/1.1 302 Found
Server: nginx/1.11.9
Content-Type: text/html; charset=UTF-8
Transfer-Encoding: chunked
Date: Sun, 24 Jun 2018 09:52:50 GMT
Location: https://godruoyi.com
Connection: keep-alive
```

### 400 Bad Request

由于明显的客户端错误（例如，请求语法格式错误、无效的请求、无效的签名等），服务器 `应该` 放弃该请求。

> 当服务器无法从其他 4xx 类型的状态码中找出合适的来表示错误类型时，都 `必须` 返回该状态码。

```
HTTP/1.1 400 Bad Request
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 13:22:36 GMT
Connection: keep-alive

{"error_code":40000,"message":"无效的签名"}
```

### 401 Unauthorized

该状态码表示当前请求需要身份认证，以下情况都 `必须` 返回该状态码。

- 未认证用户访问需要认证的 API
- access_token 无效/过期

> 客户端在收到 `401` 响应后，都 `应该` 提示用户进行下一步的登录操作。

```
HTTP/1.1 401 Unauthorized
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
WWW-Authenticate: JWTAuth
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 13:17:02 GMT
Connection: keep-alive

{"message":"Token Signature could not be verified.","error_code": "40100"}
```

### 403 Forbidden

该状态码可以简单的理解为没有权限访问该请求，服务器收到请求但拒绝提供服务。

如当普通用户请求操作管理员用户时，`必须` 返回该状态码。

```
HTTP/1.1 403 Forbidden
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 13:05:34 GMT
Connection: keep-alive

{"error_code":40301,"message":"权限不足"}
```

### 404 Not Found

该状态码表示用户请求的资源不存在，如

- 获取不存在的用户信息 （get /users/9999999）
- 访问不存在的端点

都 `必须` 返回该状态码，若该资源已永久不存在，则 `应该` 返回 `410` 响应。

### 405 Method Not Allowed

当客户端使用的 `HTTP` 请求方法不被服务器允许时，`必须` 返回该状态码。

> 如客户端调用了 `POST` 方法来访问只支持 GET 方法的 API

该响应 `必须` 返回一个 `Allow` 头信息用以表示出当前资源能够接受的请求方法的列表。

```
HTTP/1.1 405 Method Not Allowed
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Allow: GET, HEAD
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 12:30:57 GMT
Connection: keep-alive

{"message":"405 Method Not Allowed","error_code": 40500}
```

### 406 Not Acceptable

`API` 在不支持客户端指定的数据格式时，应该返回此状态码。如支持 `JSON` 和 `XML` 输出的 `API` 被指定返回 `YAML` 格式的数据时。

> Http 协议一般通过请求首部的 Accept 来指定数据格式

### 408 Request Timeout

客户端请求超时时 `必须` 返回该状态码，需要注意的时，该状态码表示 **客户端请求超时**，在涉及第三方 `API` 调用超时时，`一定不可` 返回该状态码。

### 409 Confilct

该状态码表示因为请求存在冲突无法处理。如通过手机号码提供注册功能的 `API`，当用户提交的手机号已存在时，`必须` 返回此状态码。

```
HTTP/1.1 409 Conflict
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 12:19:04 GMT
Connection: keep-alive

{"error_code":40900,"message":"手机号已存在"}
```

### 410 Gone

和 `404` 类似，该状态码也表示请求的资源不存在，只是 `410` 状态码进一步表示所请求的资源已不存在，并且未来也不会存在。在收到 `410` 状态码后，客户端 `应该` 停止再次请求该资源。

### 413 Request Entity Too Large

该状态码表示服务器拒绝处理当前请求，因为该请求提交的实体数据大小超过了服务器愿意或者能够处理的范围。

> 此种情况下，服务器可以关闭连接以免客户端继续发送此请求。

如果这个状况是临时的，服务器 `应该` 返回一个 `Retry-After` 的响应头，以告知客户端可以在多少时间以后重新尝试。

### 414 Request-URI Too Long

该状态码表示请求的 `URI` 长度超过了服务器能够解释的长度，因此服务器拒绝对该请求提供服务。

### 415 Unsupported Media Type

通常表示服务器不支持客户端请求首部 `Content-Type` 指定的数据格式。如在只接受 `JSON` 格式的 `API` 中放入 `XML` 类型的数据并向服务器发送，都 `应该` 返回该状态码。

该状态码也可用于如：只允许上传图片格式的文件，但是客户端提交媒体文件非法或不是图片类型，这时 `应该` 返回该状态码：

```
HTTP/1.1 415 Unsupported Media Type
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 12:09:40 GMT
Connection: keep-alive

{"error_code":41500,"message":"不允许上传的图片格式"}
```

### 429 Too Many Requests

该状态码表示用户请求次数超过允许范围。如 `API` 设定为 `60次/分钟`，当用户在一分钟内请求次数超过 60 次后，都 `应该` 返回该状态码。并且也 `应该` 在响应首部中加上下列头部：

```
X-RateLimit-Limit: 10 请求速率（由应用设定，其单位一般为小时/分钟等，这里是 10次/5分钟）
X-RateLimit-Remaining: 0 当前剩余的请求数量
X-RateLimit-Reset: 1529839462 重置时间
Retry-After: 120 下一次访问应该等待的时间（秒）
```

列子

```
HTTP/1.1 429 Too Many Requests
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
X-RateLimit-Limit: 10
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 1529839462
Retry-After: 290
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 11:19:32 GMT
Connection: keep-alive

{"message":"You have exceeded your rate limit.","error_code":42900}
```

`必须` 为所有的 API 设置 Rate Limit 支持。

### 500 Internal Server Error

该状态码 `必须` 在服务器出错时抛出，对于所有的 `500` 错误，都 `应该` 提供完整的错误信息支持，也方便跟踪调试。

### 503 Service Unavailable

该状态码表示服务器暂时处理不可用状态，当服务器需要维护或第三方 `API` 请求超时/不可达时，都 `应该` 返回该状态码，其中若是主动关闭 API 服务，`应该 `在返回的响应首部加上 `Retry-After` 头部，表示多少秒后可以再次访问。

```
HTTP/1.1 503 Service Unavailable
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Cache-Control: no-cache, private
Date: Sun, 24 Jun 2018 10:56:20 GMT
Retry-After: 60
Connection: keep-alive

{"error_code":50300,"message":"服务维护中"}
```

其他 `HTTP` 状态码请参考 [HTTP 状态码- 维基百科](https://zh.wikipedia.org/zh-hans/HTTP状态码)。

# 三、异常日志

## (一) 异常处理

1. 【强制】异常不要用来做流程控制，条件控制。 

    <font color="#a38e46">说明:</font>  异常设计的初衷是解决程序运行中的各种意外情况，且异常的处理效率比条件判断方式要低很多。

2. 【强制】`catch` 时请分清稳定代码和非稳定代码，稳定代码指的是无论如何不会出错的代码。 对于非稳定代码的 `catch` 尽可能进行区分异常类型，再做对应的异常处理。 

    <font color="#a38e46">说明:</font> 对大段代码进行 `try-catch`，使程序无法根据不同的异常做出正确的应激反应，也不利于定位问题，这是一种不负责任的表现。 

    <font color="green">正例:</font>  用户注册的场景中，如果用户输入非法字符，或用户名称已存在，或用户输入密码过于简单，在程序上作出分门别类的判断，并提示给用户。

3. 【强制】捕获异常是为了处理它，不要捕获了却什么都不处理而抛弃之，如果不想处理它，请 将该异常抛给它的调用者。最外层的业务使用者，必须处理异常，将其转化为用户可以理解的内容。

4. 【强制】有 `try` 块放到了事务代码中，`catch` 异常后，如果需要回滚事务，一定要注意手动回滚事务。

5. 【强制】不要在 finally 块中使用 `return`。

    <font color="#a38e46">说明:</font>  `finally` 块中的 `return` 返回后方法结束执行，不会再执行 `try` 块中的 `return` 语句。

6. 【强制】捕获异常与抛异常，必须是完全匹配，或者捕获异常是抛异常的父类。 

    <font color="#a38e46">说明:</font>  如果预期对方抛的是绣球，实际接到的是铅球，就会产生意外情况。

7. 【参考】避免出现重复的代码（Don’t Repeat Yourself），即 DRY 原则。

    <font color="#a38e46">说明:</font>  随意复制和粘贴代码，必然会导致代码的重复，在以后需要修改时，需要修改所有的副

    本，容易遗漏。必要时抽取共性方法，或者抽象公共类，甚至是组件化。

    <font color="green">正例:</font> 一个类中有多个 public 方法，都需要进行数行相同的参数校验操作，这个时候请抽取：

    `private checkParam() {...} `



## (二) SPL 标准异常

`SPL` 的 `Exception`，只有两个是直接继承自 `\Exception` 的。一个是 `RuntimeException`，一个是 `LogicException`。另外 11 个 `Exceptions` 都是又继承自它们。

1. `LogicException` **程序逻辑错误的异常**

    <font color="#a38e46">说明:</font>  这类 `Exception` 都是应该被直接修复掉的。比如说你调用一个作除法的函数，抛出一个除数为 0 的 `LogicException`，函数使用者就应该对代码除数先作检查，避免用户输入 0 的时候还去调用此函数。相对于 `RuntimeException` 而言，`LogicException` 更像是跟调用者说：你的调用方式不对，请检查您的代码！

2. `BadFunctionCallException` **函数调用错误**，典型用法是和 `is_callable()` 结合使用。

3. `BadMethodCallException`  继承于 `BadFunctionCallException` 调用方法错误。通常与调用魔法方法结合使用。

4. `DomianException` **如果值不符合定义的有效数据域，则抛出异常。**

    <font color="#a38e46">说明:</font>  官方文档一个很好的例子：说好了是处理图片的方法，其他类型的文件就请先过滤掉吧。Domain 是域的意思，这个例子即是在表达文件类型必须属于图片类型这个域的意思。

5. `InvalidArgumentException` **如果参数不是预期类型，则抛出异常。**

    <font color="#a38e46">说明:</font>  PHP 不是强类型语言，所以往往都使用 `InvalidArgumentException` 来作为非法参数类型的错误。

6. `LengthException` **如果长度不在期望范围之内，则抛出异常。**

7. `OutOfRangeException` **请求非法索引时抛出异常。**这表示应在编译时检测到的错误。

    <font color="#a38e46">说明:</font>  如果你也不知道某个数组有哪些索引,如数据库字段，此时请求了非法索引，则抛出异常。

    ```php
    <?php
    function prepareData(PDOStatement $s) {
        $x = $s->fetch();
        if (!isset($x['secretColumn']))
            throw new OutOfRangeException ("Secret column doesn't exist! Verify table definition and query.");
    }
    ```

8. `RuntimeException` **运行时发现的异常**

    <font color="#a38e46">说明:</font>  这种异常往往是用户造成，是代码调用者无法通过写更多逻辑代码来避免的。

    比如封装一个 ORM，在找不到数据的时候返回 `NotFoundException`（继承自`RuntimeException`），ORM 调用者也无法避免此意外的产生，只能根据`NotFoundException`来作出意外处理，比如再抛出 `Http404Exception` 什么的。

9. `OutOfBoundsException` **如果值不是有效键，则抛出异常。**

    <font color="#a38e46">说明:</font>  比如表单数据中缺少了参数，此时就可以使用。

    ```php
    <?php
    class HandleApplication 
    {
        public function __construct($_POST) 
        {
            if(!isset($_POST['secretCode']) {
                throw new OutOfBoundsException('Application hasn't sent secret code for authenticate');
            }  
    	}
    }
    ```

10. `OverflowException`  **溢出异常。**如果一个容器已经满了，调用者还往里塞东西，就抛出此异常。

    <font color="#a38e46">说明:</font>  容器什么时候满肯定是代码调用者自己无法预知的，所以此 `Exception` 属于 `RuntimeException`

11. `RangeException`  **抛出异常以指示程序执行期间的范围错误。**

    <font color="#a38e46">说明:</font>  `Runtime` 版本的 `DomainException` 通常这意味着有一个算术错误，而不是低于/溢出。

12. `UnderflowException` **在空容器上执行无效操作（例如删除元素）时抛出异常。**

13. `UnexpectedValueException` **如果变量不在某一组期待值里，抛出此异常。**

    <font color="#a38e46">说明:</font>  主要用于一个函数调用另外一个函数时返回值不是期待的类型或者值，也没有算法或者缓冲问题出现的时候。

# 四、MySQL 数据库 

## (一) 建表规约

1. 【推荐】表达是与否概念的字段，必须使用 `is_xxx` 的方式命名，数据类型是 `unsigned tinyint` (1 表示是，0 表示否)。

    <font color="#a38e46">说明:</font>  任何字段如果为非负数，必须是 `unsigned`。

    <font color="green">正例:</font>  表达逻辑删除的字段名 `is_deleted`，1 表示删除，0 表示未删除。

2. 【强制】表名、字段名必须使用小写字母或数字，禁止出现数字开头，禁止两个下划线中间只 出现数字。数据库字段名的修改代价很大，因为无法进行预发布，所以字段名称需要慎重考虑。 

    <font color="#a38e46">说明:</font> MySQL 在 Windows 下不区分大小写，但在 Linux 下默认是区分大小写。因此，数据库名、 表名、字段名，都不允许出现任何大写字母，避免节外生枝。 

    <font color="green">正例:</font>  `aliyun_admin，rdc_config，level3_name `

    <font color="#fe694b">反例:</font>  `AliyunAdmin，rdcConfig，level_3_name`

3. 【强制】表名不使用复数名词。 

    <font color="#a38e46">说明:</font>  表名应该仅仅表示表里面的实体内容，不应该表示实体数量。

4. 【强制】禁用保留字，如 `desc、range、match、delayed` 等，请参考 MySQL 官方保留字。

5. 【强制】主键索引名为` pk_字段名`;唯一索引名为 `uk_字段名`;普通索引名则为` idx_字段名`。

    <font color="#a38e46">说明:</font>  `pk_` 即 primary key;`uk_ `即 unique key;`idx_ `即 index 的简称。

6. 【强制】小数类型为 `decimal`，禁止使用 `float` 和 `double`。

    <font color="#a38e46">说明:</font>  `float` 和 `double` 在存储的时候，存在精度损失的问题，很可能在值的比较时，得到不正确的结果。如果存储的数据范围超过 `decimal` 的范围，建议将数据拆成整数和小数分开存储。

7. 【强制】如果存储的字符串长度几乎相等，使用 `char` 定长字符串类型。

8. 【强制】`varchar` 是可变长字符串，长度不要超过 5000，如果存储长度大于此值，定义字段类型为 `text`，独立出来一张表，用主键来对应，避免影响其它字段索 引效率。

9. 【强制】表必备三字段:`id, created_at, updated_at`。 

    <font color="#a38e46">说明:</font>  其中`id`必为主键，类型为`bigint unsigned`、单表时自增、步长为1。`created_at, updated_at` 的类型均为 `datetime` 类型，前者现在时表示主动创建，后者过去分词表示被 动更新。

10. 【推荐】表的命名最好是加上“业务名称_表的作用”。

    <font color="green">正例:</font> ` alipay_task / force_project / trade_config`

11. 【推荐】库名与应用名称尽量一致。

12. 【推荐】如果修改字段含义或对字段表示的状态追加时，需要及时更新字段注释。

13. 【推荐】字段允许适当冗余，以提高查询性能，但必须考虑数据一致。冗余字段应遵循: 

    1)不是频繁修改的字段。

    2)不是 `varchar` 超长字段，更不能是 `text` 字段。

    <font color="green">正例: </font> 商品类目名称使用频率高，字段长度短，名称基本一成不变，可在相关联的表中冗余存 储类目名称，避免关联查询。

14. 【推荐】单表行数超过 500 万行或者单表容量超过 2GB，才推荐进行分库分表。

    <font color="#a38e46">说明:</font>  如果预计三年后的数据量根本达不到这个级别，请不要在创建表时就分库分表。

15. 【参考】合适的字符存储长度，不但节约数据库表空间、节约索引存储，更重要的是提升检 索速度。

    <font color="green">正例: </font> 如下表，其中无符号值可以避免误存负数，且扩大了表示范围。

    |   对象   |  年龄区间  |        类型         | 字节 |           表示范围            |
    | :------: | :--------: | :-----------------: | :--: | :---------------------------: |
    |    人    | 150岁之内  | `tinyint unsigned`  |  1   |       无符号值:0 到 255       |
    |    龟    |   数百岁   | `smallint unsigned` |  2   |      无符号值:0 到 65535      |
    | 恐龙化石 |  数千万年  |   `int unsigned`    |  4   |    无符号值:0 到约 42.9 亿    |
    |   太阳   | 约 50 亿年 |  `bigint unsigned`  |  8   | 无符号值:0 到约 10 的 19 次方 |



## (二) 索引规约

1. 【强制】业务上具有唯一特性的字段，即使是多个字段的组合，也必须建成唯一索引。 

    <font color="#a38e46">说明:</font>  不要以为唯一索引影响了 `insert` 速度，这个速度损耗可以忽略，但提高查找速度是明 显的;另外，即使在应用层做了非常完善的校验控制，只要没有唯一索引，根据墨菲定律，必然有脏数据产生。

2. 【强制】超过三个表禁止 `join`。需要 `join` 的字段，数据类型必须绝对一致;多表关联查询时， 保证被关联的字段需要有索引。

    <font color="#a38e46">说明:</font>  即使双表 `join` 也要注意表索引、SQL 性能。

3. 【强制】在 `varchar` 字段上建立索引时，必须指定索引长度，没必要对全字段建立索引，根据实际文本区分度决定索引长度即可。

    <font color="#a38e46">说明:</font>  索引的长度与区分度是一对矛盾体，一般对字符串类型数据，长度为 20 的索引，区分度会高达 90%以上，可以使用 `count(distinct left(列名, 索引长度))/count(*)`的区分度 来确定。

    > 索引长度限制
    >
    > 1. MySQL对索引字段长度有限制
    >
    >     innodb引擎的每个索引列长度限制为767字节（bytes），所有组成索引列的长度和不能大于3072字节
    >
    >     myisam引擎的每个索引列长度限制为1000字节，所有组成索引列的长度和不能大于1000字节
    >
    > 2. varchar的最大长度是指字符长度，若数据库字符集为utf-8，则一个字符占3个bytes。因此在utf-8字符集下，innodb引擎创建的单列索引长度不能超过255个字符
    >
    > 索引长度计算
    >
    > **1.所有的索引字段，如果没有设置not null，则需要加一个字节。**
    >
    > **2.定长字段，int占四个字节、date占三个字节、char(n)占n个字符。**
    >
    > **3.对于变成字段varchar(n)，则有n个字符+两个字节。**
    >
    > **4.不同的字符集，一个字符占用的字节数不同。latin1编码的，一个字符占用一个字节，gbk编码的，一个字符占用两个字节，utf8编码的，一个字符占用三个字节。**
    >
    > **5.索引长度 char()、varchar()索引长度的计算公式：**
    >
    > (Character Set：utf8mb4=4,utf8=3,gbk=2,latin1=1) * 列长度 + 1(允许null) + 2(变长列)

4. 【强制】页面搜索严禁左模糊或者全模糊，如果需要请走搜索引擎来解决。 

    <font color="#a38e46">说明:</font>  索引文件具有 B-Tree 的最左前缀匹配特性，如果左边的值未确定，那么无法使用此索引。

5. 【推荐】如果有 order by 的场景，请注意利用索引的有序性。`order by` 最后的字段是组合 索引的一部分，并且放在索引组合顺序的最后，避免出现` file_sort` 的情况，影响查询性能。 

    <font color="green">正例:</font> `where a=? and b=? order by c; `索引:`a_b_c`

    <font color="#fe694b">反例:</font>  索引中有范围查找，那么索引有序性无法利用，如:`WHERE a>10 ORDER BY b; `索引` a_b `无法排序。

6. 【推荐】利用覆盖索引来进行查询操作，避免回表。

    <font color="#a38e46">说明:</font>  如果一本书需要知道第 11 章是什么标题，会翻开第 11 章对应的那一页吗?目录浏览 一下就好，这个目录就是起到覆盖索引的作用。 正例:能够建立索引的种类分为主键索引、唯一索引、普通索引三种，而覆盖索引只是一种查 询的一种效果，用`explain`的结果，`extra`列会出现:`using index`。

7. 【推荐】利用延迟关联或者子查询优化超多分页场景。

    <font color="#a38e46">说明:</font>  `MySQL` 并不是跳过 `offset` 行，而是取 `offset+N` 行，然后返回放弃前 `offset` 行，返回 `N` 行，那当` offset`特别大的时候，效率就非常的低下，要么控制返回的总页数，要么对超过 特定阈值的页数进行 SQL 改写。

    <font color="green">正例:</font> 先快速定位需要获取的 id 段，然后再关联:

    `SELECT a.* FROM 表 1 a, (select id from 表 1 where 条件 LIMIT 100000,20 ) b where a.id=b.id`

8. 【推荐】`SQL` 性能优化的目标:至少要达到 `range` 级别，要求是 `ref` 级别，如果可以是 `consts` 最好。

    <font color="#a38e46">说明:</font>  

    1)`consts` 单表中最多只有一个匹配行(主键或者唯一索引)，在优化阶段即可读取到数据。 
      2)`ref` 指的是使用普通的索引(`normal index`)。
      3)`range `对索引进行范围检索。

    <font color="#fe694b">反例:</font> `explain` 表的结果，`type=index`，索引物理文件全扫描，速度非常慢，这个` index` 级 别比较 `range` 还低，与全表扫描是小巫见大巫。

9. 【推荐】建组合索引的时候，区分度最高的在最左边。

    <font color="green">正例:</font>  如果` where a=? and b=? `，如果 `a` 列的几乎接近于唯一值，那么只需要单建 `idx_a `索引即可。 

    <font color="#a38e46">说明:</font>  存在非等号和等号混合时，在建索引时，请把等号条件的列前置。如:`where c>? and d=? `那么即使 `c` 的区分度更高，也必须把` d` 放在索引的最前列，即索引 `idx_d_c`。

10. 【推荐】防止因字段类型不同造成的隐式转换，导致索引失效。

11. 【参考】创建索引时避免有如下极端误解: 

    1)宁滥勿缺。认为一个查询就需要建一个索引。 

    2)宁缺勿滥。认为索引会消耗空间、严重拖慢更新和新增速度。 

    3)抵制惟一索引。认为业务的惟一性一律需要在应用层通过“先查后插”方式解决。



## (三) SQL 语句

1. 【强制】数据订正(特别是删除、修改记录操作)时，要先 select，避免出现误删除，确认无误才能执行更新语句。
2. 【推荐】`in` 操作能避免则避免，若实在避免不了，需要仔细评估 `in` 后边的集合元素数量，控制在 1000 个之内。

## (四) ORM 映射

1. 【强制】在表查询中，一律不要使用 `*` 作为查询的字段列表，需要哪些字段必须明确写明。 

    <font color="#a38e46">说明:</font>  

    ​	1)增加查询分析器解析成本。

    ​	2)增减字段容易与 `resultMap` 配置不一致。

    ​	3)无用字 段增加网络消耗，尤其是 `text` 类型的字段。



# 五、工程结构

## (一) 版本号

版本号命名方式:主版本号.次版本号.修订号

1) 主版本号:产品方向改变，或者大规模API不兼容，或者架构不兼容升级。

2) 次版本号:保持相对兼容性，增加主要功能特性，影响范围极小的 API 不兼容修改。 

3) 修订号:保持完全兼容性，修复BUG、新增次要功能特性等。

<font color="#a38e46">说明:</font> 注意起始版本号必须为:`1.0.0`，而不是` 0.0.1` 正式发布的类库必须先去仓库进行查证，使版本号有延续性，正式版本号不允许覆盖升级。如当前版本:`1.3.3`，那么下一个 合理的版本号:`1.3.4` 或` 1.4.0 `或` 2.0.0`



# 附录1：版本历史

| 版本号 | 更新日期  |                 备注                  |
| :----: | :-------: | :-----------------------------------: |
| 1.0.0  | 2020.1.15 |                 初版                  |
| 1.1.0  | 2020.1.16 | 1）增加 SPL 标准异常。2）文本修正样式 |
| 1.2.0  | 2020.1.17 |         增加 RESTful 设计规范         |
