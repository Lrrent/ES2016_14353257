#DOL(Distributed Operation Layer)实验文档

------
第一次试验：主要进行DOL环境的安装和配置：
 * DOL框架描述
 * DOL环境安装
 * 实验感想及心得
 
----------

### 1. DOL框架描述

 DOL,distirbute operation layer,是一个进行并发应用编程的软件开发框架，通过它，可以自动将应用map到多处理器SHAPES架构平台上，它主要包括以下三个部分：
1. DOL Application Programming Interface
   &ensp;&ensp;&ensp; 这部分主要包括一些提供给编程人员的应用程序接口(API).
2. DOL Functional Simulation
    &ensp;&ensp;&ensp;这一部分主要是提供给编程人员测试他们的应用，并且用来获得应用层的一些数据.，参数等等
3. DOL Mapping Optimization
    &ensp;&ensp;&ensp;这一部分的目标主要是计算运行在SHAPES架构平台中的应用的一组最优的mapping.
 ---
### 2. DOL安装与配置(Ubuntu14.04下)
**安装之前先换下源，这样可以提高下载速度。方法可参考链接[Ubuntu 14.04用户修改更新源和替换软件源的方法](http://www.linuxidc.com/Linux/2014-04/100476.htm)**
<div style="margin-left:20px">
    <li>**安装一些必要的环境**</li>
    -安装更新
    <code>sudo apt-get update</code>
    -安装ant
    <code>sudo apt-get install ant</code>
    -安装JDK
    <code>sudo apt-get install openjdk-7-jdk</code>
    -安装解压工具unzip
    <code>sudo apt-get install unzip</code>
    <li>**解压文件**</li>
    -在根目录新建dol的文件夹
    <code>mkdir dol</code>
    -将dolethz.zip文件解压到dol文件夹
    <code>unzip dol_ethz.zip -d dol</code>
    -解压systemc
    <code>tar -zxvf systemc-2.3.1.tgz</code>
    <li>**编译systemc**</li>
    -解压完成后进入systemc-2.3.1的目录
    <code>cd systemc-2.3.1</code>
    -进入systemc-2.3.1文件夹
    <code>cd systemc-2.3.1</code>
    -运行configure(能够根据系统的环境设置参数，用于编译)
    <code>../configure CXX=g++ --disable-async-updates </code>
    *如果你的系统中没有预先安装g++,则会出现以下的错误，解决方法只需要在终端中输入以下指令安装g++库就好*
    <code>sudo apt-get install g++</code>
    ![image](https://github.com/Lrrent/ES2016_14353257/blob/master/screenshoot/configure错误，没装g++库.png)
    安装g++后再次运行configure,成功结果如下:
    ![image](https://github.com/Lrrent/ES2016_14353257/raw/master/screenshoot/configure_success.png)
    -编译systemc,这一步花的时间比较长
    <code>sudo make install</code>
    -编译完后上一步没有什么错误的话,可以查看以下文件目录如下：
    <code>cd ..</code>
    <code>ls</code>
    ![编译后目录](https://github.com/Lrrent/ES2016_14353257/raw/master/screenshoot/ls.jpg)
    <li>**编译DOL**</li>
    -进入刚刚新建的dol文件夹
    <code>cd ../dol</code>
    -进入并修改build_zip.xml文件
    <code>gedit build_zip.xml</code>
    找到下面这段话，就是说上面编译的systemc位置在哪里，
    ```
    <property name="systemc.inc" value="YYY/include"/>
    <property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
    ```
    把YYY改成你的systemc的路径（注意，对于  64位 系统的机器，lib-linux要改成lib-linux64）
    -然后就是编译dol
    <code>ant -f build_zip.xml all</code>
    如果编译成功就会显示build successful:
    ![编译成功](https://github.com/Lrrent/ES2016_14353257/raw/master/screenshoot/all.jpg)
    <li>**运行第一个例子（接着上一步）**</li>
    -进入build/bin/main目录
    <code>cd build/bin/main</code>
    -运行第一个例子
    <code>ant -f runexample.xml -Dnumber=1</code>
    如果运行后你得到下面的结果，就说明配置成功了。
    ![编译成功](https://github.com/Lrrent/ES2016_14353257/raw/master/screenshoot/build_success.jpg)
</div>
###3. 实验感想及心得
第一次实验是比较简单的DOL环境配置，但是也遇到了一些问题，比如说：
1. 直接找到并修改build_zip.xml文件后无法保存，这是因为权限不够，只要在终端输入 <code>sudo gedit build_zip.xml </code>后再修改即可保存。
2. 在configure这一步出错，错误提示可看上面配置过程，这是因为没有安装g++的结果，安装后即可解决
3. 
