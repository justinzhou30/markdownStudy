# Markdown文件学习笔记

[toc]

## Flow 流程图描述语言

### 定义元素语法

> `tag=>type: content:>url`
>
> `tag` ：为元素名称  
> `type` ：为下面6种关键字  
> `content` ：为框中要写的内容，注意 __type后的冒号与文本之间一定要有个空格__  
> `url`： 是一个连接，与框框中的文本相绑定  

### 关键字

> start #开始  
> end   #结束  
> operation #操作  
> subroutine #子程序  
> condition #条件  
> inputoutput #输入输出  
>
>**如下图所示**
>
>```flow
>st=>start: Start
>st->
>```
>
>```flow
>ed=>end
>ed->
>```
>
>```flow
>op=>operation: Operation
>op->
>```
>
>```flow
>sub=>subroutine: Subroutine
>sub->
>```
>
>```flow
>con=>condition: Yes or No?
>con->
>```
>
>```flow
>io=>inputoutput: InputOutput
>io->
>```

### 链接元素语法

>用->来连接两个元素，需要注意的是condition类型，因为他有yes和no两个分支，所以要写成  
>
>c2(yes)->io->e   
>c2(no)->op2->e

### 实际应用

#### 示例一
>
>```
>st=>start: Start
>op=>operation: Your Operation
>cond=>condition: Yes or No?
>e=>end
>st->op->cond
>cond(yes)->e
>cond(no)->op
>```
>
> __输出效果如下图所示__  
>
>```flow
>st=>start: Start
>op=>operation: Your Operation
>cond=>condition: Yes or No?
>e=>end
>st->op->cond
>cond(yes)->e
>cond(no)->op
>```

#### 示例二

>```
>st=>start: Start|past:>http://www.baidu.com
>e=>end:  Ende|future:>http://www.baidu.com
>op1=>operation:  My Operation
>op2=>operation:  Stuff|current
>sub1=>subroutine:  My Subroutine|invalid
>cond=>condition:  Yes or No|approved:>http://www.google.com
>c2=>condition:  Good idea|rejected
>io=>inputoutput:  catch something...|future
>st->op1(right)->cond
>cond(yes, right)->c2
>cond(no)->sub1(left)->op1
>c2(yes)->io->e
>c2(no)->op2->e  
>```
>
>__输出效果如下图所示__
>
>```flow
>st=>start: Start:>http://www.baidu.com
>e=>end:  Ende:>http://www.baidu.com
>op1=>operation:  My Operation
>op2=>operation:  Stuff
>sub1=>subroutine:  My Subroutine
>cond=>condition:  Yes or No:>http://www.google.com
>c2=>condition:  Good idea
>io=>inputoutput:  catch something...|future
>st->op1(right)->cond
>cond(yes, right)->c2
>cond(no)->sub1(left)->op1
>c2(yes)->io->e
>c2(no)->op2->e  
>```