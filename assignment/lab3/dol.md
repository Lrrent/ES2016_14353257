# DOL实例分析与编程 #
## 一．   实验任务 
    1. 修改example1,使其输出三次方数
    2. 修改example2,让3个square模块变成2个
##二．    实验结果 
###1. example1
dot图:<br>
![](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/dot1.png)
<br>结果:<br>
![](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/example1.png)
###2.  example2
dot图:<br>
![](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/dot2.png)
<br>结果:<br>
![](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/example2.png)
##三．实验步骤 
###1. example1
 a. 将example1的src中square.c文件下图中的```i*i```改为```i*i*i```<br>
    ![](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/ex1_i.jpg)<br>
 b.将dol/build/bin/main中的example1删除<br>
 c.	进入build/bin/main文件夹<br>
    ``  cd dol/build/bin/main``<br>
d.	编译运行example1<br>
``    sudo ant -f runexample.xml -Dnumber=1``
###2.  example2
a.	将example2中的example2.xml文件下图位置中的3改为2<br>
![](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/example2_values-2.png)<br>
b.	将dol/build/bin/main中的example2删除<br>
c.	进入build/bin/main文件夹<br>
    ``cd dol/build/bin/main``<br>
d.	编译运行example2<br>
    ``sudo ant -f runexample.xml -Dnumber=2``<br>

##四．    实验代码分析##
在分析之前我们需要先了解Example中代码的结构以便更加容易理解.可以看到两个example中都有三个主要文件,generator,consumer,square.根据dot图可以看出具体过程为由generator模块产生输入数据并写到端口PORT_OUT上,然后经过square模块对数据进行处理之后,由consumer模块读取输入端数据,然后打印出来.<br />
    1.    Example1<br />
    根据上面分析,很容易知道如何修改了,既然只是需要输出结果变成三次方,那么就和generator模块以及consumer模块无关啦。只需要修改中间对数据的处理即可,所以只要将square.c中的``i*i``改为``i*i*i``即可。<br />
    2.	Example2<br />
    Example2的修改则需要分析一下example2.xml文件,它定义了系统的架构,即模块连接方式.在这个文件中定义了生产者模块,迭代生成了3个square模块以及消费者模块.因此,如果需要产生2个square模块,只需要将迭代次数N的value改为2即可.<br />

##五．    实验感想 ##
通过本次实验,我们大概可以知道嵌入式系统的三个主要模块了,信号收集,信号处理以及信号输出.由于这次实验涉及的代码量也不多并且ppt很详细,所以过程中并没有多大问题.
