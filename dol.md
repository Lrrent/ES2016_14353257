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

- ## 实验感想 ##
     
