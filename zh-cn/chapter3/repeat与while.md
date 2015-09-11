#break，continue，repeat与while

我们现在来学习另外4个重要且实用的语句～

考虑这样一个题目：输入sum，求满足1+2+3+…+n>sum的最小的n。

根据之前学过的知识，我们可以从小到大枚举n，依次试验，直到1+2+3+…+n>sum为止。

但我们在此之前并不知道n的值，也就不知道在什么时候停止。

只利用之前的知识，做起来会很麻烦（并非不可做）。

关键问题在于，如何立刻跳出循环。

好在Pascal有一个命令：

```
break;
```

它的意义是，直接跳出当前一层循环。（如果有多层则跳出最内层）

例如以下程序：

```delphi
//程序3_4_1_break
var i :longint;
begin
	for i := 1 to 1234567 do begin
		writeln(i);
		if i > 3 then break;
	end;
end.
```

它会依次输出1，2，3，4，然后结束程序。

这样，我们就可以解决之前的问题了：

```delphi
//程序3_4_2_sum_advanced
var sum, i, s :longint;
begin
	read(sum);
	s := 0;
	for i := 1 to maxlongint do begin
		s := s + i;
		if s > sum then begin
			writeln(i);
			break;
		end;
	end;
end.
```

与break相关的一个命令是continue，它的意义是立刻跳转到当前层循环的尾部（end之前）

与break的区别是：一个循环计划要做1000次，做到第233次的时候看见了break，计算机立刻停下手中的循环任务，剩下的767次也不做了直接跳过。

如果看见了continue，计算机只会忽略本次循环中没有完成的语句，相当于第233次循环只做了一半，剩下的999次循环没有特殊要求的话都是正常完成的

例如：

```delphi
//程序3_4_3_continue
var i, j :longint;
begin
	for i := 1 to maxlongint do begin
		continue; // go to B
		for j := 1 to maxlongint do begin
			continue; //go to A
			do_something;
			//here is A point
		end;
		//here is B point
	end;
end.
```

通过以上的操作已经能够解决问题了，但是那个maxlongint毕竟是不够优美，况且有些时候我们循环到了maxlongint都有可能没有退出循环。好在Pascal给我们提供了一个叫做`repeat...until`的命令：

```
repeat <语句> until <布尔表达式>;
```

它的意义是：先执行语句，然后判断表达式是否成立，如果成立则跳出，否则再次执行语句，直到表达式成立为止。简单来说，就是反复执行语句，直到表达式成立为止。

有一点需要特殊注意的是，如果语句有多条，不必加`begin...end`。（不同于if和for）

用`repeat...until`语句完成上面的题目：

```delphi
//程序3_4_4_sum_repeat
var sum, i, s :longint;
begin
	read(sum);
	s := 0; i := 0;
	repeat
		i := i + 1;
		s := s + i;
	until s > sum;
	writeln(i);
end.
```

与它相关的另一个命令是while~do~命令，它的格式如下：

```
while <布尔表达式> do <语句>;
```

它的意义是：先判断表达式是否成立，如果不成立则直接跳出，否则执行语句然后再次判断是否成立，直到不成立为止。简单来说，就是“只要表达式成立，就无限执行语句”。

如果语句包含多条，需要用`begin...end`包括起来。

用`while...do`语句完成上面的题目：

```delphi
//程序3_4_4_sum_while
var sum, i, s :longint;
begin
	read(sum);
	s := 0; i := 0;
	while s <= sum do begin
		i := i + 1;
		s := s + i;
	end;
	writeln(i);
end.
```

用上述两种语句也可以实现无限循环的功能，格式如下：

```
while true do <语句>;
repeat <语句> until false;
```

这样的循环就只能使用break来跳出了。

当然continue也可以在这两种语句中使用。

-------

gl & hf;

开始新的OI征程吧～

