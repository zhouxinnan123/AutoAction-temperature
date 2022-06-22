# AutoAction-temperature—简介
  自动填报晨午检。借鉴[GitHub Action自动完成华工疫情打卡、网站自动签到](https://blog.csdn.net/police_1/article/details/106837694)、[河北科大每日晨午检](https://blog.csdn.net/m0_47319143/article/details/119823717?ops_request_misc=&request_id=&biz_id=102&utm_term=%E6%B2%B3%E5%8C%97%E7%A7%91%E5%A4%A7%E4%BD%93%E6%B8%A9&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-119823717.142^v20^control,157^v15^new_3&spm=1018.2226.3001.4187)
# 准备工作
    1.一个github账号
    2.一个163邮箱账号：用于发送签到成功邮件，推荐添加，为了方便验证是否签到成功（可选）
# 上手教程

1.把代码clone到本地或者直接点击fork按钮将工程复制到你的仓库

![在这里插入图片描述](https://img-blog.csdnimg.cn/f3b2478cfe5d428899d219e5525f009f.png#pic_center)
2.邮件SMTP配置，本文以配置163邮箱为例。点击开启按钮，开启smtp。然后点击新增授权码，按步骤最后会得到一串字符（授权码），将字符串复制，并把它放到第三步里面的EMAILPOP变量

![在这里插入图片描述](https://img-blog.csdnimg.cn/1f9d52467b06457ba1b373397352d32c.png#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/d4d2a97a807845a3bb4f3cdbd8d766f1.png#pic_center)

3.配置你的账号和密码。在工程的secrets里面放置你的账号和密码。同样的，如果你不需要发送邮件通知可以不添加邮件配置。（EMAILNAME和EMAILPOP两个变量名需要跟tiwentianbao.yml代码里面的一致）

![在这里插入图片描述](https://img-blog.csdnimg.cn/ada5461a46b041839e536e2aee706e6d.png#pic_center)


4.点击打开autoclick.py文件，并修改信息。

 ![在这里插入图片描述](https://img-blog.csdnimg.cn/9a0e49798edf455b86b352a492f70078.png#pic_center)
 ![在这里插入图片描述](https://img-blog.csdnimg.cn/594b2a461b3e4a9a9a31929ab61c0a33.png#pic_center)

5.打开Action查看工作流

![在这里插入图片描述](https://img-blog.csdnimg.cn/875d15d1d8844d43b26ddde641056013.png#pic_center)

6.新建工作流main.yml文件，将原本.github/workflows/tiwentianbao.yml文件代码复制到main.yml,复制过程中修改信息（如果不想收到邮件通知，可以把下面的邮件发送代码删掉。如果不删，记得把里面的邮箱换成自己的邮箱账号。）复制完成之后，请把.github/workflows/tiwentianbao.yml删掉，不然每天它都会运行一次。

![在这里插入图片描述](https://img-blog.csdnimg.cn/80b2bfbe5c39443bb7bd2710d237a14e.png#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/0a1d93efeb644319974e157942a03e97.png#pic_center)
![在这里插入图片描述](https://img-blog.csdnimg.cn/79dfbc343cae496b9a130f68cb9c00d2.png#pic_center)

7.yml文件中设置了每天北京11：10、每次代码提交、仓库被star都会触发工作流


```
on:
  workflow_dispatch: #在actions界面点击即可运行
  schedule:
    - cron: '10 3 * * *'  
  #在北京时间11点10分自动运行
  
```
8.上面代码提交之后，会自动运行。同时也可以在Actions中运行

![在这里插入图片描述](https://img-blog.csdnimg.cn/2e44ada3a766464a98939b61261cd9ed.png#pic_center)

9.运行情况

![在这里插入图片描述](https://img-blog.csdnimg.cn/45d2383a00a645dbb2343f32ec365155.png#pic_center)


10.运行结束后，会有邮件发送

![在这里插入图片描述](https://img-blog.csdnimg.cn/8bdaab30a62e40d68b5442eb2ea2a181.png#pic_center)

11.之后要是不需要每天填报了，那进入setting-》action-》选择Disable Action。该仓库的工作流将不再运行。

![在这里插入图片描述](https://img-blog.csdnimg.cn/75d7ba16e4e04007ac4953aba733c904.png#pic_center)
