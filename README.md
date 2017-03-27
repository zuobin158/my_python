# 熟悉Linux操作系统，并能基于Linux平台完成日常开发工作
# 熟练部署和使用Nginx/Mysql/Redis等应用
# 精通python语言，熟悉shell脚本
# 熟悉Backbonejs，bootstrap
# 掌握python web框架，tornado、flask、django
# 有云平台开发经验
# 熟悉Openstack或参与过开发
# 熟悉搜索、推荐系统设计或者推荐策略
# 对数据结构、算法设计和设计模式有较为深刻的理解
# 熟悉redis、memcached、mongodb、elasticsearch
# 熟练使用git、jira、confluence
# 熟悉TCP/IP等常用协议
# 熟悉以下关键词：Devops、Docker、Openstack、Puppet、CFengine、Saltstack、Ansible、etcd、confd
# 熟悉高级消息管理协议、RabbitMQ、Kafka
# 熟悉python异步编程，gevent、tornado
# 熟悉Nosql数据库
# 服务开发经验，熟悉Thrift、Protocol Buffers
# 熟悉云计算iaas，paas，saas
#了解kvm、vmware、xen虚拟化技术、熟悉Qemu、Libvirt、openstack
# 熟悉Ceph、GlusterFS的架构与实现
# 熟悉常用的开源负载均衡软件，HAProxy、Nginx、LVS
# 了解OpenStack组件


python面试题--------------------
1.python多线程:
http://www.cnblogs.com/fnng/p/3670789.html
2.队列和栈：
http://www.jb51.net/article/59897.htm
3.什么是python装饰器 decorator，如何使用？
http://www.cnblogs.com/rhcad/archive/2011/12/21/2295507.html
4.你会如何​​设置很多项目，其中每一个使用Python的不同版本和第三方库？
用virtualenv
5.什么是PEP8和你是如何遵循它的规范？
pep8是python的编码规范，是大家约定的一种规范，用pylint或者在git上加钩子来检测python代码是否遵循pep8
6.参数是如何传递的 - 传值还是传引用？ （容易，但又不那么容易，不确定是否能清楚地回答这个问题） 
string，tuple，number是值传递，class，dict，list是引用传递
7.什么是列表解析、字典解析？举个例子
a=[x for x in range(101)if x%2==0]
列表解析底层使用c实现的，效率比写for循环高很多
8.你知道列表和元组之间的区别么？举个例子？
列表是一种数据结构，可以删除，增加等操作，元组是一个不可改变的结构，常用语定义常量，数据相对安全
9.range和xrange之间的区别
range返回一个list，xrange是迭代器，节省内存，用到时才返回。
10.python2.x和python3.x的区别
2x中print 不加括号，  3x中print必须加括号. xlwt包支持的编码不同
Py3.1性能比Py2.5慢15%，还有很大的提升空间
1）去除了<>，全部改用!=
2）去除``，全部改用repr()
3）关键词加入as 和with，还有True,False,None
4）整型除法返回浮点数，要得到整型结果，请使用//
5）加入nonlocal语句。使用noclocal x可以直接指派外围（非全局）变量
6）去除print语句，加入print()函数实现相同的功能。同样的还有 execl语句，已经改为exec()函数
   例如：
     2.X: print "The answer is", 2*2
     3.X: print("The answer is", 2*2)
     2.X: print x,                              # 使用逗号结尾禁止换行
     3.X: print(x, end=" ")                     # 使用空格代替换行
     2.X: print                                 # 输出新行
     3.X: print()                               # 输出新行
     2.X: print >>sys.stderr, "fatal error"
     3.X: print("fatal error", file=sys.stderr)
     2.X: print (x, y)                          # 输出repr((x, y))
     3.X: print((x, y))                         # 不同于print(x, y)!
7）改变了顺序操作符的行为，例如x<y，当x和y类型不匹配时抛出TypeError而不是返回随即的 bool值 
8）输入函数改变了，删除了raw_input，用input代替：
   2.X:guess = int(raw_input('Enter an integer : ')) # 读取键盘输入的方法
   3.X:guess = int(input('Enter an integer : '))
