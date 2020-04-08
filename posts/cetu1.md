### Cheat Engine 自带入门教程

#### [Cheat Engine 下载地址](https://www.cheatengine.org/downloads.php)

##### 本教程的 Cheat Engine 已官方汉化，汉化教程请自行百度

#### 1. 说明

直接下一步就好了啦。



#### 2. 精确查找

![image-20200407133107229](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407133107229.png)

点击左上角放大镜图标，在跳出窗口中选择 Tutorial (认准图标)

![image-20200407133157043](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407133157043.png)

在 Cheat Engine 里的左侧输入框输入健康值（刚打开时为 100），点击首次扫描。

![image-20200407133454144](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407133454144.png)

点击 打我 按钮，健康值变为一个随机数，例如 97。

![image-20200407133522327](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407133522327.png)

再次在 Cheat Engine 里输入刚才的健康值，点击 再次扫描。

重复以上步骤，直到左侧地址框中只剩一个目标，右键点击目标，选择 改变已选择地址的数值。

输入 1000，点击 OK ，下一步 会变成可点击的，点击进入下一步。



#### 3. 未知的初始值

点击 新的扫描。因为初始值在 0 至 500 之间，查找时不能使用精确数值，选择 值介于…两者之间，输入 0 和 500 ，点击 首次扫描。

![image-20200407134445269](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407134445269.png)

点击 打我，出现减少的数值，在 扫描类型 里选择 数值减少了 ，输入减少的数值，点击 再次扫描。

![image-20200407134625502](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407134625502.png)

重复以上步骤，直到左侧地址框中只剩一个目标，右键点击目标，选择 改变已选择地址的数值。

输入5000， 点击 OK ，下一步 按钮会变成可点击的，点击进入下一步。

![image-20200407134855898](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407134855898.png)



#### 4. 浮点数

数据类型选择 单浮点（健康）或双浮点（弹药） ，数值 输入 100 ，点击 首次扫描。

扫描步骤类似第一步，这里不再阐述，把数值换为 5000。

![image-20200407135613558](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407135613558.png)

下一步 按钮会变成可点击的，点击进入下一步。



#### 5. 代码查找

首先按照第一步的方法找到数值的地址，双击它将会把它添加到下方的地址栏。

![image-20200407135855293](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407135855293.png)

右键，点击 找出是什么改写了这个地址 ，再次点击 改变数值 ，操作栏会多出一条操作。

![image-20200407140055732](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407140055732.png)

选中它，点击 替换 ，然后直接点 确定 ，再次点击改变数值，下一步 按钮会变成可点击的，点击进入下一步。



#### 6. 指针

使用第一步的方法找到数值的地址（千万不要点 改变指针！！！只要点 改变数值！！！）。

双击添加到地址栏，右键点击 找出是什么改写了这个地址 ，再次点击 改变数值 ，操作栏会多出一条操作。

![image-20200407140557254](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407140557254.png)

选中它，点击 详细信息，Cheat Engine 会提示你要找的地址，记住这个地址。

![image-20200407140705044](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407140705044.png)

点击确定，点击停止，再点击关闭，点击 新的扫描，在查找框中勾选 Hex ，把刚才找到的地址输入 数值 ，点击 首次扫描。

![image-20200407141028256](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407141028256.png)

这时扫描到的地址是绿色的，说明这是一个基址。

点击手动添加地址，勾选 指针 ，输入扫描到的基址，偏移量输入 0，点击 确定。

![image-20200407141602974](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407141602974.png)

双击数值栏改变数值，输入 5000 ，右键点击 锁定/解锁选中的地址 ，这时 下一步 按钮会变成可点击的，点击进入下一步。

#### 7. 代码注入

找到 健康值 的地址，双击添加到地址栏，右键点击 找出是什么改写了这个地址 ，再次点击 打我 ，选中新增的一行，选中它，点击 显示反汇编程序 ，点击工具，自动汇编，点击模板 ，选择 代码注入

![image-20200407160644732](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407160644732.png)

![image-20200407160800460](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407160800460.png)

