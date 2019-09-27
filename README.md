# Pascal-VOC-standardizing
关于调参方面的总结可以参考https://nanfei.xyz/2018/01/23/%E8%B0%83%E5%8F%82%E6%80%BB%E7%BB%93/#more
## changedata.py
changedata的代码用于批量修改xml文件中的一些数据，如果要使用，修改file_dir为自己的目录并且将之后修改数据的逻辑换成在自己的即可，我这里做的是读取全图的宽度并且取一个比例以后加上xmin，取代原来的xmax，是项目需求所要求的。
## changetogray.py
将三通道换成灰度图
## changewhite.py
黑白互换
## copybyfilename.py
通过文件名复制文件到指定目录。
## deletebyfilename.py
通过文件名删除文件
## deletebyfoldername.py
递归删除指定名字的文件夹及里边的文件
## deletedata.py
这是用来删除一些类别的标注的，需要减少类别的时候可以使用。
## examinelei.py
检查有没有多余的类别
## examinesize.py
有时候xml中的宽和高损失了，导致训练无法正常进行，这里利用python的cv2这个包进行修正
## imagestandardizing.py
最近遇到了传输遇到图片损坏或者编码不规范的情况，低版本opencv不能读（由于我没有服务器的root权限因此），我查到的比较好的处理方法是用高版本opencv读入这些有问题的图片（可能会有warning，不用管他），再重新写一遍，这样图片就规范了。
## printbyfilename.py
打印文件夹中所有的文件名到一个txt文件里。
## k_means_yolo.py
yolo-voc.cfg中的anchors参数为预设的ImageNet中的anchors聚类结果。（yolo对fast-rcnn优化之一就是使用聚类的anchors替换了原来手工挑选的anchors，使得mAP提高了1%~2%），然而，对于自己的训练集，就需要重新聚类了。修改该文件的路径即可。
## rename.py
用6位数字重命名指定目录下的文件
## sortxml.py
将标注按照x轴从上到下排序
## standard.py
standard的代码用来将file_dir子目录下的所有xml中的路径替换成darknet中要求的路径格式（这个路径还要根据自己darknet的安装目录调整，修改change_dir即可），同时后缀统一成了jpg，要注意如果图片文件里有大写的JPG那么要修改为小写，否则不认，推荐使用ReNamer进行批量的重命名序列化等操作。
## widerdata.py
由于yolo对于小物体的处理很不好，因此我这边尝试将它的标注的bounding box放大试一试。