9）去除元组参数解包。不能def(a, (b, c)):pass这样定义函数了
10）新式的8进制字变量，相应地修改了oct()函数。
   2.X的方式如下：
     >>> 0666
     438
     >>> oct(438)
     '0666'
   3.X这样：
     >>> 0666
     SyntaxError: invalid token (<pyshell#63>, line 1)
     >>> 0o666
     438
     >>> oct(438)
     '0o666'
11）增加了 2进制字面量和bin()函数
    >>> bin(438)
    '0b110110110'
    >>> _438 = '0b110110110'
    >>> _438
    '0b110110110'
12）扩展的可迭代解包。在Py3.X 里，a, b, *rest = seq和 *rest, a = seq都是合法的，只要求两点：rest是list
对象和seq是可迭代的。
13）新的super()，可以不再给super()传参数，
    >>> class C(object):
          def __init__(self, a):
             print('C', a)
    >>> class D(C):
          def __init(self, a):
             super().__init__(a) # 无参数调用super()
    >>> D(8)
    C 8
    <__main__.D object at 0x00D7ED90>
14）新的metaclass语法：
    class Foo(*bases, **kwds):
      pass
15）支持class decorator。用法与函数decorator一样：
    >>> def foo(cls_a):
          def print_func(self):
             print('Hello, world!')
          cls_a.print = print_func
          return cls_a
    >>> @foo
    class C(object):
      pass
    >>> C().print()
    Hello, world!
class decorator可以用来玩玩狸猫换太子的大把戏。更多请参阅PEP 3129
4. 字符串和字节串
1）现在字符串只有str一种类型，但它跟2.x版本的unicode几乎一样。
2）关于字节串，请参阅“数据类型”的第2条目
5.数据类型
1）Py3.X去除了long类型，现在只有一种整型——int，但它的行为就像2.X版本的long
2）新增了bytes类型，对应于2.X版本的八位串，定义一个bytes字面量的方法如下：
    >>> b = b'china'
    >>> type(b)
    <type 'bytes'>
str对象和bytes对象可以使用.encode() (str -> bytes) or .decode() (bytes -> str)方法相互转化。
    >>> s = b.decode()
    >>> s
    'china'
    >>> b1 = s.encode()
    >>> b1
    b'china'
3）dict的.keys()、.items 和.values()方法返回迭代器，而之前的iterkeys()等函数都被废弃。同时去掉的还有
dict.has_key()，用 in替代它吧
6.面向对象
1）引入抽象基类（Abstraact Base Classes，ABCs）。
2）容器类和迭代器类被ABCs化，所以cellections模块里的类型比Py2.5多了很多。
    >>> import collections
    >>> print('\n'.join(dir(collections)))
    Callable
    Container
    Hashable
    ItemsView
    Iterable
    Iterator
    KeysView
    Mapping
    MappingView
    MutableMapping
    MutableSequence
    MutableSet
    NamedTuple
    Sequence
    Set
    Sized
    ValuesView
    __all__
    __builtins__
    __doc__
    __file__
    __name__
    _abcoll
    _itemgetter
    _sys
    defaultdict
    deque
另外，数值类型也被ABCs化。关于这两点，请参阅 PEP 3119和PEP 3141。
3）迭代器的next()方法改名为__next__()，并增加内置函数next()，用以调用迭代器的__next__()方法
4）增加了@abstractmethod和 @abstractproperty两个 decorator，编写抽象方法（属性）更加方便。
7.异常
1）所以异常都从 BaseException继承，并删除了StardardError
2）去除了异常类的序列行为和.message属性
3）用 raise Exception(args)代替 raise Exception, args语法
4）捕获异常的语法改变，引入了as关键字来标识异常实例，在Py2.5中：
    >>> try:
    ...    raise NotImplementedError('Error')
    ... except NotImplementedError, error:
    ...    print error.message
    ...
    Error
在Py3.0中：
    >>> try:
          raise NotImplementedError('Error')
        except NotImplementedError as error: #注意这个 as
          print(str(error))
    Error
5）异常链，因为__context__在3.0a1版本中没有实现
8.模块变动
1）移除了cPickle模块，可以使用pickle模块代替。最终我们将会有一个透明高效的模块。
2）移除了imageop模块
3）移除了 audiodev, Bastion, bsddb185, exceptions, linuxaudiodev, md5, MimeWriter, mimify, popen2, 
rexec, sets, sha, stringold, strop, sunaudiodev, timing和xmllib模块
4）移除了bsddb模块(单独发布，可以从http://www.jcea.es/programacion/pybsddb.htm获取)
5）移除了new模块
6）os.tmpnam()和os.tmpfile()函数被移动到tmpfile模块下
7）tokenize模块现在使用bytes工作。主要的入口点不再是generate_tokens，而是 tokenize.tokenize()
9.其它
1）xrange() 改名为range()，要想使用range()获得一个list，必须显式调用：
    >>> list(range(10))
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
2）bytes对象不能hash，也不支持 b.lower()、b.strip()和b.split()方法，但对于后两者可以使用 b.strip(b' 
\n\t\r \f')和b.split(b' ‘)来达到相同目的
3）zip()、map()和filter()都返回迭代器。而apply()、 callable()、coerce()、 execfile()、reduce()和reload
()函数都被去除了
现在可以使用hasattr()来替换 callable(). hasattr()的语法如：hasattr(string, '__name__')
4）string.letters和相关的.lowercase和.uppercase被去除，请改用string.ascii_letters 等
5）如果x < y的不能比较，抛出TypeError异常。2.x版本是返回伪随机布尔值的
6）__getslice__系列成员被废弃。a[i:j]根据上下文转换为a.__getitem__(slice(I, j))或 __setitem__和
__delitem__调用
7）file类被废弃，在Py2.5中：
    >>> file
    <type 'file'>
在Py3.X中：
    >>> file
    Traceback (most recent call last):
    File "<pyshell#120>", line 1, in <module>
       file
    NameError: name 'file' is not defined
11.with语句及其用法
with关键字是一个替你管理实现上下文协议对象的好东西,
def __enter__(self):
        '''
            with前置操作
        '''
        self.begin()
        return self

    def __exit__(self, exc_type, exc_val, exc_trace):
        '''
        with的后置操作，即with结束时调用该方法
        Args:
            exc_type:异常对象，如果在with中没有异常产生，exc_type是None
            exc_val:异常信息，即为异常中抛出的错误内容
            exc_trace:异常的堆栈对象
        '''
        if exc_type:
            self.rollback()
        else:
            try:
                self.commit()
            except:
                self.rollback()
                raise
12.如何避免对模块或方法的重复import？
用 import xxx as xxx1和import xxx as xxx2来区分
13.解读GIL
http://www.tuicool.com/articles/7zIra2r
14.什么是“特殊方法"（如<foo>）？它们如何工作的？
sdfsdf
15. yield是什么，怎么用？
http://www.cnblogs.com/tqsummer/archive/2010/12/27/1917927.html
16.redis的几种数据结构，怎么用？
string hash list set zset
17.lambda函数,map()函数,filter()函数,reduce()函数
http://www.jb51.net/article/54506.htm
函数式编程：http://www.cnblogs.com/huxi/archive/2011/06/18/2084316.html
18.Python中，如何读取大小为8GB的文件？(即python如何读取大文件) 
f = open('filename', 'rb')
f.read()一次性读取全部内容，加到内存
f.read(1024) 每次读取1024个字节
for i in f.readlines() 每次会返回一行的内容的列表，有风险
for i in f.readine() 每次读取一行，速度比readlines()慢
for i in f:  迭代器，返回当前一行，适用于比较大的文件读取
利用file的迭代器，我们可以这样写：
1
2
for line inopen("test.txt"):   #use file iterators
print line
19.不能借助内置方法如string.atoi或者int()，能否将ASCII字符转换为整数？
>>> print ord('A')
65
>>> print chr(65)
A
20.列表与元组的区别是什么.分别在什么情况下使用？
21.谈谈你用过的Python库？
pdb，requests，re，urllib，logging，threading,multiprocessing ,os/sys ,pickle,cvs,xlrd,xlwt,pymongo ,redis,collection
可以执行命令：
import pdb
pdb.set_srace()

直接回车是重复前一条命令！
p(print) 查看一个变量值 
n(next) 下一步
s(step) 单步,可进入函数
c(continue)继续前进
l(list)看源代码
22.Python是如何进行内存管理的？
http://www.cnblogs.com/CBDoctor/p/3781078.html
for i in range(100000)):                                                                                                             
              t = 'bl'+str(i) + '= "abcdeddddd"'
              exec(t)
23.对Python中装饰器的认识？
sdaf
24.用户登录和鉴权流程
http://blog.csdn.net/xiaoxian8023/article/details/38114921
http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html
用户访问客户端的网站，想操作用户存放在服务提供方的资源。
客户端向服务提供方请求一个临时令牌。
服务提供方验证客户端的身份后，授予一个临时令牌。
客户端获得临时令牌后，将用户引导至服务提供方的授权页面请求用户授权。在这个过程中将临时令牌和客户端的回调连接发送给服务提供方。
用户在服务提供方的网页上输入用户名和密码，然后授权该客户端访问所请求的资源。
授权成功后，服务提供方引导用户返回客户端的网页。
客户端根据临时令牌从服务提供方那里获取访问令牌。
服务提供方根据临时令牌和用户的授权情况授予客户端访问令牌。
客户端使用获取的访问令牌访问存放在服务提供方上的受保护的资源。
25.http错误码
100：信息提示 200：成功  300：重定向 400：客户端错误  500：服务器错误
26.lru算法实现
http://www.cnblogs.com/python27/p/LRUCache.html
27.tornado异步实现 yield实现原理 epoll原理
http://www.nowamagic.net/academy/detail/13321005
epoll是Linux内核为处理大批量文件描述符而作了改进的poll，是Linux下多路复用IO接口select/poll的增强版本，它能显著提高程序在大量并发连接中只有少量活跃的情况下的系统CPU利用率。另一点原因就是获取事件的时候，它无须遍历整个被侦听的描述符集，只要遍历那些被内核IO事件异步唤醒而加入Ready队列的描述符集合就行了。epoll除了提供select/poll那种IO事件的水平触发（Level Triggered）外，还提供了边缘触发（Edge Triggered），这就使得用户空间程序有可能缓存IO状态，减少epoll_wait/epoll_pwait的调用，提高应用程序效率。

同步阻塞：进程/线程接到一个请求需要处理的时候，该进程/线程处理这个请求的时候别的请求无法进来，并且需要
该进程/线程一直等着处理完成才返回。此时操作系统的进程会一直等着数据处理完成并拿走。
同步非阻塞：几乎很少用，操作系统告诉进程需要处理一个请求了，自己又去干别的事了，但是进程又他妈不会主动通知你
这个请求处理完了，你可以去用户缓存区拿数据滚蛋了，所以操作系统就会一直切换进程来看数据好了没。
异步阻塞：操作系统接到一个请求，把这个请求给python进程处理，python进程告诉操作系统我去处理了，我处理好了
会通知你的，你可以先去忙别的了，但是操作系统的这个进程太傻，不去干别的，就在这等着，直到等到数据才返回。
异步非阻塞：操作系统收到请求给python进程处理，python进程告诉操作系统我去处理了，好了会通知你的，然后操作系统
就去忙别的了，python进程处理好了后把数据放到了缓存区并且通知了操作系统这个请求处理好了，你可以去拿了。
显而易见异步非阻塞是效率最高的。
@tornado.web.asynchronous
     @tornado.gen.coroutine
     def get(self):
         url = "www.douban.com/search/"
         data = {}
         data['title'] = 'fury'
         ...
         client = tornado.httpclient.AsyncHTTPClient()
         response = yield client.fetch(url, method=POST, body=json.dumps(data))
         self.on_response(response)

     def on_response(self, resp):
         body = json.loads(resp.body)
         if body == None:
             self.write('error')
         else:
             self.write(body)
         return

28.mysql索引
http://tech.meituan.com/mysql-index.html
29.前沿技术

30.为什么会有线程和进程，它们的适用场景

31.python闭包
简单说,闭包就是根据不同的配置信息得到不同的结果
再来看看专业的解释:闭包（Closure）是词法闭包（Lexical Closure）的简称，是引用了自由变量的函数。这个被引用的自由变量将和这个函数一同存在，即使已经离开了创造它的环境也不例外。所以，有另一种说法认为闭包是由函数和与其相关的引用环境组合而成的实体。

32.怎么解决mysql主从同步延迟的问题
http://www.linuxidc.com/Linux/2014-05/101450.htm
33.Python如何实现单例模式？  
1.继承类
class Singleton(object):
    def __new__(cls, *args, **kw):
        if not hasattr(cls, '_instance'):
            orig = super(Singleton, cls)
            cls._instance = orig.__new__(cls, *args, **kw)
        return cls._instance


2.装饰器
def singleton(cls, *args, **kwargs):
    instances = {}
    def _singleton(*args, **kwargs):
        if not instances.has_key(cls):
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]
    return _singleton

