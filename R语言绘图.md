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

