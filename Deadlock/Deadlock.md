## DeadLock
----------
#### 一、实验任务
* 通过实验ppt中的代码,编译运行后使其发生死锁,并对原因进行分析
* 分析产生死锁的四个必要条件

#### 二、实验结果
 ![] (https://github.com/Lrrent/ES2016_14353257/blob/master/Deadlock/deadlock.png)
 从上图可以看到,当到达第32次循环的时候,达到死锁状态.
 

###三、实验代码以及死锁产生原因分析
首先贴一下代码:
 ```
class A{
	synchronized void methodA(B b){
		b.last();
	}
	synchronized void last(){
		System.out.println("Inside A.last()");
	}
}
 class B{
	synchronized void methodB(A a){
		a.last();
	}
	synchronized void last(){
		System.out.println("Inside B.last()");
	}
}

public class Deadlock implements Runnable{
	A a = new A();
	B b = new B();
	Deadlock(){
		Thread t = new Thread(this);
		int count = 20000;
		t.start();
		while(count-->0);
			a.methodA(b);
	}
	@Override
	public void run() {
		// TODO Auto-generated method stub
		b.methodB(a);
	}
	public static void main(String[] args){
		new Deadlock();
	}

}

 ```
 
*  从代码中可以看到,它使用了synchronized关键字,当使用它来修饰一个方法或者一个代码块时,能够保证最多只有一个线程执行改代码,而如果有其它线程想要调用这个代码块,那么这个进程就会被阻塞.
* 死锁产生原因:当在主函数中新创建一个Deadlock对象时,线程t会开始执行,之火被放入调度队列等待调度,当被调度时,就会运行run函数输出methodB中的内容,然后再输出methodA的内容. 而在a.method(b)有调用b.last()，当他先申请得到b.last()这部分资源的时候，run()如果再去申请a.last()就会被阻塞，只有等b.last()完全被释放，run()才会从阻塞的状态变为被唤醒，才能去申请资源a.last()。但是当methodB正在运行的过程中,等待时间刚好结束,这就会导致a.methodA开始执行,但是却又需要b对象资源,而run中的methodB又需要a资源,却无法得到。最后导致死锁产生.

###四、死锁产生四个必要条件
死锁就是两个或者多个进程,在互相请求对方占有的资源<br>
四个条件分别为:<br>
1.	互斥条件：一个资源每次只能被一个进程使用<br>
2.	请求与保持:当一个进程因请求资源而阻塞时,对已获得的资源保持不放<br>
3.	不剥夺条件:对于进程已经获得的资源,在未使用完之前,不能强行剥夺<br>
4.	循环且等待:若干进程之间形成一种头尾相接的循环等待资源关系<br>
