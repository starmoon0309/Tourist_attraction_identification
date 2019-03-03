# Tourist_attraction_identification
本项目在tensorflow下使用CNN解决景点识别问题，作者只是一个刚刚入门深度学习的新手，本文主要用来记录自己的学习历程，很多问题可能也无法回答，见谅。
本项目大量参考了 https://github.com/bighansome/flower_world 的代码，并对我在此项目中出现的问题进行说明，其中也参考了大量CSDN博主的方法
，还望各位大神不吝赐教<br>
（非商业用途，仅供学习，若有侵权，请告知我，我将立即删除）<br>
<br>
<br>
<br>
<br>
## 本机环境 
Win10 + python3.6 + pycharm + tensorflow-gpu 1.3.0 <br>
<br>
<br>
下面简单介绍一下整个流程：<br>
- 首先，从网站上批量下载景点的图片。我选用4个景点，分别是泰山，大雁塔，兵马俑，颐和园。一共下载了共计804张图片(有点少) <br>
- 调用create_record.py进行图片处理，这里主要是将图片转换为64×64像素的图片。在这一步中我出现了如下的问题()<br>
1.运行时报错 NewRandomAccessFile failed to Create/Open<br>
解决方法：文件夹没有创建出来，所以将文件夹在运行的位置创建出来就好了<br>
2.运行时报错 InvalidArgumentError (see above for traceback): Input to reshape is a tensor with xx values, but the requested shape has xx<br>
解决方法：在create_record.py中的img = Image.open(img_path)后加上了“.convert("RGB")”,强制都转成RGB格式，就好了(困扰了我很久)<br>
3.特别注意，文件的路径上不要有中文名！！！忘了报的错是什么了<br>
- 运行train.py，需要注意的是train_dir和logs_train_dir需要改成本机的目录。大约训练8~10分钟左右，可以在/save目录下得到训练好的模型
