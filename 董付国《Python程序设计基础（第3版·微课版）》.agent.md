董付国《Python程序设计基础（第3版·微课版）》
以下是董付国《Python程序设计基础（第3版·微课版）》全13章逐章超详细知识点拆解，覆盖每个核心概念的定义、语法、实操细节与典型案例，适配零基础入门到实战应用的全流程学习需求：

第1章 Python开发环境搭建与使用

1.1 Python语言认知

- 核心特点：简洁易读（语法贴近自然语言）、跨平台（Windows/macOS/Linux通用）、解释型（逐行执行，无需编译）、多范式（支持面向对象、过程式、函数式编程）、丰富的库生态；
- 版本差异：Python 3.x与2.x核心区别（print为函数需加括号、整数除法返回float、字符串默认UTF-8编码），推荐使用3.8-3.11版本（兼容性与新特性平衡）。

1.2 环境搭建（分系统）

- Windows系统：
- 下载地址：Python官网（https://www.python.org/），选择64位安装包；
- 安装步骤：勾选“Add Python to PATH”（自动配置环境变量），自定义安装路径（避免中文空格）；
- 验证：cmd中输入 python --version ，显示版本号即成功。
- macOS系统：
- 方式1：官网安装包（注意适配macOS版本）；
- 方式2：Homebrew安装（ brew install python3 ）；
- 验证：终端输入 python3 --version （系统默认可能保留Python 2.x，需用python3调用）。
- Linux系统（Ubuntu/Debian）：
- 自带Python 3，验证： python3 --version ；
- 升级/安装： sudo apt update && sudo apt install python3 python3-pip 。

1.3 开发工具详解

- IDLE：
- 交互式环境：打开即运行，支持即时执行代码（如输入 1+2 直接返回结果）；
- 脚本编辑器：File→New File创建.py文件，编写后F5运行，支持语法高亮、缩进提示、错误提示。
- Anaconda3：
- 核心功能：环境管理（创建独立环境 conda create -n env_name python=3.10 ）、包管理（ conda install 包名 ）；
- 配套工具：Jupyter Notebook（浏览器中分段执行代码，支持Markdown笔记）、Spyder（类似MATLAB的IDE，含代码编辑区、变量查看器、控制台）。
- Jupyter Notebook：
- 操作：终端输入 jupyter notebook 启动，新建Python 3文件；
- 技巧：单元格分代码块（Ctrl+Enter运行）、Markdown单元格（编写注释/笔记）、快捷键（Shift+Enter运行并新建单元格）。
- PyCharm（补充，教材推荐）：
- 社区版：免费，支持代码补全、调试、版本控制；
- 基础操作：新建项目（选择Python解释器）、创建.py文件、运行（右键→Run）、调试（设置断点，Shift+F9启动）。

1.4 库的安装与导入

- 安装方式：
- pip安装（通用）： pip install 包名 （如 pip install pandas ）、指定版本 pip install 包名==版本号 、升级 pip install --upgrade 包名 ；
- conda安装（Anaconda环境）： conda install 包名 ，自动解决依赖冲突；
- 国内源加速： pip install 包名 -i https://pypi.tuna.tsinghua.edu.cn/simple （清华源）。
- 导入方式：
- 全量导入： import numpy （使用时需 numpy.array() ）；
- 部分导入： from numpy import array （直接使用 array() ）；
- 别名导入： import numpy as np （简洁， np.array() ）；
- 导入所有： from numpy import * （不推荐，易冲突）。
- 库的分类：
- 标准库：Python自带，无需安装（如os、sys、random、datetime）；
- 扩展库：第三方开发，需手动安装（如pandas、matplotlib、requests）。

第2章 运算符、表达式与内置对象

2.1 运算符详解

- 算术运算符：
- 基础运算： + （加）、 - （减）、 * （乘）、 / （除，返回float，如 3/2=1.5 ）、 // （整除，如 3//2=1 ）、 % （取余，如 3%2=1 ）、 ** （幂运算，如 2**3=8 ）；
- 特殊用法： * 用于字符串重复（ "ab"*3="ababab" ）、列表重复（ [1,2]*3=[1,2,1,2,1,2] ）。
- 赋值运算符：
- 基础赋值： = （ a=5 ）；
- 复合赋值： += （ a+=3 等价 a=a+3 ）、 -= 、 *= 、 /= 、 //= 、 %= 、 **= 。
- 比较运算符：
- 结果：返回bool值（True/False）；
- 类型： == （值相等， 1==1.0=True ）、 != （值不等）、 > （大于）、 < （小于）、 >= （大于等于）、 <= （小于等于）；
- 注意： == 与 is 区别（ == 比较值， is 比较内存地址，如 [1,2]==[1,2]=True ， [1,2] is [1,2]=False ）。
- 逻辑运算符：
-  and ：逻辑与，两边都为True才返回True（短路求值：左边为False则不计算右边）；
-  or ：逻辑或，任意一边为True返回True（短路求值：左边为True则不计算右边）；
-  not ：逻辑非，取反（ not True=False ）；
- 优先级： not > and > or 。
- 成员运算符：
-  in ：判断元素是否在序列/集合中（ 2 in [1,2,3]=True ）；
-  not in ：判断元素是否不在序列/集合中（ 4 not in [1,2,3]=True ）。
- 身份运算符：
-  is ：判断两个对象是否指向同一内存地址（ a=1; b=1; a is b=True ，小整数池优化）；
-  is not ：判断两个对象是否指向不同内存地址。

2.2 表达式与运算符优先级

- 表达式：由运算符和操作数组成（如 3*2+5 、 a>b and c<<d ）；
- 优先级（从高到低）：
1. 括号（ () ）；
2. 幂运算（ ** ）；
3. 算术运算符（ * 、 / 、 // 、 %  >  + 、 - ）；
4. 比较运算符（ == 、 != 、 > 等）；
5. 逻辑运算符（ not  >  and  >  or ）；
6. 赋值运算符（ = 、 += 等）；
- 结合性：大部分从左到右（如 3+2+1=6 ），幂运算从右到左（如 2**3**2=2^(3^2)=512 ）。

2.3 内置对象与内置函数

