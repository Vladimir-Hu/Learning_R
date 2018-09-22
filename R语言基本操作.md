##R语言基本操作
###安装配置R
* CRAN上选择中科大（只要是\*\*\*.edu.cn便可）的镜像下载（校园网访问教育网内资源速度较快，同安装R的packages）
* 安装R Studio
###R语言基础（课上Slides）
####赋值与输出

```R
a <- 5						#赋值操作
a = 5						#赋值操作
a 							#在命令行中直接输出
print(a)					#在代码中显示输出
cat(a)						#类似于UNIX系统里的cat，但R不支持tac
```

#### 对象的操作

```R
ls()						#列举项目，用过ls -l之类命令的就知道了
rm()						#移除项目
rm(list=ls())
							#移除全部项目
```

#### 逻辑操作符

照搬C的那一套就好了

```R
is.na()						#检查一个值是否不存在(Not Available)
							#类似Perl的undef概念，但区分了0的不同
> Am_I_a_pig <- c(1:3)
> is.na(Am_I_a_pig)
[1] FALSE FALSE FALSE
```

#### 类型转换（判断）

```R
as.numeric(x)				#数字形式
as.integer(x)				#整数形式
as.charater(x)				#转换为字符串
as.logical(x)				#转换为逻辑操作
as.matrix(x)				#转换为矩阵
```

笔记：不明白`as.logical`的用法，尝试一下

```R
> num = c(1:9)
> as.logical(num)
 [1] TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE TRUE
> num = c(-9:9)
> as.logical(num)
 [1]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE
[13]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
> num = as.character(num)
> as.logical(num)
 [1] NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA NA

```

* R仅仅把**0**视作FALSE
* 也只能处理数字

#### 字符串操作

* paste操作

  ```R
  						#把东西粘在一起，sep决定分隔的样式，""表示没有间隔
  > t=1					#不一定要像课件里那样转换
  > t=paste("cake",t,"apple",sep="!!!")
  > t
  [1] "cake!!!1!!!apple"
  ```

* substr,nchar函数

  ```R
  > "A quick brown fox jump over the lazy dog." -> repair
  						#R使用箭头赋值可以左右颠倒（注意方向）
  > nchar(repair)
  [1] 41
  > substr(repair,1,4)
  [1] "A qu"
  > substr(repair,1,5)="12345"
  > repair
  [1] "12345ck brown fox jump over the lazy dog."
  ```



#### 生成一些东西

```R
numeric(3)					#3个空的向量
character(3)				#道理同上
> logical(3)
[1] FALSE FALSE FALSE		#生来就是个错误
seq(-4,4,0.1)				#从-4开始，0.1为步长，产生一大群数，直到4
c(5,7,1:3)					#数组，正常操作
rep(1,999)					#复读机
> matrix(1:12,nrow=3,ncol=4)
     [,1] [,2] [,3] [,4]
[1,]    1    4    7   10
[2,]    2    5    8   11
[3,]    3    6    9   12
> matrix(1:12,nrow=3,ncol=4, byrow=TRUE)
     [,1] [,2] [,3] [,4]
[1,]    1    2    3    4
[2,]    5    6    7    8
[3,]    9   10   11   12
							#观察一下就好，不要忘记n
```

#### 数学函数

* log等价与ln
* *\*等价于幂运算，用exp的话可以是e的幂次

```R
> round(3.1415926525897932384626,7)
[1] 3.141593
```

#### 比较好用的一些函数（可能位于统计中）

```R
legth(x)					#x长度
min(x),max(x)				#As their names suggest
sort(x)						#Perl也有
sum(x)						#求和
var(x)						#方差
sd(x)						#标准差
cor(x,y)					#相关度
```

#### 数据结构

* 常见数据结构

* Data Frame

* List（列表——或许类似于散列？？？）

* Data frame

  * 每一列都有相同性质的数据（同一种物理性质或者化学性质，浓度等等）

  * 每一行代表这些性质的来源体（比如实验一这样子）

    ```R
    > head(mtcars)
                         mpg cyl  disp  hp drat    wt  qsec vs am gear 
    Mazda RX4           21.0   6 160.0 110 3.90 2.620 16.46  0  1    4   
    Mazda RX4 Wag       21.0   6 160.0 110 3.90 2.875 17.02  0  1    4   
    Datsun 710          22.8   4 108.0  93 3.85 2.320 18.61  1  1    4   
    Hornet 4 Drive      21.4   6 258.0 110 3.08 3.215 19.44  1  0    3   
    Hornet Sportabout   18.7   8 360.0 175 3.15 3.440 17.02  0  0    3   
    					#可以直接访问每一列（例如mtcars$gear)
    					#每一列的长度要标齐
    ```
