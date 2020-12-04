# create_program_language
《自制编程语言》读书笔记及代码


## 第二章：试做一个计算器

`2.2/`下：
- 编译
```shell
yacc -dv mycalc.y
lex mycalc.l
cc -o mycalc y.tab.c lex.yy.c
```

- 执行
```shell
$ mycalc
1+2
>>3.000000
1+2*3
>>7.000000
```

`2.2.5-confilt/`下：
```shell
$ yacc -dv mycalc.y
conflicts: 3 shift/reduce
```

`2.2.6-error_handle/`下：
```shell
$ mycalc
2-3
>>-1.000000
1//2
parser error near /
2+2
>>4.000000
^C
```



## 遇到的问题及解决办法
### premature EOF
执行 `lex mycalc.l` 时，报错：`premature EOF`
大概率是因为
```
%{
    ...    
%}
```
写成了：
```
%{
    ...
}%
```

###  command not found: mycalc
需要将该命令加入环境变量中：
```shell
export PATH=${PATH}:~/Code/program_lanaguage/2.2
```
这里后半部分的`~/Code/program_lanaguage/2.2` 应当改为你自己的文件路径

