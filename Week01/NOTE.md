学习笔记
a first day to learn python again
what I have learnt:
git的简单使用：
git --version
git init
git config --global user.name "" 
git config --global user.email ""
查阅过global，system，local的区别，已经忘了；
git status
git add 文件名；git add . 添加所有文件；
git commit -m "注释内容 越详细越好" 提交更改
git log 查看所有修改

python环境：
venv虚拟环境
开发环境，生产环境--- 不要装多个版本的python解释器，不然会很烦。。
把更改路径放到配置文件里，sudo vim /etc/profile 管理员模式；python2不要删，因为有很多系统相关的脚本
查看第三方库都装在哪个版本的python里了， .../3.7/lib/3.7/site-packages

更改pip安装源之后，安装包安装可以加快；

一些IDE：例如古老而重量级的pycharm，轻量级的VScode，jupyter notebook，
VScode里rainfart 括号；option+shift+f格式化代码；
option comman ⬆️  开头；反之到结尾，⬅️  到当前开头，反之当前结尾
option ⬆️  ⬇️  上下行调换
断点
F5 启动调试；F11逐行调试
command / 注释

.pyc 保存目标代码 # 这个我不是很懂

第三方库也要迁移：
python 版区别查看：python -V；pip3 -V 查看pip版本，便于环境freeze等
如何更改使用的python版本路径，$PATH：原来的各个版本的python版本路径，更改 export PATH = 想要用的python的版本的路径$PATH
创建虚拟环境：python3 -m venv venv1
激活虚拟环境：source venv1/bin/activate
退出虚拟环境：deactivate

进入venv1:
pip3 freeze 查看有哪些包安装了的
pip3 freeze > requirements.txt
退出venv1
进入venv2 用pip3 freeze 查看安装了什么
which python3 版本是否跟venv1的版本一致
pip3 -V 版本是否跟venv1的一致
pip3 insatll -r ./requirements.txt

python 基础知识：
数据类型：None, Bool,数值，序列（字符串，列表，元组），集合（字典），可调用的（函数）
字符串，列表，元组，字典的内置方法，全部看了一下；
import this可以看到python之禅
高级数据类型：了解了collections里的deque和counter，就是封装了一下，可以更加灵活地使用方法，deque是列表的子类，counter是字典的子类，很好使用，计算最常见的值什么的。。

控制流：就是if，for，while这样的循环； break，continue可以用；for比while更加pythonic；

函数跟模块的区别：模块包含多个函数。。。
常见模块：
time
datetime
logging 日志记录
random 获得随机数之类的
json 特定格式保存
pathlib 比os.path更新一些
os.path

【dander name：__name__ python运行的时候，系统会自定义一些特殊的变量和属性，用前后双下划线包括进来，会随运行环境而改变，在模块里加 if __name__ = "__main__" 可以防止运行两次，被调用也行，自己是个函数调用也行】

常见模块：
time 
time.time() 当前秒数
time.strftime("%Y-%m-%d %X", time.localtiem()) 格式化时间表示
time.strptime(...)
时间偏移，可以用datetime模块来表示，这个模块封装了time
from datetime import *
timedelta(days=1, seconds...) 可以查看官方文档使用

logging 日志模块
可以用在多线程的应用程序中，自己可以定义各种程度什么的；
级别：debug,info,warning,error,critical, 默认warning及以上才会输出，【这些参数我还不是很懂】【练习的时候发现，路径上错了好久，要记得输绝对路径】

random 伪随机模块，因为是基于当前的时间戳的随机 0-1.0
randomrange(0,101,2) [0,100]的偶数随便选一个
choice（["red","green","yellow","web","xz","turtle"]） 随机挑选一个
sample([1,2,3,4,5,6], k=3) 随机挑选3（k）个

json数据格式整理，不是很懂怎么处理，还没有查
json.loads()
json.dumps()


pathlib 路径库
from pathlib import Path
p=Path() 实例化当前路径
p.resolve() 显示当前完整路径；
path = "user/local/a.txt.py"
p=Path(path)
p.name --- a.txt.py
p.stem --- a.txt
p.suffix --- 
p.suffixes 
.tar.gz  .tar.bz2 双扩展名
p.parent --- 路径名
p.parents -- 可迭代对象 例如：for i in p.parents: print(i)
p.parts() --- 元组形式显示各个部分

os.path 比较老，看懂即可
import os
os.oath.abspath('test.log")
path = ...
oa,path.basename(path)
os.path.dirname(path)
os.path.exists('/etc/passwd') 文件是否存在
os.path.isdir("..")
os.path.isfile("...")
os.path.join("a","b")


daemon进程，手动实现进程守护，没有用户信息，开机即可启动；不会随着终端的关闭而关闭
标准库os.fork() 创建子进程，我不是很懂，以后再弄明白吧
ps -ef | grep daemon1 可以查看进程，前面那串数字是进程名
输入输出路径，还是要注意一下
kill -9 进程名
tail -f d1.log 查看文件的末尾

正则表达式 re库
文档要通读，我还没有通读，找个时间吧，嗯
应用：提取子串；在有规律的文本中查找分析字符串；字符串替换
元字符
模块内容，这个章节也要看！
需要多次使用这个正则pattern的时候可以用re.compile()
有很多的常量，需要背诵；
函数，先掌握这五个，match search findall sub split
re.match(pattern,content ).group()
re.match(  ).group(1)

re.search( , )	找到第一个
re,findall( ) 找到所有
re.sub("old", "new", content) 
re.sub("\d", "$ ", content) 每个数字都变成$
re.sub("\d+", $, content) 那一串数字变成$




以上是第一周的学习，加油呀爸爸！













