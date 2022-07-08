# Typora笔记上传给别时图片不显示问题解决

[TOC]

## 1.配置图床（GitHub + PicGo）

## (1)在Github新建一个仓库

必须是public的

![image](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210115100558.png)

## (2)在个人设置中生成 Access Token



[![image](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210115100607.png)](https://springboot.io/uploads/default/original/2X/b/ba40b6bb02331d2c741128bcf619d415f3a11f21.png)

repo权限全部勾上

[![image](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210115100612.png)](https://springboot.io/uploads/default/original/2X/3/339cd2f7d4cf27c56bf01b98a50e4490541102f5.png)



记录下生成的Token

## (3)使用图床客户端

下载并且安装（选择对应操作系统的客户端）

[GitHub 19](https://github.com/Molunerfinn/PicGo)

在图床设置中，正确的填写仓库信息，以及生成的Access Token，点击确定

![image](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210114141539.png)

在上传区，通过拖曳，或者复制上传图片

![image](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210114141619.png)

上传成功，仓库中已经有图片

![](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210115114346.png)

可以在PicGo中设置后用jsDelivr加速

![](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210115115245.png)

其中设定自定义域名

```
https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master
```

u1123p为用户名

image-bucket是仓库名

==@master是分支名==（也是第二个设定分支名中的名称）



# 2.Typora 设置上传图片功能

1. Ctrl + 逗号` 进入偏好设置 -> 上传服务设定

2. 对本地图片和网络位置图片都应用上述规则 -> 上传图片

3. 验证图片上传选项（关键步骤）

   然后，Typora 将从输出中获取两个远程图像 URL，并替换 Markdown 文档中使用的原始本地图像。您可以单击“测试上传器”按钮来验证您的自定义命令。第一次点击要验证的时候会失败，原因大概率是因为 **Picgo app 的监听端口设置不正确**

4. 解决办法

   进入 Picgo 软件 -> Picgo 设置 ->设置 server -> 设置监听端口 ->**将端口改为 36677** ->最后重新验证即可（127.0.0.1 是本地物理机的 ip 地址，）

![在这里插入图片描述](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210114141853.png)

![image-20200319120709531](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210114141920.png)

![在这里插入图片描述](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210114141911.png)

我的配置

![image-20210114131412128](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210114141933.png)

在这里如果图片上传不成功有以下几个解决方法

1. Token未更新
2. 仓库名称带空格，配置时需要变为-
3. 无法上传PNG
4. 图片名称不能带+
5. 仓库中已存在相同名称的图片
6. 重启PicGo或者电脑

官方文档中给出了其他错误及解决方法

![image-20210114131810130](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210114141944.png)

![image-20210114131827383](https://cdn.jsdelivr.net/gh/u1123p/image-bucket@master/20210114141956.png)



# 3.本地可看到传到GitHub上的图片

（1）找到C:\Windows\System32\drivers\etc目录下的hosts文件

（2）找到host文件，用记事本格式打开，添加代码（如果权限不够的话，复制一份，修改后覆盖原host）

```
# GitHub Start 
140.82.113.3      github.com
140.82.114.20     gist.github.com
151.101.184.133    assets-cdn.github.com
151.101.184.133    raw.githubusercontent.com
151.101.184.133    gist.githubusercontent.com
151.101.184.133    cloud.githubusercontent.com
151.101.184.133    camo.githubusercontent.com
151.101.184.133    avatars0.githubusercontent.com
199.232.68.133     avatars0.githubusercontent.com
199.232.28.133     avatars1.githubusercontent.com
151.101.184.133    avatars1.githubusercontent.com
151.101.184.133    avatars2.githubusercontent.com
199.232.28.133     avatars2.githubusercontent.com
151.101.184.133    avatars3.githubusercontent.com
199.232.68.133     avatars3.githubusercontent.com
151.101.184.133    avatars4.githubusercontent.com
199.232.68.133     avatars4.githubusercontent.com
151.101.184.133    avatars5.githubusercontent.com
199.232.68.133     avatars5.githubusercontent.com
151.101.184.133    avatars6.githubusercontent.com
199.232.68.133     avatars6.githubusercontent.com
151.101.184.133    avatars7.githubusercontent.com
199.232.68.133     avatars7.githubusercontent.com
151.101.184.133    avatars8.githubusercontent.com
199.232.68.133     avatars8.githubusercontent.com
# GitHub End
```

至此修改完成，即可在本地看到图片











# 参考文档

（1）[GitHub + jsDelivr CDN 全球加速的免费图床，它不香吗？](https://springboot.io/t/topic/1561)

（2）[Typora 设置上传图片功能](https://blog.csdn.net/haikupeng/article/details/104974939)

（3）[Picgo Github图床 上传失败](https://blog.csdn.net/qq_44275286/article/details/104858576?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromBaidu-1.control)

（4）[PicGo踩坑记（上传失败，服务端出错，请重试）](https://blog.csdn.net/TalesOV/article/details/104450037?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-5.channel_param&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-5.channel_param)

（5）[解决github+typora无法显示图片的问题](https://blog.csdn.net/weixin_41279876/article/details/109040379?utm_medium=distribute.pc_relevant.none-task-blog-baidujs_title-2&spm=1001.2101.3001.4242)

（6）[官方文档](https://support.typora.io/Upload-Image/)

（7）[PicGo + GitHub 搭建个人图床工具](https://blog.csdn.net/yefcion/article/details/88412025)