@singelton
class MyClass(Singleton):

34.什么是lambda函数？
Python允许你定义一种单行的小函数。定义lambda函数的形式如下：labmda 参数：表达式lambda函数默认返回表达式的值。你也可以将其赋值给一个变量。lambda函数可以接受任意个参数，包括可选参数，但是表达式只有一个：

35.Python是如何进行类型转换的？
int("345")   str(343)
36.如何反序的迭代一个序列？
1. list反序直接可用a.reverse()
2.print a[-1::-1]，直接实现reverse的功能
3. a[:-1]从头开、始，（len-1）个，不包括最后一个
4. a[-1:]最后一个，等同于a[-1]

37.Python里面如何实现tuple和list的转换？
Python中，tuple和list均为内置类型，
以list作为参数将tuple类初始化，将返回tuple类型
tuple([1,2,3]) #list转换为tuple
以tuple作为参数将list类初始化，将返回list类型
list((1,2,3)) #tuple转换为list

38.请写出一段Python代码实现删除一个list里面的重复元素
python strip函数 list去重 sort从小到大排序和 reversed()倒序 sorted()排序.note
{}.fromkeys(ll).keys()

39.有没有一个工具可以帮助查找python的bug和进行静态的代码分析？
pychecker和pylint

40.如何在一个function里面设置一个全局的变量？
global
http://www.jb51.net/article/64058.htm
41.有两个序列a,b，大小都为n,序列元素的值任意整形数，无序；要求：通过交换a,b中的元素，使[序列a元素的和]与[序列b元素的和]之间的差最小。

