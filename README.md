# Simplified_C_Complier
# SC 语言定义
## 1. 字符集
### 1.1 字母

a b c d e f g h i j k l m

n o p q r s t u v w x y z

A B C D E F G H I J K L M

N O P Q R S T U V W X Y Z

_
### 1.2 数字
0 1 2 3 4 5 6 7 8 9
### 1.3 标点和特殊字符
\+ \- \* / % = ! < > . & ( ) [ ] { } ; , \\ " '

## 2. 单词
SC语言的单词可以分为：关键字、标识符、整数常量、字符常量、字符串常量、运算符、分隔符、注释。

### 2.1 关键字
<char 关键字>::="char"

<short 关键字>::="short"

<int 关键字>::="int"

<void 关键字>::="void"

<struct 关键字>::="struct"

<if 关键字>::="if"

<else 关键字>::="else"

<for 关键字>::="for"

<continue 关键字>::="continue"

<break 关键字>::="break"

<return 关键字>::="return"

<sizeof 关键字>::="sizeof"

<__cdecl 关键字>::="__cdecl"

<__stdcall 关键字>::="__stdcall"

<__align 关键字>::="__align"

### 2.2 标识符
<标识符>::=<非数字>{<数字>|<非数字>}

<非数字>::="_" | "a" | "b" | "c" | "d" | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n"

$~~~~~~~~~~~~~~~~~~~~~~~$| "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x" | "y" | "z"

$~~~~~~~~~~~~~~~~~~~~~~~$| "A" | "B" | "C" | "D" | "E" | "F" | "G" | "H" | "I" | "J" | "K" | "L" | "M" | "N"

$~~~~~~~~~~~~~~~~~~~~~~~$| "O" | "P" | "Q" | "R" | "S" | "T" | "U" | "V" | "W" | "X" | "Y" | "Z"

### 2.3 整数常量
<整数常量>::=<数字>{<数字>}

<数字>：：= "0" | "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

### 2.4 字符常量
<字符常量>::='<C-字符>'

<C-字符>::=<转义序列> | 原字符集中除单引号'、反斜线字符\\ 之外的任意字符

<转义序列>::="\'" | "\\"" | "\\\\" | "\\a" | "\\b" | "\\f" | "\\n" | "\\r" | "\\t" | "\\v"

### 2.5 字符串常量
<字符串常量>::="{<串字符>}"

<串字符>::=<转义字符> | 原字符集中除单引号'、反斜线字符\\ 之外的任意字符

### 2.6 运算符
<加号>::="+"

<减号>::="-"

<星号>::="*"

<除号>::="/"

<取余号>::="%"

<等于号>::="=="

<不等于号>::="!="

<小于号>::="<"

<小于等于号>::="<="

<大于号>::=">"

<大于等于号>::=">="

<赋值等号>::="="

<箭头>::="->"

<点>::="."

<与>::="&"

<左小括号>::="("

<右小括号>::=")"

<左中括号>::="["

<右中括号>::="]"

<左大括号>::="{"

<右大括号>::="}"

<分号>::=";"

<逗号>::=","

<省略号>::="..."

## 3. 语法定义
### 3.1 外部定义
<翻译单元>::={<外部声明>}<文件结束符>

<外部声明>::=<函数定义>|<声明>

**函数定义**

<函数定义>::=<类型区分符><声明符><函数体>

<函数体>::=<复合语句>

**声明**

<声明>::=<类型区分符>[<初值声明符表>]<分号>

<初值声明符表>::=<初值声明符>{<逗号><初值声明符>}

<初值声明符>::=<声明符>|<声明符><赋值运算符><初值符>

**类型区分符**

<类型区分符>::=<void 关键字>|<char 关键字>|<short 关键字>|

$~~~~~~~~~~~~~~~~~~~~~~~~~$<int 关键字>|<结构区分符>

<结构区分符>::=<struct 关键字><标识符><左大括号><结构声明表><右大括号>|

$~~~~~~~~~~~~~~~~~~~~~~~~~$<struct 关键字><标识符>

<结构声明表>::=<结构声明>{<结构声明>}

<结构声明>::=<类型区分符>{<结构声明符表>}<分号>

<结构声明符表>::=<声明符>{<逗号><声明符>}

**声明符**

<声明符>::={<指针>}[<调用约定>][<结构成员对齐>]<直接声明符>

<调用约定>::=<__cdecl 关键字>|<__stdcall 关键字>

<结构成员对齐>::=<__align 关键字><左小括号><整数常量><右小括号>

<指针>::=<星号>

<直接声明符>::=<标识符><直接声明符后缀>

<直接声明符后缀>::={<左中括号><右中括号>

$~~~~~~~~~~~~~~~~~~~~~~~~~~~~$|<左中括号><整数常量><右中括号>

$~~~~~~~~~~~~~~~~~~~~~~~~~~~~$|<左小括号><右小括号>

$~~~~~~~~~~~~~~~~~~~~~~~~~~~~$|<左小括号><形参表><右小括号>}

<参数声明>::=<类型区分符><声明符>

**初值符**

<初值符>::=<赋值表达式>