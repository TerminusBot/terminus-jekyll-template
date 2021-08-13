---

layout: post

title: [自己动手作词云](https://mp.weixin.qq.com/s?__biz=MzA3MDQ2NzE5Mw==&mid=2652773538&idx=1&sn=efb9d44740ca41b39479bbf8c9a8db96&chksm=84d6d7b4b3a15ea2f8d7baeb3750b5cd06f225c6de0afd5e6f3f40ccc97a339aebdc18108490&token=184373101&lang=zh_CN#rd)  

date: 2020-08-29

categories: Archive

tags: 词云；python

---


市面上自动生成的词云网站挺多的，但是因为之前做过python的词云，觉得自定义会更自如一些（其实就是复习一下，不然全忘了），就用昨天爬取的数据来试验一下。



因为重装电脑的原因，许多文件出现了问题，所以这里从0开始



首先cmd安装jieba和wordcloud





安装jieba时出现问题





使用镜像网站重试





完美解决



将已经爬取到的csv文件转为txt文本记下存储路径





准备工作就绪



第一步准备好字符串文本

引入第三方库，打开信息文件对应的位置，进行网页编码

使用jieba进行分词

使用空格将列表元素联系起来，形成由空格分隔的长字符串
```
>>> import jieba
>>> import wordcloud
>>> f = open(r"D:\龟峰.txt","r",encoding="utf-8")
>>> t = f.read()
>>> f.close()
>>> ls = jieba.lcut(t)
>>> txt ="".join(ls)
```

第二步生成词云对象

设置字体，生成图片的长宽，导出图片即可
```
w = wordcloud.WordCloud( \
    width = 1000, height = 700,\
    background_color = "white",
    font_path = "msyh.ttc"
    )
w.generate(txt)
w.to_file("grwordcloud.png")
```

文件自动存储在写python的文件夹里





最终结果如图







从里面还可以看到龙虎山和三清山哈哈



因为龟峰是丹霞地貌所以山不高，但奇形怪状。与韶关的丹霞山相比景区较小，造型比较精致，除去各种经典的乌龟小品外，厕所也设计的十分考量。玻璃栈道靠山处贴心的做了一条木质实心路，安全感up，up，up，哈哈哈。



这里尝试用让所有字都在龟峰字里呈现



在ps里生成一张龟峰字样的图片并导出







接着只需引入imread更改3处代码即可
```
import jieba
import wordcloud
from scipy.misc import imread
mask = imread("guifeng.jpg")
excludes = { }
f = open(r'D:\龟峰.txt', encoding="utf-8")

t = f.read()
f.close()
ls = jieba.lcut(t)

txt = " ".join(ls)
w = wordcloud.WordCloud( \
    width = 1000, height = 700,\
    background_color = "white",
    font_path = "msyh.ttc", mask = mask  
    )
w.generate(txt)
w.to_file("guifeng.png")
```


运行代码一直报错





根据报错提示去安装scipy



然后在安装imread时出现了错误





根据提示下载了微软的Visual（可是明明我电脑里已经有了n个版本了。。。）





又下载了一个









正在安装（默认值）







结果！！！依然报错







决定不折腾了曲线救国，安装imageio从这个库里调用imread







更改代码为
```
from imageio import imread
```

再次运行







成功！



打开文件夹查看



哈哈哈哈哈哈哈，字体大小什么应该改一下的，好好笑噢



更多好玩的，下次再探索~
