php代码书写规范
=========

----------

### 1、PHP 源文件只能使用 &lt;?php 和 &lt;?= 这两种标签 ###
> &lt;?php 标签通常用于纯 PHP 的脚本当中，而 &lt;?= 通常用于模板当中。

### 2、PHP 源文件必须是不带 BOM 的 UTF-8 编码的文件 ###

> BOM（Byte Order Mark)，字节顺序标记，出现在文本文件头部，Unicode 编码标准中用于标识文件是采用哪种格式的编码。

### 3、PHP 源文件缩进采用 4 个空格 ###
> 很多编辑器使用 Tab 作为缩进。会造成空格性问题。

### 4、纯 PHP 代码的源文件关闭标签 ?> 必须省略 ###

PHP 解析器在对文件进行解释的时候，会有性能提升。并且，这能一定程序避免在 ?之后有多余的空格导致程序报错。

### 5、请严格控制每行 120 个字符 ###

> 过长的代码会导致多种分辨率的显示器造成兼容问题。并且，过长的代码也会造成难以阅读理解。如果实在太长，请把代码换行。

### 6、所有的类必须设定一个命令空间 ###

> 命令空间给代码结构有较强的说明性，以及杜绝同名类的冲突问题。同时，也能用到 Composer 的自动加载优势特性。

    <?php
    namespace core;
    ​

### 7、命名空间(namespace)的声明后面必须有一行空行 ###

> 空行会让代码看起来更加清晰容易阅读。

    <?php
    namespace core;
    
    use common;

### 8、所有的导入(use)声明必须放在命名空间(namespace)声明的下面 ###

> 这样会让代码结构变得清晰容易阅读。

    <?php
    namespace core;
    
    use common;
    
### 9、一句声明中，必须只有一个导入(use)关键字 ###

> 虽然 PHP 允许一行代码当中允许使用多个 use 关键字导入一个类。但是，这会使代码阅读造成障碍。

错误：

    <?php
    namespace core;
    
    use common, library;
    
正确：

    <?php
    namespace core;
    
    use common;
    use library;
    
### 10、在导入(use)声明代码块后面必须有一行空行 ###

> 空行让代码结构变得容易理解。

    <?php
    namespace core;
    
    use common;
    use library;
    
    class Person {
    
    }
    
### 11、PHP 关键字必须小写 ###

> PHP 的关键字，必须小写，boolean 值：true，false，null 也必须小写。下面的关键字，也必须小写：
> 
> '__halt_compiler', 'abstract', 'and', 'array', 'as', 'break', 'callable', 'case', 'catch', 'class', 'clone', 'const', 'continue', 'declare', 'default', 'die', 'do', 'echo', 'else', 'elseif', 'empty', 'enddeclare', 'endfor', 'endforeach', 'endif', 'endswitch', 'endwhile', 'eval', 'exit', 'extends', 'final', 'for', 'foreach', 'function', 'global', 'goto', 'if', 'implements', 'include', 'include_once', 'instanceof', 'insteadof', 'interface', 'isset', 'list', 'namespace', 'new', 'or', 'print', 'private', 'protected', 'public', 'require', 'require_once', 'return', 'static', 'switch', 'throw', 'trait', 'try', 'unset', 'use', 'var', 'while', 'xor'


### 12、继承(extends) 和实现(implement) 必须和 class name 写在一行，切花括号要换行写。 ###
    <?php
    namespace Lib\Databaes;
     
    class Mysql extends ParentClass implements \PDO, \DB // 写一行
    { // 换行写{
     
    }

### 13、成员属性访问修饰符必须显示声明不能省略 ###

> 成员属性有三种访问修饰符：public、protected、private。不能使用老式的 var 来声音成员属性。

    <?php
    namespace Lib\Databaes;
     
    class Mysql extends ParentClass implements \PDO, \DB // 写一行
    {
	    public$foo  = null;
	    private   $name = 'sam';
	    protected $age  = '17';
    }

### 14、成员方法访问修饰符必须显示声明不能省略 ###

> 成员方法有三种访问修饰符：public、protected、private。

错误：

    <?php
    namespace Lib\Databases;
    
    class MySQL
    {
        function fetchOne()
        {
            // ......
        }
    }
    
正确：

    <?php
    namespace Lib\Databases;
    
    class MySQL
    {
        public function fetchOne()
        {
            // ......
        }
    }
    
