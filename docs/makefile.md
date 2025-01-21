---
title: "Makefile"
---

# [Makefile](https://seisman.github.io/how-to-write-makefile/overview.html)

```makefile
include foo.make *.mk                           # 包含其他makefile，执行make时会在当前目录下查找，也可通过-I参数指定
objects = main.o kbd.o command.o display.o \    # "\"表示换行
    insert.o search.o files.o utils.o           # 定义变量，简化重复项

edit : $(objects)          # 第一项edit为make的目标生成文件，此处引用objects变量作为依赖项
    cc -o edit $(objects)  # 编译指令

main.o : defs.h            # 中间文件:编译依赖项
kbd.o : defs.h command.h
command.o : defs.h command.h
display.o : defs.h buffer.h
insert.o : defs.h buffer.h
search.o : defs.h buffer.h
files.o : defs.h buffer.h command.h
utils.o : defs.h

.PHONY : clean             # .PHONY 表示 clean 是个伪目标文件
clean :                    # clean指令默认放在make文件末尾
   -rm edit $(objects)     # 小减号的意思就是，也许某些文件出现问题，但不要管，继续做后面的事
```