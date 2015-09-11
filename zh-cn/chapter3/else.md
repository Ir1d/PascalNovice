#else

现在我们来学习else语句～

在上一节的两个程序当中，都有着一个共同的特点：

前一个if的条件表达式不成立，则后面的必然成立。（至少有一个成立）而else可以使我们避免这种重复的情况。

if~else的格式如下：

```
if <布尔表达式> then <语句1> else <语句2>;
```

它的意义为：如果布尔表达式成立，则执行语句1，否则执行语句2。

语句1和/或语句2也可以像上一小节那样替换成begin~end类型的多条语句。

例如，第一个程序可以这样改写：

```delphi
//程序3_2_1_abs_new
var a :longint;
begin
	read(a);
	if a >= 0 then writeln(a) else writeln(-a);
	//中间没有多余的分号
	readln;
end.
```

语句1和语句2中也可以包含if~else~语句，所以以下格式是常用的。不看后面的解释，试着自己理解它的意思。

```delphi
if <布尔表达式1>then <语句1>
else if <布尔表达式2> then <语句2>
else if <布尔表达式3> then <语句3>
...
else <语句n>;
```

它的意义是：如果布尔表达式1成立则只执行语句1，否则再判断布尔表达式2是否成立，如果成立则只执行语句2……如果都不成立，则执行语句n。

例如，第二个程序可以这样改写：

```delphi
//程序3_2_2_grade_new
var a :longint;
begin
	read(a);
	if a >= 90 then writeln('A')
	else if a >= 75then writeln('B')
	else if a >= 60 then writeln('C')
	else writeln('D');
	readln;
end.
```

现在你已经学会使用Pascal来实现一些简单的小程序啦

希望你能严谨地Coding～养成良好的代码风格

所谓良好呢？就是你自己看着舒服咯（缩进、对齐、空格之类的）
-------

gl & hf;

开始新的OI征程吧～