### 15、方法的参数有多个的时候，每个参数的逗号后面必须加个空格 ###
    namespace Lib\Databaes;
     
    class Mysql extends ParentClass implements \PDO, \DB // 写一行
    {
        public getInfo ($name, $age, $gender = 1)
        {
        }
    }
    
### 16、当用到抽象(abstract)和终结(final)来做类声明时，它们必须放在可见性声明(public 还是protected还是private)的前面。而当用到静态(static)来做类声明时，则必须放在可见性声明的后面。 ###
    <?php
    namespace Vendor\Package;
     
    abstract class ClassName
    {
        protected static $foo; // static 放后面
     
	    abstract protected function zim(); // abstract 放前面
     
	    final public static function bar() // final 放前面，static 放最后。
        {
            // 方法主体部分
        }
    }

### 17、控制结构花括号、换行、空格等规范 ###
> if、else、elseif、switch、for、foreach、case、while、go、try、catch 等关键词后面必须加空格。可以说，没有特殊说明的情况下，基本上所有的 PHP 关键词后面都必须加空格。
> 
> 流程控制语句起始的花括号是不需要另起一行。

    if ($expr1) { // 左右空格
        // if body
    } elseif ($expr2) { // elesif 连着写
        // elseif body
    } else {
        // else body;
    }
    
    switch ($expr) { // 左右空格
    case 0:
        echo 'First case, with a break'; // 对齐
        break; // 换行写break，也对齐。
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
    }
    
    while ($expr) { // 左右空格
        // structure body
    }
     
    do {
        // structure body; // 左右空格
    } while ($expr);
    
    for ($i = 0; $i < 10; $i++) { // 注意几个参数之间的空格
        // for body
    }
    
    foreach ($iterable as $key => $value) { // 还是空格问题
        // foreach body
    }
    
    try {
        // try body
    } catch (FirstExceptionType $e) { // 同样也是注意空格。
        // catch body
    } catch (OtherExceptionType $e) {
        // catch body
    }

### 18、类名必须与文件名一样 ###

> 这个很容易理解，没啥好补充说明的。除非框架有特殊的加载规则。

### 19、类的命名必须遵循 StudlyCaps 大写开头的驼峰命名规范 ###
### StudlyCaps 即单词首字母大写风格。有些人也称它为大驼峰。 ###

### 20、方法名称必须符合 camelCase 式的小写开头驼峰命名规范 ###

> camelCase 即第一个单词首字母小写后面的单词首字母大写的风格。

### 21、类中的常量所有字母都必须大写，单词间用下划线分隔 ###

> CONST ORDER_STATUS = 1;

### 22、变量必须使用小驼峰命名风格 ###
> $cardNo   = ''; // 卡号。 
> $idCardNo = ''; // 身份证号。

### 23、参数必须使用驼峰命名风格 ###

> 参数也是变量的一种。故与变量的命名风格一致。

### 24、所有方法的起始花括号必须另起一行。 ###

> 虽然以下两种在实际开发中都是允许的。但是，为了保持代码一致。所以，必须强制使用。

错误：

    <?php
    
    class MySQL
    {
        public function fetchOne() {
    
        }
    }
    
正确：

    <?php
    
    class MySQL
    {
        public function fetchOne() 
        {
	    
        }
    }
    
### 25、直接在方法中写数组参数时格式如下 ###
    $object->callFunc([
        'userId'   => 1,
        'username' => 'sam',
        'age'  => 20,
        'sex'  => 'male'
    ]);

### 26、方法参数注释 ###
    /**
     * 管理后台获取优惠券发送记录。
     *
     * @author 7031 2018-02-23
     * @modify 7031 2019-02-25 修复了 SQL 性能问题。
     *
     * @param int$couponId  优惠券ID。
     * @param string $username  用户名。
     * @param string $mobilephone   用户手机号。
     * @param int$page  当前分页页码。
     * @param int$count 每页显示条数。
     * @param array  $data  请求参数。
     *
     * ------------------- eg:start ---------------------
     * $data = [
     *	 'username' => '用户账号,没有时传空字符串',
     *	 'age'  => '用户年龄,没有时传0',
     * ];
     * ------------------- eg:end -----------------------
     *
     * @return array
     */
    public static function getBackendSendHistory($couponId = -1, $username, $mobilephone, $page, $count, $data) {
    
    }
    
