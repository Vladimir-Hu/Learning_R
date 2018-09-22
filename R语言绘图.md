## R语言绘图

> ​	 喜欢装在树莓派上的R版本代号: *Someone To Lean On* 

#### 课件上的“高下之分”

* 课件上的*High level functions*不知所云，在此就简单陈列出来

* 估计是先有了*High*,再有了*Low*进行修饰美化

* 还请上课听讲，精通藏语/法语的同学指点^_^

  | *High Level* | *Low Level* |
  | :----------: | :---------: |
  |    plot()    |  points()   |
  |    hist()    |   lines()   |
  |  barplot()   |  abline()   |
  |  boxplot()   |   text()    |
  |              |   mtext()   |
  |              |   title()   |
  |              |  legend()   |


##### 这些人都在说些什么啊

##### High Functions

* plot()

  最基础的绘图，仅表示x-y的关系

  ```R
  > x <- c(rnorm(47,1,27))
  > y <- c(rnorm(47,1,27))
  > plot(x,y)
  ```

* hist()

  *Histogram*代表直方图，就那一个个柱子

  ```R
  > data <- c(rep(1, 10), rep(2, 5), rep(3, 6))
  > data
   [1] 1 1 1 1 1 1 1 1 1 1 2 2 2 2 2 3 3 3 3 3 3
  > hist(data)
  					#和SPSS一样，不可以直接输入我们容易理解的中文！
  					#Example is as followed:
  > clubs <- c("不通过","不通过","不通过","不通过","不通过","不通过","不通过","不通过","不通过","不通过","不通过","不通过","不通过","不通过","通过")
  > hist(clubs)
  Error in hist.default(clubs) : 'x'必需为数值
  ```

* barplot()
* boxplot()

##### Low Functions 

> 不可去名上理会。须求其所以然。  ——《朱子语类》

在开始的开始，先弄一个*高端*函数来做参考

```R
> x=c(1,2,3,4,5,6)		#简单的点，下同
> y=c(1,2,3,4,5,6)
> plot(x,y)				#简单的图
```



* points()

  不要信什么**晦涩难懂的教程**，x,y根本就不是横纵坐标的意思。这里把x,y看成点

  ```R
  > points(x,y=5,3)	#我们一起学猪叫
  Error in xy.coords(x, y) : 'x' and 'y' lengths differ
  > points(x=c(3,4),y=c(1,5))
  ```

  参数设定

  ```R
  > points(x=c(3,4),cex=c(9,0.1),y=c(1,5))
  					#cex指定点的大小，按顺序分配，不管你是不是塞在了中间
  > points(x=c(2,4),lwd=c(9,0.1),y=c(0,4))
  					#lwd指定点的厚度，按顺序分配
  > points(x=c(3,4),col=c("red","blue"),y=c(1,5))
  					#同样的，还有广泛使用的col指定颜色
  #一段经典的代码
  > points(x=c(2,4),lwd=c(9,0.1),y=c(0,4))
  > plot(1:5, 1:5, xlim = c(0,6), ylim = c (0,6), type = "n")
  > index <- 1:25
  > start <- 0
  > for (i in 1:5) {
  + for (j in 1:5) {
  + start <- start + 1
  + points(x = i, y = j, pch = index[start], cex = 1.5)
  + text(x = i, y = j, labels = index[start], pos = 3, offset = 1)
  + }
  + }
  					#pch指定点的样式
  > points(x=c(2,4),bg=c("red","cyan"),pch=c(22,25),y=c(0,4))
  					#bg是填充，pch21~25才有，也可以先bg
  ```


* lines()和abline()
  * lines在原图上直接加直线
  * 不要打成line
  * abline可以指定$y=ax+b$这样的函数形式
  * abline可以画垂直坐标轴的直线，可以建立线性回归方程
  * lines()输入的时候注意x,y又变回了横纵坐标
* text()
* mtext()
* title()
* legend()