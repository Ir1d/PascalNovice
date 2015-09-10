# 初识FreePascal

本节内容分两部分，我们先从Windows下更方便的窗口操作说起。

[Free Pascal](http://www.freepascal.org/)有很多版本，目前，在Windows平台下，广泛使用的稳定版本是2.4.0版。它与最新版本相比的最大优点是Debug功能强大。（其实更主要的是先行`NOI Linux`中的fpc版本不是最新的版本）

安装完毕后，删除安装文件夹（默认为`C:\FPC\2.4.0\bin\i386-win32\`）中的`fp.cfg`，即可正常使用。

如果你看到`Free Pascal`中有一堆“屯”字，在cmd上边点右键把默认代码页改成`437--美国`就好啦。

通常，我们将程序源代码（`*.pas`文件）拖到`Free Pascal IDE`的图标当中，即可用`Free Pascal`打开它。至于源代码的编辑工作，建议在专用的文本编辑器中完成。（比如我们之前推荐的Vim或者Sublime、Notepad++之类的）

例如，将以下这一段程序保存到一个`.pas`文件当中，并拖入`Free Pascal`，以此为例介绍`Free Pascal`的基本操作。

```Delphi
//程序2_1_1_forever_hello
begin
	while true do write('Hello ');
end.
```

编译（快捷键F9）：生成程序所对应的可执行文件（*.exe），如成功，会提示与以下类似的信息：

```bash
Main file: C:\..\desktop\xxx.pas
Done.
Target: Win32 for i386
Line number:      3     Total lines:           2
Used memory:    412K    Allocated memory:   2112K
Total errors:     0     Compile time:        0.1s

        Compile successful: Press any key
```

否则提示相关错误信息。

运行（快捷键Ctrl+F9）：先编译程序，然后运行之。可以用上述程序试验运行结果。可以看到，屏幕上不断地闪着Hello这一单词。

Ctrl+C可以用来结束死循环的程序。

可以通过Alt+F5来看程序上一次运行的结果。

保存（快捷键F2）：保存对代码所做的修改。（如果不主动保存，并且中途没有编译操作，则一切修改都会丢失）

好的我们现在开始研究Linux下面更方便的命令行方法。

比如Ubuntu吧～

打开Terminal输入下面这段代码

```bash
sudo apt-get install fpc
```

如果出现异常系统将提示相应的信息。

然后我们就安装成功啦～

比如现在我们有之前写好的一个文件是`a.pas`

我只需要在终端里进入`a.pas`所在的目录然后运行：

```bash
fpc a.pas
```
如果你想要知道更多的编译选项可以试试这个：

```bash
fpc --help
```

要知道，Windows下面的那个`Free Pascal`实际上也是在调用现在这个fpc

不信你在Terminal里面输入fpc

是不是界面都一模一样阿？

-------

gl & hf;

开始新的OI征程吧～