42.Python里面search()和match()的区别？
match()函数只检测RE是不是在string的开始位置匹配，search()会扫描整个string查找匹配；

43.经常上的网站
iteye,stackoverflow,oschina,segmentfault,github,zhihu,csdn

44.sql语句复习

45.杨洋的python奇淫巧计
http://duoduo369.github.io/chatter/#13

46.常用数据结构算法


冒泡：临近的2个关键字比较，谁小谁就升上去，大的就降下去，然后这个大的继续和临近的后面那个关键字比较。一直比较N-1轮 
选择：遍历所有关键字中最小的那个排到最前面，然后遍历剩下的第二小的排在第二个，以此类推，遍历N轮
插入排序： 从第2个关键字开始和前面的关键词比较，如果比前面的小就交换位置，直到遇到比前面大的关键字就进入下一轮循环 遍历N-1轮
快速排序：http://zhidao.baidu.com/link?url=568g3jCcCuey8TczIAelJW5XHtjM3AlHgeEp9nx_Elxqg2jBatLp3gqw7lGBaQrowohPTLK79SDcxbVwazBC4_
：从需要比较的列表中选择一个初始计较关键字，一般选第一个关键字，然后以这个关键字为比较对象，把大于这个关键字的
其他的关键字放到它的右边，把小于这个关键字的其他的关键字放到它的左边，然后再把左边的数据按照递归的办法重复这一步骤知道左边的顺序排好，然后右边，最后就ok了。
归并排序：http://blog.csdn.net/hguisu/article/details/7776068