将 newmem: 后的注释，修改为 ```add [xxx], 03``` （把 xxx 修改为上面 sub dword ptr [xxx], 01 中方括号中的内容）注意是 3 不是 2 ，因为源程序 -1 后必须再 +3​ 才能变成所要的 ​+2​ ，点击 执行 ，随后一路确定。

再一次点击 打我 ，现在下一步 按钮会变成可点击的，点击进入下一步。



#### 8. 多重指针

![image-20200407162133262](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407162133262.png)

首先跟第六步类似，先找到地址。

![image-20200407162010696](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407162010696.png)

根据 Cheat Engine 给出的地址（这里是 01571D10），记住它的偏移量（方括号中 ​+​ 后的内容），查找到指向它的指针，注意勾选 Hex。

![image-20200407162323648](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407162323648.png)

右键点击 找出是什么访问了这个地址 （对，没写错，就是访问），再次点击 改变数值 ，这时新增的有两行，选择包含 ```cmp...```的一行，选中它,点击 详细信息 ，记下地址和偏移量（如果没有找到偏移量则偏移量为 0）。

![image-20200407162551586](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407162551586.png)

![image-20200407162823364](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407162823364.png)

再次搜索给出的地址，重复以上操作，右键点击 找出是什么访问了这个地址 ，点击 改变数值 ，选择包含 ```cmp...```的一行，选中它，点击 详细信息 ，记下地址和偏移量。

![image-20200407170611452](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407170611452.png)

![image-20200407170655444](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407170655444.png)

查找给出的地址，右键点击 找出是什么访问了这个地址 ，点击 改变数值 ，选择包含 ```cmp...```的一行，选中它，点击 详细信息 ，记下地址和偏移量。

![image-20200407170845688](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407170845688.png)

![image-20200407170855286](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407170855286.png)

再次搜索给出的地址，这时查找到的地址应该为绿色的基址。

![image-20200407171005526](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407171005526.png)

双击添加到地址栏。点击 手动添加地址 ，勾选 指针 选项，输入前面找到的基址，点击三次 添加偏移 ，偏移量从上到下按照从先到后的顺序依次填入，点击确定。

![image-20200407171947164](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407171947164.png)

选择刚才添加的指针，再双击数值栏改变数值，输入 5000 ，右键点击 锁定/解锁选中的地址 ，点击 改变指针 ，这时 下一步 按钮会变成可点击的，点击进入下一步。

![image-20200407172038175](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200407172038175.png)



#### 9. 注入++

找到四个健康值的地址，注意健康值是单浮点。

![image-20200408130929405](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200408130929405.png)

双击添加到地址栏，右键点击 找出是什么改写了这个地址 ，再次点击 攻击 ，操作栏会多出一条操作。

![image-20200408131130315](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200408131130315.png)

选中那一条操作，点击 显示反汇编程序。点击 工具 ，选择 自动汇编 ，选择模板、AOB 注入 ，两个对话框保留默认。

![image-20200408131431715](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200408131431715.png)

在代码框中修改，注意代码中的 xxxxx 不要复制，只要复制没有被注释标记的代码，注释用来辅助你将代码放在正确的位置，将```define(address,"Tutorial-x86_64.exe"+xxxxx)```中的```xxxxx```替换为注释里```alloc(newmem,$1000,"Tutorial-x86_64.exe"+xxxxx)```中的```xxxxx```。

