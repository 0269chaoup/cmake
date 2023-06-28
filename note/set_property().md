# 签名
```cmake
set_property(<GLOBAL|
    DIRECTORY [dir] | 
    TARGET [target [target2 ...]]> |
    SOURCE [src1 [src2 ...]]> |
    TEST [test1 [test2 ...]]> |
    CACHE [entry1 [entry2 ...]]> |
    [APPEND][APPEND_STRING]
    PROPERTY <name> [value [value2...]])
```
# 参数
* GLOBAL
    * 全局属性
* DIRECTORY
    * 目录属性
* TARGET
    * 目标属性
* SOURCE
    * 源文件属性
* TEST
    * 测试属性
* CACHE
    * 缓存属性
* APPEND
    * 追加属性
* APPEND_STRING
    * 追加字符串
* PROPERTY
    * 属性名
* name
    * 属性名
* value
    * 属性值
* value2
    * 属性值
# 描述
- `set_property`: 在指定域中设置一个命名属性
- 在某个域中对零个或者多个对象设置一个属性。
  - 第一个参数决定了该属性设置所在的域。他必须是下列中的一个：
    - `GLOBAL`：全局域
    - `DIRECTORY [dir]`：目录域
      - `DIRECTORY` 域默认为当前目录，但也可以用全路径或者是相对路径指定其他的目录（前提是该目录已经被cmake处理了）
    - `TARGET [target [target2 ...]]`：目标域（可命名零个或者多个已经存在的目标）。
    - `SOURCE [src1 [src2 ...]]`：源文件域。**注意**：源文件属性只对在相同目录下的目标是可见的。
    - `TEST [test1 [test2 ...]]`：测试域。
    - `CACHE [entry1 [entry2 ...]]`：缓存域。
  - 必须项 `PROPERTY`  后面紧跟着属性名，属性名可以是任意的字符串，但是不能包含空格。其他的参数用于构建以分号隔开的列表形式的属性值。
  - 如果指定了`APPEND`选项，则指定的列表将会追加到任何已存在的属性值当中。如果指定了`APPEND_STRING`选项，则指定的字符串将会追加到任何已存在的属性值当中。
设置属性。如果没有给出`APPEND`或`APPEND_STRING`，则属性的值将被设置为给定的值。如果给出了`APPEND`，则属性的值将被设置为给定值的列表附加到属性的当前值。如果给出了`APPEND_STRING`，则属性的值将被设置为给定值的字符串附加到属性的当前值。如果属性不存在，则将创建它。如果属性已经存在，则将其值设置为给定值。如果属性已经存在，并且给出了`APPEND`，则将给定值的列表附加到属性的当前值。如果属性已经存在，并且给出了`APPEND_STRING`，则将给定值的字符串附加到属性的当前值。如果属性已经存在，并且没有给出`APPEND`或`APPEND_STRING`，则将其值设置为给定值。如果属性已经存在，并且给出了`APPEND`，则将给定值的列表附加到属性的当前值。如果属性已经存在，并且给出了`APPEND_STRING`，则将给定值的字符串附加到属性的当前值。如果属性已经存在，并且没有给出`APPEND`或`APPEND_STRING`，则将其值设置为给定值。如果属性已经存在，并且给出了`APPEND`，则将给定值的列表附加到属性的当前值。如果属性已经存在，并且给出了`APPEND_STRING`，则将给定值的字符串附加到属性的当前值。如果属性已经存在，并且没有给出`APPEND`或`APPEND_STRING`，则将其值设置为给定值。
# 示例`
## 1. 设置全局属性
```cmake
set_property(GLOBAL PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```
解释：
```cmake
这条CMake指令设置了全局属性RULE_LAUNCH_COMPILE，它将在编译时运行一个命令，并记录执行时间。该命令是${CMAKE_COMMAND} -E time。${CMAKE_COMMAND}是一个CMake内置的变量，它包含了CMake的可执行文件路径。-E time选项是CMake命令行工具中的一个选项，它将执行给定的命令并记录其执行时间。因此，这条指令的含义是在编译时记录每个编译命令的执行时间。
```
## 2. 设置目录属性
```cmake
set_property(DIRECTORY PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```
## 3. 设置目标属性
```cmake
set_property(TARGET mytarget PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```
## 4. 设置源文件属性
```cmake
set_property(SOURCE mysource.cpp PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```
## 5. 设置测试属性
```cmake
set_property(TEST mytest PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```
## 6. 设置缓存属性
```cmake
set_property(CACHE MYVAR PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```
## 7. 设置属性值
```cmake
set_property(GLOBAL PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```
## 8. 追加属性值
```cmake
set_property(GLOBAL APPEND PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```
## 9. 追加属性字符串
```cmake
set_property(GLOBAL APPEND_STRING PROPERTY RULE_LAUNCH_COMPILE "${CMAKE_COMMAND} -E time")
```

# 相关说明
* [cmake\README.md](../README.md)
* [cmake\note\set_property().md](note\set_property().md)
# 参考资料
* [cmake-set_property](https://cmake.org/cmake/help/latest/command/set_property.html)
* [cmake-set_property](https://cmake.org/cmake/help/v3.0/command/set_property.html)
* [cmake-set_property](https://cmake.org/cmake/help/v3.1/command/set_property.html)