# <center>无水印上传本地图片到网络获取地址+小书匠使用 +github和 七牛云 图床绑定 

---
- 简介：
  最近开始写博客，缺少一个Markdown编辑器。寻找了两三天终于找到了这款《小书匠》，可复制粘图，可导出多种格式，导出.md文档可以直接导入博客，十分方便快捷。但是存在问题时图片转存的问题。本地图片在小书匠里可以使用，但导出好的小书匠.md文件想上传到csdn，是必须需要将图片上传到网络图床的。此处选择github图床储存仓库，当然此处也算是无水印将图片从本地上传到网络获取地址的一种方法了。
  
 ----
 
- 工具下载：链接: https://pan.baidu.com/s/1HKi_4PTAgac1VQbldjRLHA    提取码: txn4 
下载安装自己正常安装就可以。


---
## <center> github图床绑定：
1.左侧菜单栏->"**绑定**"
![enter description here](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRodWIuY29tL215aHVpYmJhb3FpL2NjYy9yYXcvbWFzdGVyLyVFNSVCMCU4RiVFNCVCOSVBNiVFNSU4QyVBMC8xNTYzNjgyMjQ3Njg3LnBuZw)

2.选择github
![enter description here](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRodWIuY29tL215aHVpYmJhb3FpL2NjYy9yYXcvbWFzdGVyLyVFNSVCMCU4RiVFNCVCOSVBNiVFNSU4QyVBMC8xNTYzNjgyMjYzMjIyLnBuZw)

3.选择下方申请“**token**"
![https://raw.githubusercontent.com/myhuibbaoqi/ccc/master/%E5%B0%8F%E4%B9%A6%E5%8C%A0/1563682330499.png](https://img-blog.csdnimg.cn/20190721124413803.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

4.进入github 登陆后 自己设置一个名字，选项勾选如下图，点击Generate
![enter description here](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRodWIuY29tL215aHVpYmJhb3FpL2NjYy9yYXcvbWFzdGVyLyVFNSVCMCU4RiVFNCVCOSVBNiVFNSU4QyVBMC8xNTYzNjgyNDczMTY5LnBuZw)
![\[外链图片转存失败(img-R3dRH51O-1563684046509)(https://github.com/myhuibbaoqi/ccc/raw/master/小书匠/1563682782637.png)\]](https://img-blog.csdnimg.cn/20190721124455750.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

5.得到“**token**”值填入小书匠下图位置：
![enter description here](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRodWIuY29tL215aHVpYmJhb3FpL2NjYy9yYXcvbWFzdGVyLyVFNSVCMCU4RiVFNCVCOSVBNiVFNSU4QyVBMC8xNTYzNjgyOTg0OTg1LnBuZw)
![\[外链图片转存失败(img-D460nolH-1563684046515)(https://github.com/myhuibbaoqi/ccc/raw/master/小书匠/1563683012498.png)\]](https://img-blog.csdnimg.cn/20190721124507602.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

6.github右上角点击**New repository**：
![enter description here](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRodWIuY29tL215aHVpYmJhb3FpL2NjYy9yYXcvbWFzdGVyLyVFNSVCMCU4RiVFNCVCOSVBNiVFNSU4QyVBMC8xNTYzNjgzMDk3Mzc1LnBuZw)

7.填写**name**，此处**仓库名**填到小书匠下图位置，**ur前缀**自动生成，确定：
![\[外链图片转存失败(img-hCPo4ChZ-1563684046521)(https://github.com/myhuibbaoqi/ccc/raw/master/小书匠/1563683145876.png)\]](https://img-blog.csdnimg.cn/20190721124221274.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
![\[外链图片转存失败(img-HwgQ8HWr-1563684046523)(https://github.com/myhuibbaoqi/ccc/raw/master/小书匠/1563683167861.png)\]](https://img-blog.csdnimg.cn/20190721124255624.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

8.最后选择刚刚建好的图床即可：
![enter description here](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRodWIuY29tL215aHVpYmJhb3FpL2NjYy9yYXcvbWFzdGVyLyVFNSVCMCU4RiVFNCVCOSVBNiVFNSU4QyVBMC8xNTYzNjgzMjc3NjgzLnBuZw)

- 完成图床绑定，截个图放入小书匠编辑框就可以发现github仓库中自动生成文件夹
![enter description here](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRodWIuY29tL215aHVpYmJhb3FpL2NjYy9yYXcvbWFzdGVyLyVFNSVCMCU4RiVFNCVCOSVBNiVFNSU4QyVBMC8xNTYzNjgzNDg1ODI0LnBuZw)
![enter description here](https://imgconvert.csdnimg.cn/aHR0cHM6Ly9naXRodWIuY29tL215aHVpYmJhb3FpL2NjYy9yYXcvbWFzdGVyLyVFNSVCMCU4RiVFNCVCOSVBNiVFNSU4QyVBMC8xNTYzNjgzNTEwMTQzLnBuZw)
- 上传的图片都保存在这里：
![\[外链图片转存失败(img-bfhJ4cwd-1563684046542)(https://github.com/myhuibbaoqi/ccc/raw/master/小书匠/1563683524024.png)\]](https://img-blog.csdnimg.cn/2019072112420060.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)

---

<center><font color=red size=5>github图床绑定已经完成了</font>

- 注意：但是我这边可能网络有问题，每次上传图片速度不是很好，同样感觉图片上传速度欠佳的小伙伴们可以尝试下方七牛云图床。

---

##  <center>七牛云图床绑定（建议使用）
- 小书匠中绑定位置与github绑定位置相同，此处不做介绍：
- 先去申请并实名认证一个七牛云账户（需要身份证照片）；
- 看到我们所需要填写的内容：共6个位置!![在这里插入图片描述](https://img-blog.csdnimg.cn/20190721135046894.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
1.左侧菜单栏选择对象存储-->**新建存储** -->填写下面内容；此处可以得到需填图的<font color=red>  4、1</font>
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190721135431167.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)2.创建完成点击右上角 **个人中心**--> **秘钥管理**得到 <font color=red>  2、3</font>
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190721135808173.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)![在这里插入图片描述](https://img-blog.csdnimg.cn/20190721135959667.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
3.不要用汉字作为图片后缀，容易乱码，文件名生成规则-->“**小书匠**”三个字改为“**blog**” 得到 <font color=red>  5</font>
  4.回到刚刚建好的储存空间中-->**内容管理**外联默认域名就是<font color=red>  6</font>
  ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190721140513291.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)<center><font color=red size=5>七牛云图床绑定已经完成了</font>

## 无水印本地图片上传得到图片外联地址
- 截图、复制、导入图片到小书匠编辑框自动生成图片外联，复制即可；
- 也可去七牛云的存储空间找上传的图片：
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190721141805260.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190721141621884.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzM5MjMxNzY5,size_16,color_FFFFFF,t_70)
