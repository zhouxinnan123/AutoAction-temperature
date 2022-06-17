# AutoAction—简介
    该github工程主要是为了解决疫情期间华工需要不断地申报自身健康而建立,工程中使用GitHub Action来实现每天自动打卡工作。
# 准备工作
    1.一个github账号
    2.一个163邮箱账号：用于发送签到成功邮件，推荐添加，为了方便验证是否签到成功（可选）
#	上手教程
由于github上无法查看图片，建议移步到csdn查看上手教程：[csdn](https://blog.csdn.net/police_1/article/details/106837694)

1.把代码clone到本地或者直接点击fork按钮将工程复制到你的仓库
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200618170529885.png)
2.邮件SMTP配置，本文以配置163邮箱为例。点击开启按钮，开启smtp。然后点击新增授权码，按步骤最后会得到一串字符（授权码），将字符串复制，并把它放到第三步里面的EMAILPOP变量

![在这里插入图片描述](https://img-blog.csdnimg.cn/20200618182701545.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200618182802385.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
3.配置你的账号和密码。在工程的secrets里面放置你的账号和密码。同样的，如果你不需要发送邮件通知可以不添加邮件配置。（EMAILNAME和EMAILPOP两个变量名需要跟tiwentianbao.yml代码里面的一致）
![在这里插入图片描述](https://github.com/13063516125/AutoAction-temperature/blob/master/IMAGE/secrets.png)

4.点击打开autoclick.py文件，并修改信息。
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/20200618172029327.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200618172541226.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200618172155813.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)

5.打开Action查看工作流
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200618222752943.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
6.新建工作流main.yml文件，将原本.github/workflows/tiwentianbao.yml文件代码复制到main.yml,复制过程中修改信息（如果不想收到邮件通知，可以把下面的邮件发送代码删掉。如果不删，记得把里面的邮箱换成自己的邮箱账号。）复制完成之后，请把.github/workflows/tiwentianbao.yml删掉，不然每天它都会运行一次。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200619094611775.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020061909494572.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020061909543129.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200619095721133.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
7.yml文件中设置了每天北京11：10、每次代码提交、仓库被star都会触发工作流

```
on:
  workflow_dispatch: #在actions界面点击即可运行
  schedule:
    - cron: '10 1,3 * * *'  
  #在UTC时间1:10,3:10运行，也就是北京时间9点10分和11点10分
  
```
8.上面代码提交之后，会自动运行。同时也可以在Actions中运行

9.运行情况
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020061822350874.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)

10.运行结束后，会有邮件发送
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200618223940995.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
11.之后要是不需要每天填报了，那进入setting-》action-》选择Disable Action。该仓库的工作流将不再运行。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200619100121815.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3BvbGljZV8x,size_16,color_FFFFFF,t_70)
参考链接：[GitHub Actions 入门教程](http://www.ruanyifeng.com/blog/2019/09/getting-started-with-github-actions.html)

