#for

现在我们来学习for语句～

为了计算1+2+3+…+100的值，我们能够写出以下程序：

```delphi
//程序3_3_1_plus_old
var sum :longint;
begin
	sum := 0;
	sum := sum + 1;
	sum := sum + 2;
	//省略97行
	sum := sum + 100;
	writeln(sum);
end.
```

但是这样实在是太麻烦了，我们需要一个能够批量处理数据的语句：

```
for <整数变量名> := <表达式1> to <表达式2> do <语句>;
```

它的意义是，先计算出表达式1和表达式2的值，然后进行一次赋值（即`<变量名> := <表达式1>`）

如果此时变量的值不超过表达式2，则执行语句，然后将变量的值增加1，继续判断是否不超过表达式2，如果不超过则再次执行语句，如此反复，直到表达式1与表达式2相等为止。

**如果表达式1与表达式2是相等的，则语句只会执行1次；如果表达式1大于表达式2，则语句不会执行。（这句话是重点）**

**整数变量可以在语句中被调用，但不能被赋值。（同样是重点）**

例如，上述程序可以这样改写：

```delphi
//程序3_3_2_plus_new
var i, sum :longint;
begin
	sum := 0;
	for i := 1 to 100 do sum := sum + i;
	writeln(sum);
end.
```

它相当于：

```
//程序3_3_3_plus_foo
var i, sum :longint;
begin
	sum := 0;
	i := 1;
	sum := sum + i;
	i := 2;
	sum := sum + i;
	i := 3;
	sum := sum + i;
	...
	i := 100;
	sum := sum + i;
	writeln(sum);
end.
```

既然有逐步增加，也会有逐步减少，它的格式如下：

```
for <整数变量名> := <表达式1> downto <表达式2> do <语句>;
```

就是把to变成downto咯～

例如，上述程序也可以改写为：

```delphi
//程序3_3_4_plus_new_new
var i, sum :longint;
begin
	sum := 0;
	for i := 100 downto 1 do sum := sum + i;
	writeln(sum);
end.
```

for中的表达式不一定是常数。不看解释，试着指出以下程序的功能：

```delphi
//程序3_3_5_plus_new_new_new
var n, i, sum :longint;
begin
	read(n);
	sum := 0;
	for i := 1 to n do sum := sum + i;
	writeln(sum);
end.
```

实际上，这是在计算1+2+3+…+n的值。

for中的语句也可以是for语句。例如计算1+1+2+1+2+3+1+2+3+4+…+1+2+3+…+n：

```delphi
//程序3_3_6_plus_super
var n, i, sum :longint;
begin
	read(n);
	sum := 0;
	for i := 1 to n do for j := 1 to i do sum := sum + j;
	writeln(sum);
end.
```

例如，从小到大输出所有的仅由1，2，3，4构成的三位数：

//程序1_2_3_7_triple
var a, b, c :longint;
begin
	for a := 1 to 4 do
		for b := 1 to 4 do
			for c := 1 to 4 do
				writeln(a * 100 + b * 10 + c);
end.

利用for循环，我们就可以做很多事情了。例如：输入n和n个数，找出其中的最小值：

```delphi
//程序3_3_8_min
var n, i, a, min :longint;
begin
	read(n);
	min := maxlongint; //默认最小值为无穷大
	for i := 1 to n do begin
		read(a); //读取当前的这个数
		if a < min then min := a;
		//如果它比当前最小值还小则改变最小值
	end;
	writeln(min);
end.
```

既然我们已经能够找到最小值了，那么如果我们每次都找一个最小值，便可实现对于数据的排序。

这一点我们将在第6章中继续探讨。

再如：输入n（至少为2），判断n是否为质数。

```delphi
//程序3_3_9_prime
var n, i :longint;
var isPrime :boolean;
begin
	read(n);
	isPrime := true; //默认它是质数
	for i := 2 to n – 1 do //从2到n-1依次试除
		if n mod i = 0 then //如果n能被i整除
			isPrime := false; //说明n不是质数
	if isPrime then writeln('YES') else writeln('NO');
end.
```

-------

gl & hf;

开始新的OI征程吧～