47.get和post区别 这个要深入一点 不能按照网上的回答
https://segmentfault.com/a/1190000005613496

48.负载高可能的原因


49.tornado的异步实现的原理 这个必须深入理解下


50.mysql redis优化方案


51.linux 常用命令 sed awk什么的也看下
http://www.2cto.com/os/201307/226591.html
cat access.log | grep "05/Aug/2016:18:39" | wc -l
awk是一种编程语言，用于在linux/unix下对文本和数据进行处理。数据可以来自标准输入、一个或多个文件，或其它命令的输出。它支持用户自定义函数和动态正则表达式等先进功能，是linux/unix下的一个强大编程工具。它在命令行中使用，但更多是作为脚本来使用。awk的处理文本和数据的方式是这样的，它逐行扫描文件，从第一行到最后一行，寻找匹配的特定模式的行，并在这些行上进行你想要的操作。如果没有指定处理动作，则把匹配的行显示到标准输出(屏幕)，如果没有指定模式，则所有被操作所指定的行都被处理。awk分别代表其作者姓氏的第一个字母。因为它的作者是三个人，分别是Alfred Aho、Brian Kernighan、Peter Weinberger。gawk是awk的GNU版本，它提供了Bell实验室和GNU的一些扩展。下面介绍的awk是以GUN的gawk为例的，在linux系统中已把awk链接到gawk，所以下面全部以awk进行介绍。