- 基本数据类型：
-  int （整数）：支持任意大小整数（如 100 、 -5 、 0x10 （十六进制）、 0o10 （八进制）、 0b10 （二进制））；
-  float （浮点数）：如 3.14 、 -0.5 、 1e3 （1000.0），注意精度问题（ 0.1+0.2=0.30000000000000004 ，需用decimal模块解决）；
-  complex （复数）： a+bj 形式（如 3+4j ），实部 3 、虚部 4 ，支持 + 、 - 、 * 、 / 运算；
-  bool （布尔值）：仅True（1）和False（0），可参与算术运算（ True+1=2 ）；
-  str （字符串）：字符序列，用 '' 、 "" 或 """ 包裹（如 'hello' 、 "Python" 、 """多行字符串""" ）。
- 常用内置函数：
- 输出与输入： print(value, ..., sep=' ', end='\n') （sep分隔符，end结束符，如 print(1,2,sep=',',end='!') 输出 1,2! ）、 input(prompt) （获取用户输入，返回字符串，需类型转换： a=int(input("请输入数字：")) ）；
- 类型转换： int(x) （字符串/浮点数转整数， int('5')=5 、 int(3.8)=3 ）、 float(x) （转浮点数）、 str(x) （转字符串）、 bool(x) （转布尔值，0、空序列、None为False，其余为True）；
- 序列操作： len(s) （求长度， len([1,2,3])=3 、 len("abc")=3 ）、 max(s) （求最大值， max([1,2,3])=3 ）、 min(s) （求最小值）、 sum(s) （求和， sum([1,2,3])=6 ）；
- 其他： type(x) （判断类型， type(5)=<class 'int'> ）、 id(x) （返回对象内存地址）、 range(start, end, step) （生成整数序列，如 range(1,5)=[1,2,3,4] ）。

第3章 内置数据结构

3.1 列表（list）—— 可变序列

- 创建方式：
- 直接创建： lst = [1, 2, 'a', True] （支持不同数据类型）；
- 构造函数： lst = list() （空列表）、 lst = list((1,2,3)) （元组转列表）、 lst = list("abc") （字符串转列表， ['a','b','c'] ）；
- 列表推导式： lst = [x*2 for x in range(5)] （ [0,2,4,6,8] ）、 lst = [x for x in range(10) if x%2==0] （筛选偶数， [0,2,4,6,8] ）。
- 核心操作（增删改查）：
- 增：
-  append(x) ：末尾添加元素（ lst.append(3) ，原地修改）；
-  insert(index, x) ：指定位置插入（ lst.insert(1, 'b') ，在索引1处插入）；
-  extend(iterable) ：添加可迭代对象的所有元素（ lst.extend([4,5]) ，等价 lst += [4,5] ）。
- 删：
-  pop(index) ：删除指定索引元素，返回该元素（默认删除最后一个， lst.pop() ）；
-  remove(x) ：删除第一个匹配的元素（ lst.remove(2) ，无返回值）；
-  del lst[index] ：删除指定索引元素（ del lst[0] ）、删除切片（ del lst[1:3] ）、清空列表（ del lst[:] ）；
-  clear() ：清空列表（ lst.clear() ，等价 lst = [] ）。
- 改：
- 直接赋值： lst[0] = 'new' （修改索引0元素）；
- 切片赋值： lst[1:3] = [6,7] （替换索引1-2元素）。
- 查：
- 索引访问： lst[index] （正向索引从0开始，反向索引从-1开始， lst[-1] 取最后一个元素）；
- 切片访问： lst[start:end:step] （默认start=0、end=len(lst)、step=1， lst[1:4] 取索引1-3元素， lst[::2] 步长2取元素）；
-  index(x, start=0, end=len(lst)) ：返回第一个匹配x的索引（无则报错）；
-  count(x) ：返回x出现的次数（ lst.count(2) ）；
- 成员判断： x in lst （ 2 in [1,2,3]=True ）。
- 其他常用方法：
-  sort(key=None, reverse=False) ：原地排序（默认升序， reverse=True 降序， key=len 按长度排序）；
-  reverse() ：原地反转列表（ lst.reverse() ，等价 lst = lst[::-1] ）；
-  copy() ：浅拷贝（ lst2 = lst.copy() ，等价 lst2 = lst[:] ，修改lst2不影响原lst）。

3.2 元组（tuple）—— 不可变序列

- 创建方式：
- 直接创建： tup = (1, 2, 'a') （括号可省略， tup = 1,2,'a' ）；
- 构造函数： tup = tuple() （空元组）、 tup = tuple([1,2,3]) （列表转元组）；
- 注意：单元素元组需加逗号（ tup = (5,) ，否则为 int 类型）。
- 核心特性与操作：
- 不可变性：创建后无法修改元素（ tup[0] = 10 报错），但元素为可变对象时可修改其内部（ tup = (1, [2,3]); tup[1].append(4) ，结果 (1, [2,3,4]) ）；
- 访问操作：与列表一致（索引、切片、 index() 、 count() 、 in 判断）；
- 拆包操作： a, b, c = (1,2,3) （ a=1, b=2, c=3 ）、 a, *b = (1,2,3,4) （ a=1, b=[2,3,4] ）；
- 常用场景：函数返回多值（本质是元组， def func(): return 1,2; a,b=func() ）、存储固定不变的数据（如坐标 (x,y) ）。

3.3 字典（dict）—— 键值对映射

- 创建方式：
- 直接创建： dic = {'name': '张三', 'age': 20, 'gender': '男'} （键为不可变类型：int、str、tuple等，值可任意）；
- 构造函数： dic = dict() （空字典）、 dic = dict(name='张三', age=20) （关键字参数）、 dic = dict([('name','张三'), ('age',20)]) （列表转字典）；
- 字典推导式： dic = {k: v*2 for k, v in {'a':1, 'b':2}.items()} （ {'a':2, 'b':4} ）。
- 核心操作（增删改查）：
- 增：
- 直接赋值： dic['score'] = 90 （键不存在则新增）；
-  update(iterable) ：批量添加/修改（ dic.update({'score':90, 'city':'北京'}) 或 dic.update(score=90, city='北京') ）。
- 删：
-  pop(key, default) ：删除指定键，返回对应值（键不存在则返回default， dic.pop('age', 0) ）；
-  del dic[key] ：删除指定键（ del dic['gender'] ）；
-  clear() ：清空字典（ dic.clear() ）；
-  popitem() ：删除并返回最后一个键值对（Python 3.7+有序）。
- 改：直接赋值（ dic['age'] = 21 ，键存在则修改值）。
- 查：
- 直接访问： dic['name'] （键不存在报错）；
-  get(key, default) ：键存在返回值，不存在返回default（ dic.get('score', 0) ，推荐使用）；
- 键/值/键值对遍历： dic.keys() （所有键， dict_keys(['name','age']) ）、 dic.values() （所有值）、 dic.items() （所有键值对， dict_items([('name','张三'), ('age',20)]) ）；
- 成员判断： key in dic （判断键是否存在， 'name' in dic=True ）。
- 其他常用方法：
-  copy() ：浅拷贝（ dic2 = dic.copy() ，修改dic2的可变值不影响原dic）；
-  fromkeys(seq, value) ：创建新字典，seq为键，value为默认值（ dict.fromkeys(['a','b'], 0) ， {'a':0, 'b':0} ）。

3.4 集合（set）—— 无序不重复集合

- 创建方式：
- 直接创建： s = {1, 2, 3} （不可用 {} 创建空集合，为空字典）；
- 构造函数： s = set() （空集合）、 s = set([1,2,2,3]) （列表转集合，自动去重， {1,2,3} ）、 s = set("aabbcc") （字符串转集合， {'a','b','c'} ）。
- 核心操作（增删、集合运算）：
- 增：
-  add(x) ：添加单个元素（ s.add(4) ，元素已存在则不报错）；
-  update(iterable) ：添加可迭代对象的所有元素（ s.update([5,6]) ，自动去重）。
- 删：
-  remove(x) ：删除元素，不存在则报错；
-  discard(x) ：删除元素，不存在则不报错（推荐使用）；
-  pop() ：随机删除并返回一个元素（无序）；
-  clear() ：清空集合。
- 集合运算（核心价值）：
- 交集（&）： s1 & s2 或 s1.intersection(s2) ，返回共同元素（ {1,2} & {2,3}={2} ）；
- 并集（|）： s1 | s2 或 s1.union(s2) ，返回所有元素（去重）（ {1,2} | {2,3}={1,2,3} ）；
- 差集（-）： s1 - s2 或 s1.difference(s2) ，返回s1独有的元素（ {1,2} - {2,3}={1} ）；
- 对称差集（^）： s1 ^ s2 或 s1.symmetric_difference(s2) ，返回互不相同的元素（ {1,2} ^ {2,3}={1,3} ）；
- 子集判断： s1.issubset(s2) （s1是否是s2的子集）、 s1.issuperset(s2) （s1是否是s2的超集）。

3.5 实用技巧

- 序列解包：将序列元素赋值给多个变量（ a,b,c = [1,2,3] 、 a,*b,c = [1,2,3,4] ）；
- 生成器推导式： (x*2 for x in range(5)) （返回生成器对象，节省内存，需通过 list() 或循环转换）；
- 不可变序列vs可变序列：
- 不可变（tuple、str）：创建后无法修改元素，支持索引、切片、 in 判断；
- 可变（list、dict、set）：支持增删改操作，灵活调整内容。

第4章 程序控制结构

4.1 选择结构（分支结构）

- 单分支结构（if）：
- 语法：
python

if 条件表达式:
    代码块（缩进4个空格）

- 说明：条件表达式为True时执行代码块，False则跳过（如 if a>10: print("a大于10") ）。
- 双分支结构（if-else）：
- 语法：
python

if 条件表达式:
    代码块1
else:
    代码块2

- 案例：
python

score = 85
if score >= 60:
    print("及格")
else:
    print("不及格")

- 多分支结构（if-elif-else）：
- 语法：
python

if 条件表达式1:
    代码块1
elif 条件表达式2:
    代码块2
...
else:
    代码块n

- 说明：依次判断条件，满足一个则执行对应代码块，后续不再判断；
- 案例：
python

score = 85
if score >= 90:
    print("优秀")
elif score >= 80:
    print("良好")
elif score >= 60:
    print("及格")
else:
    print("不及格")

- 条件表达式（三元运算符）：
- 语法： 变量 = 表达式1 if 条件表达式 else 表达式2 （条件为True返回表达式1，否则返回表达式2）；
- 案例： result = "及格" if score >=60 else "不及格" （等价于if-else双分支）。
- 嵌套选择结构：
- 语法：选择结构内部嵌套选择结构（缩进区分层级）；
- 案例：
python

score = 85
if score >= 60:
    if score >= 90:
        print("优秀")
    else:
        print("及格")
else:
    print("不及格")


4.2 循环结构

- for循环（遍历序列/可迭代对象）：
- 基本语法：
python

for 变量 in 可迭代对象:
    代码块

- 可迭代对象：列表、元组、字符串、集合、字典、range()、文件对象等；
- 案例1（遍历序列）：
python

for char in "Python":
    print(char)  # 逐行输出P、y、t、h、o、n

- 案例2（range()函数）：
python

for i in range(1, 5):  # 生成1-4的整数序列
    print(i)  # 输出1、2、3、4
for i in range(0, 10, 2):  # 步长2，生成0、2、4、6、8
    print(i)

- 案例3（遍历字典）：
python

dic = {'name': '张三', 'age':20}
for key in dic.keys():
    print(key)  # 输出name、age
for value in dic.values():
    print(value)  # 输出张三、20
for k, v in dic.items():
    print(k, v)  # 输出name 张三、age 20

- for-else结构：循环正常结束（未被break中断）时执行else代码块：
python

for i in range(3):
    print(i)
else:
    print("循环正常结束")  # 会执行

- while循环（条件循环）：
- 基本语法：
python

while 条件表达式:
    代码块

- 说明：条件表达式为True时重复执行代码块，False则退出循环；
- 案例1（基本循环）：
python

i = 1
while i <= 5:
    print(i)  # 输出1-5
    i += 1  # 计数器自增，避免死循环

- 案例2（死循环与退出）：
python

while True:
    user_input = input("请输入指令（输入q退出）：")
    if user_input == 'q':
        break  # 退出循环
    print(f"你输入的指令是：{user_input}")

- while-else结构：与for-else一致，循环正常结束时执行else。

4.3 循环控制语句

- break：终止当前循环，跳出循环体（不再执行后续迭代）；
- 案例：
python

for i in range(10):
    if i == 5:
        break  # 当i=5时终止循环
    print(i)  # 输出0-4

- continue：跳过本次循环的剩余代码，直接进入下一次迭代；
- 案例：
python

for i in range(10):
    if i % 2 == 0:
        continue  # 跳过偶数，执行下一次迭代
    print(i)  # 输出1、3、5、7、9

- pass：占位符，无实际功能，用于填充语法空白（避免报错）；
- 案例：
python

for i in range(5):
    if i == 2:
        pass  # 暂时不处理，后续补充代码
    else:
        print(i)  # 输出0、1、3、4


4.4 嵌套循环（循环中嵌套循环）

- 基本语法：
python

for 变量1 in 可迭代对象1:
    for 变量2 in 可迭代对象2:
        代码块

- 案例1（九九乘法表）：
python

for i in range(1, 10):
    for j in range(1, i+1):
        print(f"{j}×{i}={i*j}", end="\t")
    print()  # 换行

- 案例2（矩阵遍历）：
python

matrix = [[1,2,3], [4,5,6], [7,8,9]]
for row in matrix:
    for num in row:
        print(num, end=" ")
    print()  # 输出1 2 3；4 5 6；7 8 9

- 注意：嵌套层数不宜过多（一般不超过3层），避免代码复杂度过高。

第5章 函数

5.1 函数基础（定义、调用、返回值）

- 函数定义：
- 语法：
python

def 函数名(参数列表):
    """函数文档字符串（说明功能、参数、返回值）"""
    函数体（代码块）
    return 返回值

- 说明： def 关键字声明函数，函数名遵循变量命名规范，参数列表可选，函数体需缩进， return 可选（无则返回None）；
- 案例：
python

def add(a, b):
    """计算两个数的和
    参数：
        a: 第一个数
        b: 第二个数
    返回值：
        两数之和
    """
    return a + b

- 函数调用：
- 语法： 函数名(参数列表) （实参需与形参匹配）；
- 案例： result = add(3, 5) （ result=8 ）；
- 注意：函数必须先定义后调用（Python解释器逐行执行）。
- 返回值（return语句）：
- 无返回值：函数中无 return 或 return 后无值，返回None（ def func(): print("hello") ， func()返回None ）；
- 单个返回值： return 值 （如上述add函数）；
- 多个返回值： return 值1, 值2, ... （本质返回元组，可拆包： a,b = func() ）；
- 案例（多返回值）：
python

def get_info():
    name = "张三"
    age = 20
    return name, age
name, age = get_info()  # name="张三"，age=20


5.2 参数传递（形参vs实参）

- 形参类型（定义函数时指定）：
- 位置参数：按顺序传递，必须传入且数量匹配（ def add(a,b): return a+b ，调用时 add(3,5) ）；
- 关键字参数：指定参数名传递，顺序可任意（ add(b=5, a=3) ，结果同上）；
- 默认参数：定义时指定默认值，调用时可省略（ def add(a, b=2): return a+b ， add(3) 返回5， add(3,4) 返回7）；
- 注意：默认参数必须放在位置参数之后（否则语法错误）；
- 可变位置参数（*args）：接收任意数量的位置实参，打包为元组（ def func(*args): print(args) ， func(1,2,3) 输出 (1,2,3) ）；
- 可变关键字参数（**kwargs）：接收任意数量的关键字实参，打包为字典（ def func(**kwargs): print(kwargs) ， func(name="张三", age=20) 输出 {'name':'张三','age':20} ）；
- 混合使用顺序：位置参数→默认参数→*args→**kwargs（ def func(a, b=2, *args, **kwargs): ... ）。
- 实参传递方式：
- 位置传递：按形参顺序传入（ add(3,5) ）；
- 关键字传递： add(a=3, b=5) 或 add(b=5, a=3) ；
- 混合传递：位置参数在前，关键字参数在后（ add(3, b=5) 合法， add(a=3,5) 非法）。
- 参数传递机制：
- 不可变对象（int、str、tuple等）：值传递，函数内修改不影响外部（ def func(x): x=10; a=5; func(a); print(a) 输出5）；
- 可变对象（list、dict、set等）：引用传递，函数内修改影响外部（ def func(lst): lst.append(10); lst=[1,2]; func(lst); print(lst) 输出 [1,2,10] ）。

5.3 变量作用域

- 作用域分类：
- 局部变量：函数内部定义的变量，仅在函数内有效（函数执行结束后销毁）；
- 案例：
python

def func():
    x = 10  # 局部变量
    print(x)
func()  # 输出10
print(x)  # 报错，x未定义

- 全局变量：函数外部定义的变量（或 global 声明的变量），整个程序有效；
- 案例1（直接使用全局变量）：
python

x = 10  # 全局变量
def func():
    print(x)  # 读取全局变量
func()  # 输出10

- 案例2（修改全局变量，需 global 声明）：
python

x = 10
def func():
    global x  # 声明x为全局变量
    x = 20  # 修改全局变量
func()
print(x)  # 输出20

- 非局部变量（nonlocal）：嵌套函数中，内层函数修改外层函数的局部变量（需 nonlocal 声明）；
- 案例：
python

def outer():
    x = 10
    def inner():
        nonlocal x  # 声明x为非局部变量
        x = 20
    inner()
    print(x)  # 输出20
outer()

- 作用域查找顺序（LEGB规则）：
- 局部作用域（Local）→ 嵌套作用域（Enclosing）→ 全局作用域（Global）→ 内置作用域（Built-in）。

5.4 进阶函数

- lambda匿名函数：
- 语法： lambda 参数列表: 表达式 （仅一行表达式，返回结果）；
- 特点：简洁，无需定义函数名，适用于简单逻辑；
- 案例：
python

add = lambda a,b: a+b  # 等价于def add(a,b): return a+b
print(add(3,5))  # 输出8

- 常用场景：作为高阶函数的参数（如 sort() 的 key 参数）：
python

lst = [(1,3), (2,1), (3,2)]
lst.sort(key=lambda x: x[1])  # 按元组第二个元素排序，结果[(2,1), (3,2), (1,3)]

- 高阶函数（操作函数的函数）：
-  map(func, iterable) ：将func应用于可迭代对象的每个元素，返回迭代器；
- 案例： list(map(lambda x: x*2, [1,2,3])) （ [2,4,6] ）；
-  filter(func, iterable) ：筛选可迭代对象中使func返回True的元素，返回迭代器；
- 案例： list(filter(lambda x: x%2==0, [1,2,3,4])) （ [2,4] ）；
-  reduce(func, iterable) ：累积计算（func接收两个参数，返回一个结果，依次迭代）；
- 案例： from functools import reduce; reduce(lambda x,y: x+y, [1,2,3,4]) （ 1+2+3+4=10 ）。
- 函数嵌套（内部函数）：
- 语法：函数内部定义另一个函数；
- 案例：
python

def outer():
    def inner():
        print("内部函数")
    inner()  # 内部函数仅在外部函数内可调用
outer()  # 输出"内部函数"

- 递归函数（调用自身的函数）：
- 核心要素：递归条件（终止递归的条件）、递归步骤（分解问题）；
- 案例1（阶乘计算）：
python

def factorial(n):
    if n == 1:  # 递归终止条件
        return 1
    return n * factorial(n-1)  # 递归步骤
print(factorial(5))  # 5! = 120

- 案例2（斐波那契数列，第n项）：
python

def fib(n):
    if n <= 2:
        return 1
    return fib(n-1) + fib(n-2)
print(fib(5))  # 第5项为5

- 注意：递归深度有限制（Python默认递归深度约1000，超过会报错），复杂问题可优化为迭代或动态规划。
- 装饰器（decorator）：
- 作用：在不修改原函数代码的前提下，为函数添加额外功能（如日志记录、性能计时、权限验证）；
- 无参装饰器案例（日志记录）：
python

def log_decorator(func):
    def wrapper(*args, **kwargs):
        print(f"调用函数：{func.__name__}")
        result = func(*args, **kwargs)
        print(f"函数{func.__name__}调用结束")
        return result
    return wrapper
@log_decorator  # 为add函数添加装饰器
def add(a, b):
    return a + b
add(3,5)  # 输出"调用函数：add"、"函数add调用结束"，返回8

- 带参装饰器案例（指定日志前缀）：
python

def log_decorator(prefix):
    def decorator(func):
        def wrapper(*args, **kwargs):
            print(f"{prefix}：调用函数{func.__name__}")
            result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator
@log_decorator("INFO")
def add(a, b):
    return a + b
add(3,5)  # 输出"INFO：调用函数add"


5.5 函数文档与帮助

- 函数文档字符串：定义函数时在函数体开头添加 """文档内容""" ，说明函数功能、参数、返回值；
- 查看文档： help(函数名) （如 help(add) ）或 print(函数名.__doc__) ；
- 案例：
python

def add(a, b):
    """计算两个数的和
    参数：
        a: 整数或浮点数
        b: 整数或浮点数
    返回值：
        整数或浮点数，a与b的和
    """
    return a + b
help(add)  # 输出完整文档
print(add.__doc__)  # 输出文档内容


第6章 面向对象程序设计

6.1 类与对象（基础概念）

- 核心概念：
- 类（class）：抽象的模板，定义对象的属性和方法（如“人”是类，包含姓名、年龄属性，吃饭、睡觉方法）；
- 对象（instance）：类的实例化结果，具体的个体（如“张三”是“人”类的对象）；
- 面向对象三大特性：封装、继承、多态。
- 类的定义与对象实例化：
- 类的定义：
python

class Person:
    """人类"""
    # 类属性（所有实例共享）
    species = "人类"
    # 构造方法（初始化实例属性）
    def __init__(self, name, age):
        # 实例属性（每个实例独有）
        self.name = name
        self.age = age
    # 实例方法（第一个参数为self，指向当前实例）
    def eat(self, food):
        print(f"{self.name}在吃{food}")
    def sleep(self):
        print(f"{self.name}在睡觉")

- 对象实例化： 对象名 = 类名(参数) （调用 __init__ 方法）；
- 案例：
python

zhangsan = Person("张三", 20)  # 创建对象
print(zhangsan.name)  # 访问实例属性，输出"张三"
print(zhangsan.species)  # 访问类属性，输出"人类"
zhangsan.eat("米饭")  # 调用实例方法，输出"张三在吃米饭"
zhangsan.sleep()  # 输出"张三在睡觉"


6.2 类的属性与方法

- 属性分类：
- 实例属性：在 __init__ 方法中通过 self.属性名 定义，每个实例独有（如 name 、 age ）；
- 类属性：在类体内、方法外定义，所有实例共享（如 species ），可通过 类名.属性名 或 对象名.属性名 访问；
- 注意：修改类属性需通过 类名.属性名 （ Person.species=" Homo sapiens" ），通过对象修改仅创建实例属性，不影响类属性。
- 方法分类：
- 实例方法：第一个参数为 self ，需通过对象调用，可访问实例属性和类属性（如 eat() 、 sleep() ）；
- 类方法：
- 语法：用 @classmethod 装饰器，第一个参数为 cls （指向当前类）；
- 功能：操作类属性，无需实例化即可调用（ 类名.方法名() ）；
- 案例：
python

class Person:
    species = "人类"
    @classmethod
    def get_species(cls):
        return cls.species
print(Person.get_species())  # 输出"人类"（无需创建对象）

- 静态方法：
- 语法：用 @staticmethod 装饰器，无默认参数；
- 功能：与类和实例无关，仅为类的“工具函数”，可通过类名或对象调用；
- 案例：
python

class Person:
    @staticmethod
    def add(a, b):
        return a + b
print(Person.add(3,5))  # 输出8
zhangsan = Person("张三",20)
print(zhangsan.add(3,5))  # 输出8


6.3 面向对象三大特性

- 封装（隐藏内部细节，对外提供接口）：
- 实现方式：属性私有化（在属性名前加 __ ，如 __name ），通过 getter （获取属性）和 setter （修改属性）方法访问；
- 案例：
python

class Person:
    def __init__(self, name, age):
        self.__name = name  # 私有属性
        self.__age = age
    # getter方法（获取私有属性）
    def get_name(self):
        return self.__name
    # setter方法（修改私有属性，可添加验证逻辑）
    def set_age(self, age):
        if age > 0 and age < 120:
            self.__age = age
        else:
            print("年龄不合法")
    def get_age(self):
        return self.__age
zhangsan = Person("张三",20)
print(zhangsan.get_name())  # 输出"张三"（通过getter访问）
zhangsan.set_age(25)  # 通过setter修改年龄
print(zhangsan.get_age())  # 输出25
zhangsan.set_age(150)  # 输出"年龄不合法"

- 原理：私有属性会被Python重命名为 _类名__属性名 （如 _Person__name ），仍可访问（不推荐），本质是“名字修饰”而非真正私有。
- 继承（子类复用父类的属性和方法，可扩展新功能）：
- 单继承：
- 语法： class 子类名(父类名): ... ；
- 案例：
python

class Student(Person):  # Student类继承Person类
    def __init__(self, name, age, student_id):
        # 调用父类构造方法（两种方式）
        super().__init__(name, age)  # 推荐，无需指定父类名
        # Person.__init__(self, name, age)  # 需传入self
        self.student_id = student_id  # 子类新增属性
    # 子类新增方法
    def study(self, subject):
        print(f"{self.get_name()}（学号：{self.student_id}）在学习{subject}")
lisi = Student("李四", 18, "2024001")
print(lisi.get_age())  # 继承父类方法，输出18
lisi.study("Python")  # 子类方法，输出"李四（学号：2024001）在学习Python"

- 多继承：
- 语法： class 子类名(父类1, 父类2, ...): ... ；
- 注意：继承顺序（MRO，方法解析顺序），优先从左到右、从子类到父类查找方法；
- 案例：
python

class A:
    def func(self):
        print("A的func方法")
class B:
    def func(self):
        print("B的func方法")
class C(A, B):  # 先继承A，再继承B
    pass
c = C()
c.func()  # 输出"A的func方法"（按继承顺序查找）

- 多态（不同子类对同一父类方法的重写，表现不同行为）：
- 实现条件：继承、方法重写；
- 案例：
python

class Animal:
    def sound(self):
        print("动物发出声音")
class Dog(Animal):
    # 重写父类方法
    def sound(self):
        print("小狗汪汪叫")
class Cat(Animal):
    # 重写父类方法
    def sound(self):
        print("小猫喵喵叫")
# 多态体现：同一接口（sound方法），不同实现
def make_sound(animal):
    animal.sound()
dog = Dog()
cat = Cat()
make_sound(dog)  # 输出"小狗汪汪叫"
make_sound(cat)  # 输出"小猫喵喵叫"


6.4 特殊方法（魔法方法）

- 常用特殊方法：
-  __init__(self, ...) ：构造方法，对象实例化时自动调用；
-  __str__(self) ：返回对象的字符串表示（ print(对象) 时调用），需返回字符串；
- 案例：
python

class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def __str__(self):
        return f"Person(name='{self.name}', age={self.age})"
zhangsan = Person("张三",20)
print(zhangsan)  # 输出"Person(name='张三', age=20)"

-  __repr__(self) ：返回对象的官方字符串表示（ repr(对象) 时调用），用于调试；
-  __len__(self) ： len(对象) 时调用，返回对象的“长度”；
- 案例：
python

class MyList:
    def __init__(self, data):
        self.data = data
    def __len__(self):
        return len(self.data)
lst = MyList([1,2,3])
print(len(lst))  # 输出3

-  __add__(self, other) ： 对象1 + 对象2 时调用，实现对象加法；
- 案例：
python

class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    def __add__(self, other):
        return Point(self.x + other.x, self.y + other.y)
p1 = Point(1,2)
p2 = Point(3,4)
p3 = p1 + p2
print(p3.x, p3.y)  # 输出4 6


第7章 字符串操作

7.1 字符串基础

- 字符串定义：字符序列，用 '' 、 "" 或 """ 包裹（ """ 支持多行字符串）；
- 案例： s1 = 'hello' 、 s2 = "Python" 、 s3 = """第一行 第二行""" 。
- 转义字符：
- 常用转义字符： \n （换行）、 \t （制表符，占4个空格）、 \\ （转义为 \ ）、 \' （转义为 ' ）、 \" （转义为 " ）、 \r （回车）；
- 原始字符串：在字符串前加 r ，转义字符失效（如 r"C:\Users\test" ，无需写 \\ ）。
- 字符串编码与解码：
- 编码（str→bytes）： s.encode(encoding='utf-8') （如 "中文".encode('utf-8') ，返回 b'\xe4\xb8\xad\xe6\x96\x87' ）；
- 解码（bytes→str）： b.decode(encoding='utf-8') （如 b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8') ，返回 "中文" ）；
- 注意：编码与解码的字符集必须一致（如utf-8编码需用utf-8解码），否则报错。

7.2 字符串常用操作（拼接、重复、切片、遍历）

- 拼接： + 运算符（ s1 + s2 ， "hello" + "Python"="helloPython" ）；
- 重复： * 运算符（ s * n ， "ab"*3="ababab" ）；
- 切片（与列表切片一致）： s[start:end:step] ；
- 案例： s = "Python"; s[1:4]="yth"; s[::-1]="nohtyP" （反转字符串）；
- 遍历：
- for循环遍历字符： for char in s: print(char) ；
- 枚举遍历（含索引）： for index, char in enumerate(s): print(index, char) 。

7.3 字符串常用方法（重点）

- 查找与替换：
-  find(sub, start=0, end=len(s)) ：查找子串sub的第一个位置，未找到返回-1（ "Python".find("yth")=1 ）；
-  index(sub, start=0, end=len(s)) ：查找子串sub的第一个位置，未找到报错；
-  replace(old, new, count=-1) ：替换子串（count为替换次数，默认全部替换， "abac".replace("a","x")="xbxc" ）；
-  rfind(sub) ：从右往左查找子串的第一个位置。
- 分割与拼接：
-  split(sep=None, maxsplit=-1) ：按sep分割字符串，返回列表（sep默认分割所有空白字符， "a b c".split()=["a","b","c"] ； "a,b,c".split(",")=["a","b","c"] ）；
-  rsplit(sep=None, maxsplit=-1) ：从右往左分割；
-  splitlines(keepends=False) ：按换行符分割（ "a\nb\nc".splitlines()=["a","b","c"] ）；
-  join(iterable) ：用字符串拼接可迭代对象的元素（ "-".join(["a","b","c"])="a-b-c" ，常用）。
- 大小写转换：
-  upper() ：转大写（ "Python".upper()="PYTHON" ）；
-  lower() ：转小写（ "PYTHON".lower()="python" ）；
-  capitalize() ：首字母大写，其余小写（ "python".capitalize()="Python" ）；
-  title() ：每个单词首字母大写（ "python programming".title()="Python Programming" ）。
- 去除空白字符：
-  strip(chars=None) ：去除字符串首尾的空白字符（默认）或指定字符（ "  abc  ".strip()="abc" ； "aabcca".strip("a")="bcc" ）；
-  lstrip(chars=None) ：去除左侧空白字符或指定字符；
-  rstrip(chars=None) ：去除右侧空白字符或指定字符。
- 判断类方法（返回bool值）：
-  isalpha() ：是否全为字母（ "Python".isalpha()=True ； "Python123".isalpha()=False ）；
-  isdigit() ：是否全为数字（ "123".isdigit()=True ； "123a".isdigit()=False ）；
-  isalnum() ：是否全为字母或数字（ "Python123".isalnum()=True ）；
-  isspace() ：是否全为空白字符（ "   \t\n".isspace()=True ）；
-  startswith(prefix, start=0, end=len(s)) ：是否以prefix开头（ "Python".startswith("Py")=True ）；
-  endswith(suffix, start=0, end=len(s)) ：是否以suffix结尾（ "Python".endswith("on")=True ）。
- 其他常用方法：
-  count(sub, start=0, end=len(s)) ：统计子串sub出现的次数（ "abac".count("a")=2 ）；
-  center(width, fillchar=' ') ：居中对齐，填充字符fillchar（ "Python".center(10, "*")="**Python**" ）；
-  ljust(width, fillchar=' ') ：左对齐；
-  rjust(width, fillchar=' ') ：右对齐；
-  zfill(width) ：左侧填充0，使字符串长度为width（ "123".zfill(5)="00123" ）。

7.4 字符串格式化输出（3种方式）

- %占位符方式（传统）：
- 语法： "格式字符串" % (值1, 值2, ...) ；
- 常用占位符： %s （字符串）、 %d （整数）、 %f （浮点数）、 %x （十六进制整数）；
- 案例： "姓名：%s，年龄：%d，成绩：%.2f" % ("张三",20,95.5) （输出“姓名：张三，年龄：20，成绩：95.50”）；
- 说明： %.2f 表示保留2位小数。
- format()函数方式（灵活）：
- 位置格式化： "姓名：{}，年龄：{}".format("张三",20) ；
- 关键字格式化： "姓名：{name}，年龄：{age}".format(name="张三", age=20) ；
- 索引格式化： "姓名：{0}，年龄：{1}，再次姓名：{0}".format("张三",20) ；
- 格式说明： "{:.2f}".format(95.5) （保留2位小数）、 "{:05d}".format(123) （填充0至5位）、 "{:,}".format(1000000) （千分位分隔）。
- f-string方式（Python 3.6+，推荐）：
- 语法： f"字符串{变量/表达式}" ；
- 案例： name="张三"; age=20; f"姓名：{name}，年龄：{age}，明年{age+1}岁" ；
- 格式说明： f"成绩：{95.5:.2f}" （保留2位小数）、 f"数字：{123:05d}" （填充0至5位）；
- 优势：简洁、直观、效率高，支持直接嵌入变量和表达式。

第8章 正则表达式

8.1 正则表达式基础（元字符、量词、字符集）

- 元字符（具有特殊含义的字符）：
-  . ：匹配任意单个字符（除换行符 \n ）；
-  ^ ：匹配字符串开头（ ^abc 匹配以“abc”开头的字符串）；
-  $ ：匹配字符串结尾（ abc$ 匹配以“abc”结尾的字符串）；
-  * ：匹配前面的子表达式0次或多次（ ab*c 匹配“ac”、“abc”、“abbc”等）；
-  + ：匹配前面的子表达式1次或多次（ ab+c 匹配“abc”、“abbc”等，不匹配“ac”）；
-  ? ：匹配前面的子表达式0次或1次（ ab?c 匹配“ac”、“abc”）；
-  () ：分组，将括号内的内容视为一个整体（ (ab)+ 匹配“ab”、“abab”等）；
-  | ：或，匹配左右任意一个子表达式（ a|b 匹配“a”或“b”）；
-  \ ：转义字符，将元字符转为普通字符（ \. 匹配“.”， \* 匹配“*”）。
- 转义序列（常用）：
-  \d ：匹配任意数字（等价于 [0-9] ）；
-  \D ：匹配任意非数字（等价于 [^0-9] ）；
-  \w ：匹配任意字母、数字、下划线（等价于 [a-zA-Z0-9_] ）；
-  \W ：匹配任意非字母、数字、下划线（等价于 [^a-zA-Z0-9_] ）；
-  \s ：匹配任意空白字符（空格、制表符 \t 、换行符 \n 等，等价于 [ \t\n\r\f] ）；
-  \S ：匹配任意非空白字符；
-  \b ：匹配单词边界（如 \babc\b 匹配独立的“abc”单词，不匹配“abcd”或“xabc”）；
-  \B ：匹配非单词边界。
- 字符集（ [] ，匹配任意一个括号内的字符）：
-  [abc] ：匹配“a”、“b”或“c”；
-  [a-z] ：匹配任意小写字母；
-  [A-Z] ：匹配任意大写字母；
-  [0-9] ：匹配任意数字；
-  [^abc] ：匹配除“a”、“b”、“c”外的任意字符（^在字符集内表示“非”）；
-  [a-zA-Z0-9] ：匹配任意字母或数字（等价于 \w ，不含下划线）。
- 量词（指定匹配次数）：
-  {n} ：匹配前面的子表达式恰好n次（ a{3} 匹配“aaa”）；
-  {n,} ：匹配前面的子表达式至少n次（ a{2,} 匹配“aa”、“aaa”等）；
-  {n,m} ：匹配前面的子表达式n至m次（ a{2,4} 匹配“aa”、“aaa”、“aaaa”）；
- 贪婪匹配vs非贪婪匹配：默认贪婪（尽可能多匹配），量词后加 ? 为非贪婪（尽可能少匹配）；
- 案例： "aaaaa".match("a+") 匹配所有“a”（贪婪）， "aaaaa".match("a+?") 匹配1个“a”（非贪婪）。

8.2 re模块核心函数（重点）

- re.match(pattern, string, flags=0)：
- 功能：从字符串开头匹配模式，成功返回匹配对象（Match object），失败返回None；
- 案例：
python

import re
result = re.match(r"(\d{3})-(\d{8})", "010-12345678")
if result:
    print(result.group())  # 输出匹配的整个字符串："010-12345678"
    print(result.group(1))  # 输出第1个分组："010"
    print(result.group(2))  # 输出第2个分组："12345678"

- re.search(pattern, string, flags=0)：
- 功能：在字符串任意位置匹配模式，成功返回匹配对象，失败返回None（与match的区别：不局限于开头）；
- 案例： re.search(r"\d+", "abc123def") 匹配“123”。
- re.findall(pattern, string, flags=0)：
- 功能：匹配字符串中所有符合模式的子串，返回列表（无匹配返回空列表）；
- 案例： re.findall(r"\d+", "abc123def456") 返回 ["123", "456"] 。
- re.sub(pattern, repl, string, count=0, flags=0)：
- 功能：替换字符串中符合模式的子串，count为替换次数（0表示全部替换），返回替换后的字符串；
- 案例： re.sub(r"\d+", "数字", "abc123def456") 返回 "abc数字def数字" 。
- re.split(pattern, string, maxsplit=0, flags=0)：
- 功能：按匹配模式分割字符串，返回列表；
- 案例： re.split(r"[,;]", "a,b;c") 返回 ["a", "b", "c"] 。
- 匹配对象（Match object）常用方法：
-  group(num=0) ：返回匹配的子串（num=0返回整个匹配，num>0返回第num个分组）；
-  groups() ：返回所有分组的元组（ result.groups() 返回 ("010", "12345678") ）；
-  start() ：返回匹配子串的起始索引；
-  end() ：返回匹配子串的结束索引；
-  span() ：返回匹配子串的索引范围（ (start, end) ）。

8.3 正则表达式实战案例

- 案例1：匹配手机号（11位数字，以13/14/15/17/18/19开头）：
python

pattern = r"^1[345789]\d{9}$"
print(re.match(pattern, "13812345678"))  # 匹配成功
print(re.match(pattern, "12345678901"))  # 匹配失败（开头不是13/14等）

- 案例2：匹配邮箱（用户名@域名，域名含.）：
python

pattern = r"^[a-zA-Z0-9_-]+@[a-zA-Z0-9_-]+\.[a-zA-Z]{2,}$"
print(re.match(pattern, "test123@qq.com"))  # 匹配成功
print(re.match(pattern, "test@.com"))  # 匹配失败（域名不合法）

- 案例3：匹配身份证号（18位，最后一位可为X/x）：
python

pattern = r"^[1-9]\d{16}[\dXx]$"
print(re.match(pattern, "110101199001011234"))  # 匹配成功
print(re.match(pattern, "11010119900101123X"))  # 匹配成功

- 案例4：提取HTML标签中的内容（如 <title>Python教程</title> 提取“Python教程”）：
python

html = "<title>Python教程</title>"
pattern = r"<title>(.*?)</title>"  # 非贪婪匹配，避免多标签时匹配过度
result = re.search(pattern, html)
print(result.group(1))  # 输出"Python教程"

- 案例5：去除字符串中的所有空白字符：
python

s = "  Python  编程  \n  教程  "
result = re.sub(r"\s+", "", s)
print(result)  # 输出"Python编程教程"


以下是董付国《Python程序设计基础（第3版·微课版）》第9-13章超详细知识点拆解，覆盖核心语法、实操细节、函数参数与典型案例，适配深度学习与实战应用：

第9章 文件内容操作

9.1文件基础操作

- 文件打开（ open() 函数）：
- 核心参数：
-  file ：文件路径（绝对路径如 "C:/test.txt" ，相对路径如 "test.txt" ）；
-  mode ：打开模式（文本模式 r/r+/w/w+/a/a+ ，二进制模式 rb/wb/ab ）；
-  encoding ：文本文件编码（如 utf-8 、 gbk ，二进制文件无需指定）；
-  errors ：编码错误处理（ ignore 忽略、 replace 替换错误字符）。
- 模式详解：
模式 功能 特性 
 r  只读 文件不存在报错，指针在文件开头 
 r+  读写 不创建新文件，写入覆盖原有内容 
 w  只写 文件不存在则创建，存在则清空内容 
 w+  读写 强制创建新文件，清空原有内容 
 a  追加 文件不存在则创建，写入在末尾追加 
 a+  追加+读 追加模式，读需移动指针（ f.seek(0) ） 
- 关闭文件： f.close() （必须关闭释放资源），推荐 with 语句自动关闭：
python

with open("test.txt", "r", encoding="utf-8") as f:
    content = f.read()  # 缩进内操作文件，退出自动关闭


9.2 文本文件读写

- 读取方法：
-  read(size=-1) ：读取全部内容（ size 指定字节数，-1为全部），如 f.read(100) 读取前100字节；
-  readline(size=-1) ：读取一行，包括换行符 \n ，如 f.readline() 读取第一行；
-  readlines(hint=-1) ：读取所有行，返回列表（每行为元素），如 lines = f.readlines() ；
- 逐行遍历（高效省内存）： for line in f: print(line.strip()) （去除换行符）。
- 写入方法：
-  write(string) ：写入字符串，返回写入字节数，如 f.write("Hello Python\n") ；
-  writelines(iterable) ：写入字符串序列（列表/元组），如 f.writelines(["第一行\n", "第二行\n"]) ；
- 注意：写入后需 f.flush() 刷新缓冲区，或关闭文件，内容才会写入磁盘。

9.3二进制文件操作

- 打开模式： rb （只读）、 wb （只写）、 ab （追加），无需指定 encoding ；
- 读写操作：
- 读取： data = f.read() （返回字节流 bytes 类型）；
- 写入： f.write(data) （需传入 bytes 类型）；
- 案例（复制图片）：
python

with open("source.jpg", "rb") as f1, open("copy.jpg", "wb") as f2:
    f2.write(f1.read())  # 字节流直接读写


9.4序列化与反序列化

- json模块（通用格式，支持跨语言）：
- 序列化（对象→JSON文件）： json.dump(obj, fp, ensure_ascii=False, indent=2) ；
python

import json
data = {"name": "张三", "age": 20}
with open("data.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)  # 中文不转义，缩进2空格

- 反序列化（JSON文件→对象）： obj = json.load(fp) ；
python

with open("data.json", "r", encoding="utf-8") as f:
    data = json.load(f)  # 字典类型：{"name": "张三", "age": 20}

- 支持类型： int/float/str/list/tuple/dict/None ，不支持 set 、自定义对象。
- pickle模块（Python专属，支持所有对象）：
- 序列化： pickle.dump(obj, fp) ；
- 反序列化： obj = pickle.load(fp) ；
- 案例（保存自定义对象）：
python

import pickle
class Person:
    def __init__(self, name):
        self.name = name
p = Person("李四")
with open("person.pkl", "wb") as f:
    pickle.dump(p, f)  # 保存对象
with open("person.pkl", "rb") as f:
    p2 = pickle.load(f)  # 恢复对象，可调用p2.name


9.5办公文件操作

- Word文件（python-docx库）：
- 安装： pip install python-docx ；
- 核心操作：
python

from docx import Document
doc = Document()  # 创建新文档
doc.add_heading("标题", level=1)  # 添加标题
doc.add_paragraph("正文内容")  # 添加段落
doc.add_table(rows=3, cols=2)  # 添加3行2列表格
doc.save("test.docx")  # 保存

- Excel文件（openpyxl库）：
- 安装： pip install openpyxl ；
- 核心操作：
python

from openpyxl import Workbook
wb = Workbook()  # 创建工作簿
ws = wb.active  # 获取活跃工作表
ws["A1"] = "姓名"  # 写入单元格
ws["B1"] = "年龄"
ws.append(["张三", 20])  # 追加行
wb.save("test.xlsx")  # 保存


第10章 文件与文件夹操作

10.1 os模块核心功能

- 目录操作：
-  os.getcwd() ：获取当前工作目录，如 print(os.getcwd()) ；
-  os.chdir(path) ：切换工作目录，如 os.chdir("C:/Users") ；
-  os.listdir(path=".") ：列出目录内容（文件+子目录），返回列表，如 os.listdir("test") ；
-  os.mkdir(path) ：创建单层文件夹，如 os.mkdir("new_dir") （父目录不存在报错）；
-  os.makedirs(path) ：递归创建多层文件夹，如 os.makedirs("a/b/c") ；
-  os.rmdir(path) ：删除空文件夹，如 os.rmdir("new_dir") （非空报错）；
-  os.removedirs(path) ：递归删除空文件夹，如 os.removedirs("a/b/c") （仅删除空目录）。
- 文件操作：
-  os.remove(path) ：删除文件，如 os.remove("test.txt") ；
-  os.rename(src, dst) ：重命名文件/文件夹，如 os.rename("old.txt", "new.txt") 。

10.2 os.path模块路径处理

- 路径判断：
-  os.path.exists(path) ：判断路径是否存在（文件/文件夹）；
-  os.path.isfile(path) ：判断是否为文件；
-  os.path.isdir(path) ：判断是否为文件夹；
-  os.path.isabs(path) ：判断是否为绝对路径。
- 路径操作：
-  os.path.join(path1, path2, ...) ：拼接路径（自动适配系统分隔符），如 os.path.join("a", "b", "test.txt") ；
-  os.path.abspath(path) ：转换为绝对路径，如 os.path.abspath("test.txt") ；
-  os.path.basename(path) ：获取文件名（含后缀），如 os.path.basename("a/b/test.txt")→"test.txt" ；
-  os.path.dirname(path) ：获取目录名，如 os.path.dirname("a/b/test.txt")→"a/b" ；
-  os.path.getsize(path) ：获取文件大小（字节），如 os.path.getsize("test.txt") 。

10.3 shutil模块高级操作

- 文件复制：
-  shutil.copy(src, dst) ：复制文件（保留权限，不复制元数据），如 shutil.copy("a.txt", "b.txt") ；
-  shutil.copy2(src, dst) ：复制文件+元数据（创建时间、修改时间）；
-  shutil.copytree(src, dst) ：递归复制文件夹，如 shutil.copytree("old_dir", "new_dir") 。
- 文件移动/重命名：
-  shutil.move(src, dst) ：移动文件/文件夹，如 shutil.move("a.txt", "dir/b.txt") （跨磁盘则复制后删除原文件）。
- 文件夹删除：
-  shutil.rmtree(path) ：递归删除文件夹（含所有文件/子目录），如 shutil.rmtree("old_dir") （慎用，不可逆）。

10.4目录遍历

-  os.walk(top) ：递归遍历目录树，返回生成器（ root, dirs, files ）：
-  root ：当前目录路径；
-  dirs ：当前目录下的子目录列表；
-  files ：当前目录下的文件列表；
- 案例（遍历所有文件）：
python

import os
for root, dirs, files in os.walk("test_dir"):
    for file in files:
        file_path = os.path.join(root, file)
        print(f"文件路径：{file_path}")


第11章 异常处理结构

11.1常见异常类型

异常类型 触发场景 
 SyntaxError  语法错误（如缺少冒号、缩进错误） 
 TypeError  类型错误（如字符串+数字） 
 ValueError  值错误（如 int("abc") ） 
 FileNotFoundError  文件未找到（如打开不存在的文件） 
 KeyError  字典键不存在（如 dict["none_key"] ） 
 IndexError  索引越界（如 list[10] ，列表仅5个元素） 
 ZeroDivisionError  除零错误（如 1/0 ） 

11.2异常处理结构

- 基础结构（ try-except ）：
- 捕获指定异常：
python

try:
    1 / 0  # 可能触发异常的代码
except ZeroDivisionError:
    print("除零错误！")  # 异常触发后执行

- 捕获多个异常：
python

try:
    lst = [1,2,3]
    print(lst[10])
except IndexError:
    print("索引越界")
except TypeError:
    print("类型错误")

- 捕获所有异常（不推荐，难以排查问题）：
python

try:
    # 代码
except Exception as e:  # 捕获所有非系统退出异常
    print(f"异常信息：{e}")  # 打印异常详情

- 扩展结构（ try-except-else ）：无异常时执行 else ：
python

try:
    result = 1 + 2
except Exception:
    print("异常")
else:
    print(f"结果：{result}")  # 无异常执行，输出"结果：3"

- 最终结构（ try-finally ）：无论是否异常， finally 必执行（释放资源）：
python

f = None
try:
    f = open("test.txt", "r")
    content = f.read()
except FileNotFoundError:
    print("文件未找到")
finally:
    if f:
        f.close()  # 确保文件关闭


11.3异常进阶

- 自定义异常：继承 Exception 类：
python

class MyError(Exception):  # 自定义异常类
    def __init__(self, message):
self.message = message
try:
    raise MyError("自定义异常触发")  # 主动抛出异常
except MyError as e:
    print(e.message)  # 输出"自定义异常触发"

- 异常链（ from 关键字）：关联异常因果：
python

try:
    1 / 0
except ZeroDivisionError as e:
    raise ValueError("计算错误") from e  # 新异常关联原异常


第12章 SQLite数据库操作

12.1数据库基础

- SQLite特性：轻量级、文件型数据库（无需单独安装服务）、支持标准SQL、Python内置 sqlite3 模块。
- 连接数据库： sqlite3.connect(database) ，如：
python

import sqlite3
conn = sqlite3.connect("test.db")  # 不存在则创建数据库文件
cursor = conn.cursor()  # 创建游标（执行SQL语句）


12.2核心操作流程

1. 创建数据表（ CREATE TABLE ）：
python

# 创建学生表（id为主键自增，姓名、年龄、成绩）
cursor.execute('''
    CREATE TABLE IF NOT EXISTS students (
        id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL,
        age INTEGER,
        score REAL
    )
''')
conn.commit()  # 提交事务（创建/修改表需提交）

2. 插入数据（ INSERT ）：
- 单条插入：
python

cursor.execute("INSERT INTO students (name, age, score) VALUES (?, ?, ?)", ("张三", 20, 90.5))
conn.commit()

- 多条插入（ executemany ）：
python

data = [("李四", 19, 85.0), ("王五", 21, 92.3)]
cursor.executemany("INSERT INTO students VALUES (NULL, ?, ?, ?)", data)
conn.commit()

- 注意：用 ? 占位符，避免SQL注入（勿用字符串拼接）。
3. 查询数据（ SELECT ）：
-  fetchone() ：获取一条结果（元组）：
python

cursor.execute("SELECT * FROM students WHERE age < 20")
print(cursor.fetchone())  # 输出("李四", 19, 85.0)

-  fetchall() ：获取所有结果（列表嵌套元组）：
python

cursor.execute("SELECT name, score FROM students ORDER BY score DESC")
print(cursor.fetchall())  # 输出[("王五", 92.3), ("张三", 90.5), ("李四", 85.0)]

- 逐行遍历：
python

cursor.execute("SELECT * FROM students")
for row in cursor:
    print(f"ID: {row[0]}, 姓名: {row[1]}")

4. 更新数据（ UPDATE ）：
python

cursor.execute("UPDATE students SET score = ? WHERE name = ?", (88.0, "李四"))
conn.commit()

5. 删除数据（ DELETE ）：
python

cursor.execute("DELETE FROM students WHERE age > 21")
conn.commit()

6. 关闭资源：
python

cursor.close()  # 关闭游标
conn.close()    # 关闭连接


12.3事务处理

- 提交事务： conn.commit() （插入/更新/删除后必须提交，否则修改无效）；
- 回滚事务： conn.rollback() （异常时回滚，撤销未提交的修改）；
- 案例（事务安全）：
python

try:
    cursor.execute("INSERT INTO students VALUES (NULL, '赵六', 22, 89.0)")
conn.commit()
except Exception as e:
    conn.rollback()  # 出错回滚
    print(f"插入失败：{e}")


第13章 数据处理与可视化

13.1 NumPy库（科学计算基础）

- 安装： pip install numpy ，导入： import numpy as np 。
- 数组创建：
-  np.array() ：从列表/元组创建，如 arr = np.array([1,2,3,4]) （一维数组）、 arr2 = np.array([[1,2],[3,4]]) （二维数组）；
- 特殊数组： np.zeros((3,2)) （3行2列全0）、 np.ones((2,2)) （全1）、 np.arange(0,10,2) （0-10步长2： [0,2,4,6,8] ）、 np.linspace(0,1,5) （0-1均分5个值）。
- 数组属性：
-  arr.shape ：数组形状（行数, 列数），如 arr2.shape→(2,2) ；
-  arr.dtype ：数据类型，如 arr.dtype→dtype('int64') ；
-  arr.size ：元素总数，如 arr2.size→4 。
- 索引与切片：
- 一维数组： arr[0]→1 、 arr[1:3]→[2,3] ；
- 二维数组： arr2[0,1]→2 （第0行第1列）、 arr2[:,0]→[1,3] （第0列所有行）。
- 数值运算：
- 元素级运算： arr + 2 （所有元素+2）、 arr * 3 （所有元素×3）、 arr1 + arr2 （对应元素相加）；
- 矩阵运算： arr2 @ arr2 （矩阵乘法）、 np.dot(arr2, arr2) ；
- 统计函数： arr.mean() （平均值）、 arr.sum() （求和）、 arr.std() （标准差）、 arr.max() （最大值）、 arr.min() （最小值）。

13.2 Pandas库（数据处理核心）

- 安装： pip install pandas ，导入： import pandas as pd 。
- 数据结构：
-  Series （一维序列）：
python

s = pd.Series([10,20,30], index=["a","b","c"])  # 索引可自定义
print(s["a"])  # 输出10

-  DataFrame （二维表格）：
python

data = {"姓名": ["张三", "李四", "王五"], "年龄": [20,19,21], "成绩": [90.5,85.0,92.3]}
df = pd.DataFrame(data)  # 自动生成行索引（0,1,2）
print(df)

- 数据读取：
- 读取CSV： df = pd.read_csv("data.csv", encoding="utf-8") ；
- 读取Excel： df = pd.read_excel("data.xlsx", sheet_name="Sheet1") 。
- 数据清洗：
- 查看缺失值： df.isnull().sum() （统计每列缺失值个数）；
- 删除缺失值： df.dropna() （删除含缺失值的行）、 df.dropna(axis=1) （删除列）；
- 填充缺失值： df.fillna(value=0) （用0填充）、 df["年龄"].fillna(df["年龄"].mean()) （用平均值填充）；
- 去重： df.drop_duplicates() （删除重复行）；
- 数据类型转换： df["年龄"] = df["年龄"].astype(int) （转为整数型）。
- 数据筛选与分组：
- 条件筛选： df[df["成绩"] > 90] （筛选成绩>90的行）；
- 列选择： df[["姓名", "成绩"]] （选择指定列）；
- 行索引选择： df.loc[0:2] （按标签索引）、 df.iloc[0:2] （按位置索引）；
- 分组统计： df.groupby("性别")["成绩"].mean() （按性别分组，计算成绩平均值）。

13.3 Matplotlib库（数据可视化）

- 安装： pip install matplotlib ，导入： import matplotlib.pyplot as plt 。
- 基础配置（中文显示）：
python

plt.rcParams['font.sans-serif'] = ['SimHei']  # Windows：黑体
plt.rcParams['axes.unicode_minus'] = False  # 正常显示负号

- 常用图表：
- 折线图（ plot() ）：
python

x = [1,2,3,4,5]
y = [10,20,15,25,22]
plt.plot(x, y, marker='o', color='red', label='销量')  # marker标记点
plt.xlabel("月份")
plt.ylabel("销量")
plt.title("月度销量趋势图")
plt.legend()  # 显示图例
plt.grid(True, alpha=0.3)  # 显示网格
plt.show()

- 柱状图（ bar() ）：
python

x = ["A产品", "B产品", "C产品"]
y = [50, 30, 45]
plt.bar(x, y, color=['blue', 'green', 'orange'])
plt.xlabel("产品类型")
plt.ylabel("销售额（万元）")
plt.title("产品销售额对比")
plt.show()

- 饼图（ pie() ）：
python

labels = ["语文", "数学", "英语", "物理"]
sizes = [85, 92, 78, 88]
plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=90)
plt.axis('equal')  # 正圆形
plt.title("科目成绩占比")
plt.show()

- 散点图（ scatter() ）：
python

x = np.random.rand(50)
y = np.random.rand(50)
plt.scatter(x, y, c='red', alpha=0.6)  # alpha透明度
plt.xlabel("X")
plt.ylabel("Y")
plt.title("散点图")
plt.show()

- 图表保存： plt.savefig("chart.png", dpi=300, bbox_inches="tight") （高分辨率保存）。



