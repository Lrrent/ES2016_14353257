# DOL实例分析与编程 #

- ## 任务 ##
  1. 修改example2，让3个square模块变成2个, tips:修改xml的iterator
  2. 修改example1，使其输出3次方数，tips:修改square.c


- ## 实验过程及结果 ##
###example1###

 1. 进入build/bin/mian路径下,运行example1，查看修改之前的结果
		 cd build/bin/main
   ant -f runexample.xml -Dnumber=1
   　 ![example1](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/build_success.png)
 2. 打开dol/examples/example1/src/square.c，找到与下图语句位置，并把`i*i`改成`i*i*i`
      ![i*i] (https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/ex1_i.jpg) 
      
 3. 进入dol/build/bin/main文件夹,将example1整个文件夹删除后,再次运行example1，并查看结果
```python
         cd build/bin/main
         ant -f runexample.xml -Dnumber=1
```   
   　　![example1](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/example1.png)
     　　　![example1](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/dot1.png)
###example2###
 7. 运行example2
 ```python
	ant -f runexample.xml -Dnumber=2
 ```
	 　　![example2](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/example1.png)

	 　　![example2_dot](https://github.com/Lrrent/ES2016_14353257/blob/master/assignment/lab3/dot2.png)
  
- ## 代码分析 ##
在分析之前我们需要先了解Example中代码的结构以便更加容易理解.可以看到两个example中都有三个主要文件,generator,consumer,square.根据dot图可以看出具体过程为由generator模块产生输入数据并写到端口PORT_OUT上,然后经过square模块对数据进行处理之后,由consumer模块读取输入端数据,然后打印出来.
1.	Example1
根据上面分析,很容易知道如何修改了,既然只是需要输出结果变成三次方,那么就和generator模块以及consumer模块无关啦。只需要修改中间对数据的处理即可,所以只要将square.c中的i*i改为i*i*i即可。
2.	Example2
Example2的修改则需要分析一下example2.xml文件,它定义了系统的架构,即模块连接方式.在这个文件中定义了生产者模块,迭代生成了3个square模块以及消费者模块.因此,如果需要产生2个square模块,只需要将迭代次数N的value改为2即可.

- ## 实验感想 ##
通过本次实验,我们大概可以知道嵌入式系统的三个主要模块了,信号收集,信号处理以及信号输出.由于这次实验涉及的代码量也不多并且ppt很详细,所以过程中并没有多大问题     
