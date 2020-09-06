##### 1.基本选择器

​	jq中最常用的选择器，通过id，class，标签名来查找DOM元素。

##### ![image-20200906154523679](C:\Users\林帅哥\AppData\Roaming\Typora\typora-user-images\image-20200906154523679.png)2.层次选择器

​	通过DOM元素之间的层次关系获取特定元素，例如后代元素、子元素、相邻元素或兄弟元素等。

![image-20200906155800151](C:\Users\林帅哥\AppData\Roaming\Typora\typora-user-images\image-20200906155800151.png)

可用 next() 方法代替 $('prev + next')

可用 nextALL() 方法代替 $('prev~sibligs')

##### 3.过滤选择器

​	过滤选择器通过过滤规则筛选所需的DOM的元素，选择器以 ”：“ 开头。过滤选择器可分为：基本过滤、内容过滤、可见性过滤、属性过滤、子元素过滤和表单对象属性过滤。

###### 3.1基本过滤器

![image-20200906161826008](C:\Users\林帅哥\AppData\Roaming\Typora\typora-user-images\image-20200906161826008.png)

![image-20200906161836279](C:\Users\林帅哥\AppData\Roaming\Typora\typora-user-images\image-20200906161836279.png)

###### 3.2内容过滤选择器

![image-20200906162602102](C:\Users\林帅哥\AppData\Roaming\Typora\typora-user-images\image-20200906162602102.png)

###### 3.3可见性过滤选择器

![image-20200906162848286](C:\Users\林帅哥\AppData\Roaming\Typora\typora-user-images\image-20200906162848286.png)

###### 3.4属性过滤选择器

![image-20200906163321490](C:\Users\林帅哥\AppData\Roaming\Typora\typora-user-images\image-20200906163321490.png)

###### 3.5子元素过滤选择器

![image-20200906163518925](https://github.com/lin-zp/jq_notes/blob/master/images/image-20200906163518925.png)

###### 3.6表单对象属性过滤选择器

<<<<<<< HEAD
![image-20200906163649818](https://github.com/lin-zp/jq_notes/blob/master/images/image-20200906163649818.png)

##### 4.表单选择器

![image-20200906210426407](C:\Users\林帅哥\AppData\Roaming\Typora\typora-user-images\image-20200906210426407.png)