```assembly
/*{
  Game   : Tutorial-x86_64.exe
  Version: 
  Date   : 2020-04-08
  Author : ??????

  This script does blah blah blah
}*/

define(address,"Tutorial-x86_64.exe"+xxxxx)
define(bytes,Original bytes)

/*[ENABLE]

aobscanmodule(INJECT,Tutorial-x86_64.exe,F3 0F 11 43 08 0F) // should be unique
alloc(newmem,$1000,"Tutorial-x86_64.exe"+xxxxx)

label(code)*/
label(exit)
label(tp1)
label(tp2)
label(tp3)
/*label(return)*/

newmem:
  pushfq
  cmp rsi,01
  je tp1
  movss xmm0,[tp2]
  exit:
    popfq

/*code:
  movss [rbx+08],xmm0
  jmp return*/

tp1:
  movss [rbx+08],xmm0
  jmp exit

tp2:
  dd (float)5000

tp3:
  dd 0

/*INJECT:
  jmp newmem
return:
registersymbol(INJECT)*/

/*[DISABLE]*/

address:
  jmp newmem

dealloc(newmem)

/*INJECT:
  db F3 0F 11 43 08

unregistersymbol(INJECT)
dealloc(newmem)

{
// ORIGINAL CODE - INJECTION POINT: "Tutorial-x86_64.exe"+2EB6D

"Tutorial-x86_64.exe"+2EB43: E9 97 00 00 00           -  jmp Tutorial-x86_64.exe+2EBDF
"Tutorial-x86_64.exe"+2EB48: F3 0F 2A C6              -  cvtsi2ss xmm0,esi
"Tutorial-x86_64.exe"+2EB4C: F3 0F 10 4B 08           -  movss xmm1,[rbx+08]
"Tutorial-x86_64.exe"+2EB51: F3 0F 5C C8              -  subss xmm1,xmm0
"Tutorial-x86_64.exe"+2EB55: 0F 2F 0D 24 DC 1F 00     -  comiss xmm1,[Tutorial-x86_64.exe+22C780]
"Tutorial-x86_64.exe"+2EB5C: 7A 0C                    -  jp Tutorial-x86_64.exe+2EB6A
"Tutorial-x86_64.exe"+2EB5E: 73 0A                    -  jae Tutorial-x86_64.exe+2EB6A
"Tutorial-x86_64.exe"+2EB60: F3 0F 10 05 18 DC 1F 00  -  movss xmm0,[Tutorial-x86_64.exe+22C780]
"Tutorial-x86_64.exe"+2EB68: EB 03                    -  jmp Tutorial-x86_64.exe+2EB6D
"Tutorial-x86_64.exe"+2EB6A: 0F 28 C1                 -  movaps xmm0,xmm1
// ---------- INJECTING HERE ----------
"Tutorial-x86_64.exe"+2EB6D: F3 0F 11 43 08           -  movss [rbx+08],xmm0
// ---------- DONE INJECTING  ----------
"Tutorial-x86_64.exe"+2EB72: 0F 2F 05 07 DC 1F 00     -  comiss xmm0,[Tutorial-x86_64.exe+22C780]
"Tutorial-x86_64.exe"+2EB79: 7A 14                    -  jp Tutorial-x86_64.exe+2EB8F
"Tutorial-x86_64.exe"+2EB7B: 75 12                    -  jne Tutorial-x86_64.exe+2EB8F
"Tutorial-x86_64.exe"+2EB7D: 48 8B 4B 60              -  mov rcx,[rbx+60]
"Tutorial-x86_64.exe"+2EB81: 48 8B 15 40 10 18 00     -  mov rdx,[Tutorial-x86_64.exe+1AFBC8]
"Tutorial-x86_64.exe"+2EB88: E8 43 CB 07 00           -  call Tutorial-x86_64.exe+AB6D0
"Tutorial-x86_64.exe"+2EB8D: EB 42                    -  jmp Tutorial-x86_64.exe+2EBD1
"Tutorial-x86_64.exe"+2EB8F: F3 0F 10 4B 08           -  movss xmm1,[rbx+08]
"Tutorial-x86_64.exe"+2EB94: 48 8D 4D E0              -  lea rcx,[rbp-20]
"Tutorial-x86_64.exe"+2EB98: E8 73 B6 01 00           -  call Tutorial-x86_64.exe+4A210
}*/
```

这时点击 执行 ，随后一路确定，点击 重新启动游戏并自动执行 ，等待几秒后 下一步 会变成可点击的，点击进入下一步。



#### 10. 

你还在看？？？

你肯定没有动手做对不对？

如果你做了，那你肯定是看到了这个界面，这是实战教程了啦。

如果想看实战教程请回到首页找吧……

![image-20200408132613220](https://raw.githubusercontent.com/roymsi/cetu1/master/res/image-20200408132613220.png)



#### 11. 你怎么还在看啊！！！

是不是一直在点跳过，跳到了最后啊……

最后一步可不是在最后面哦……



### 12. 没了啦