sed是一种在线编辑器，它一次处理一行内容。处理时，把当前处理的行存储在临时缓冲区中，称为“模式空间”（pattern space），接着用sed命令处理缓冲区中的内容，处理完成后，把缓冲区的内容送往屏幕。接着处理下一行，这样不断重复，直到文件末尾。文件内容并没有改变，除非你使用重定向存储输出。Sed主要用来自动编辑一个或多个文件；简化对文件的反复操作；编写转换程序等。以下介绍的是Gnu版本的Sed 3.02。


52.有1000w用户 push一条消息 怎么在2-3分钟内完成
分布式一次性push过去，不要等相应

53.数据库分表 分库 索引什么
索引：http://www.2cto.com/database/201303/197717.html



54.RDB和AOF的redis持久化机制
http://my.oschina.net/davehe/blog/174662


55.进程之间如何通信
http://jingyan.baidu.com/article/3a2f7c2e17e12b26afd611cb.html
管道，共享内存，信号量、信号、消息队列，socket，

56.python常用的设计模式
http://www.cnblogs.com/wuyuegb2312/archive/2013/04/09/3008320.html


57. rabbitmq
http://www.cnblogs.com/mingaixin/archive/2012/10/26/2741624.html
Exchange，Queue，RoutingKey
 

蓝色-- Client（相对于Rabbitmq Server来说）
绿色--Exchange
红色—Queue
     - 交换器（Exchange），它是发送消息的实体。
     - 队列（Queue），这是接收消息的实体。
     - 绑定器（Bind），将交换器和队列连接起来，并且封装消息的路由信息。

58. 深入理解HTTP协议


59.RESTful
http://www.cnblogs.com/loveis715/p/4669091.html

60.git使用规范
http://duoduo369.github.io/chatter/git.html#1

61.单点登录原理，新浪登录了后登录微博怎么直接登录的。
http://blog.csdn.net/ghsau/article/details/20545513
认证系统根据用户在浏览器中输入的登录信息，进行身份认证，如果认证通过，返回给浏览器一个证明[认证系统_ticket]；这时再通过浏览器将[认证系统_ticket]发送到到应用系统1的设置cookie的url，应用系统1返回给浏览器一个证明[应用系统1_ticket]，这时再将请求重定向到最初访问的页面，以后应用系统1就可以自动登录了。现在用户访问了应用系统2，由于应用系统2没有生成过cookie（但是用户已经在应用系统1登录过一次了），将请求重定向到认证系统；认证系统检测到已经生成过[认证系统_ticket]了，认证通过；再通过浏览器将[认证系统_ticket]发送到到应用系统2的设置cookie的url，应用系统2返回给浏览器一个证明[应用系统2_ticket]，这时再将请求重定向到最初访问的页面。应用系统3也同样原理，我们等于将ticket做了一次同步，保证了每个应用系统都有一份认证系统产生的ticket。剩余的ticket验证过程和上篇文章一样了。

62.http实现聊天，怎么会被动接收消息
http://blog.lmlphp.com/archives/18/The_technology_principle_and_realization_of_real-time_push_WEB_message_based_on_HTTP_protocol

http://blog.csdn.net/psp0001060/article/details/51223662

63.nginx配置匹配优先级
http://blog.csdn.net/xy2204/article/details/47749405

64.一致性哈希
http://blog.csdn.net/cywosp/article/details/23397179/

65.codis对redis的集群部署方案
http://www.cnblogs.com/xuanzhi201111/p/4425194.html

66. python元类
http://blog.jobbole.com/21351/

67.nginx深入理解


68.一些乱七八糟的问题
多继承，2个子类的调用  django rest_framework
django 用命令执行脚本 ./manage.py lms --settings=aws gen_paper_credential "13136" "course-323"

69.https的使用
http://www.cnblogs.com/wuhuacong/p/4814708.html




