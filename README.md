# Jisp 编程语言

一个基于 λ-演算 的饥饿求值编程语言。    

## 工具链用法

### Jisp 主工具（`jisp.exe`, `Jisp.Interpreter`)
此工具包含Jisp的基本解释器和编译器，并提供一个REPL.

#### 以交互式编程方式启动
```shell
jisp
```

#### 解释运行一个Jisp程序
```shell
jisp jisp程序源代码 [命令行参数]
```

#### 编译一个Jisp程序
```shell
jisp -c jisp程序源代码 输出
jisp --compile jisp程序源代码 输出 
```

### Jisp 工程管理器 (`jisp-project.exe`, `jisp-project`)
该工具由Jisp语言自身写成，提供了jisp工程化的工具。    
如果您需要编译该工具，请执行`build-jisp-project.ps1`以生成`jisp-project.exe`。

#### Jisp 工程结构

```
hello_world				# 工程根目录
|- src					# 源码目录
|  |- first.jisp				# 源码
|  |- second.jisp
|  |- main.jisp
|- tests					# 单元测试目录		
|  |- test_first.jisp			# 单元测试源码
|  |- test_second.jisp
|- lib					# 引用的库目录
|  |- libio.jisplib			# 库文件
|- build					# 构建临时文件 (需要排除)
|- hello_world.exe			# 发布的二进制文件 (需要排除)
|- hello_world.jispapp		# 发布的Jisp App文件 (需要排除)
|- project.yml				# 工程文件
|- .gitignore				# git省略规则文件
```

project.yml:  
 
```yaml
project: hello_world
type: app					# 如果是lib，则生成jisplib文件，如果是app，则生成jispapp文件。
lib: libio
src: first.jisp
src: second.jisp
src: main.jisp
test: test_first
test: test_second
```

#### 创建一个Jisp项目
```shell
jisp-project new 项目名称
```

#### 编译当前项目
```shell
jisp-project build
```

#### 运行当前项目
```shell
jisp-project run
```

#### 单元测试相关

##### 创建单元测试
```shell
jisp-project test new 单元测试名称
```

##### 执行单元测试
```shell
jisp-project test run [单元测试名称]
```

## 特性
* 使用Y-组合子实现递归
* Call-CC以及使用Call-CC实现循环、异常控制流
* 与F#编程语言具有良好的交互性
* 完全“纯”的计算环境
* 支持Eval
* 极小语言核心，使用库来充实功能
* 使用Jisp语言自身实现的工程管理系统与单元测试系统

## 例子程序

[HelloWorld](Examples/HelloWorld.jisp)
```
print-str-ln "Hello, world!"
```

[布尔运算](Examples/Boolean.jisp)   
[丘奇数](Examples/Church-Numerals.jisp)   
[列表](Examples/Functional-List.jisp)   
[Call-CC与控制流例子](Examples/Call-CC.jisp)    
[打印斐波那契数列](Examples/Fibonacci.jisp)     
[打印命令行参数](Examples/PrintCommandLineArguments.jisp)     
[生命游戏](Examples/LifeGame.jisp)      
[Brainf*ck语言解释器](Examples/Brainfxxk.jisp)    
[Monad例子](Examples/BoxMonad.jisp)        
[Jisp标准库](Jisp/stdlib.jisp)    
