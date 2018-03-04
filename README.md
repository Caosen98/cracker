# cracker
正则表达式在爬虫中的应用：
  主要是和bsobj.find()或者和bsobj.findall()函数配合，通过正则表达式regex来寻找有着相应属性的标签
      例子： bsObj.findAll("img",{"src":re.compile("\.\.\/img\/gifts/img.*\.jpg")}) 
     
一小段实例程序：
  from urllib.request import urlopen
from bs4 import BeautifulSoup
import re 
import os
os.chdir('C:\\users\\cao\\desktop')
html = urlopen("http://www.pythonscraping.com/pages/page3.html")
bsObj = BeautifulSoup(html)
images = bsObj.findAll("img",{"src":re.compile("\.\.\/img\/gifts/img.*\.jpg")})
with open('some_url.txt','w') as f:
    for image in images:
        f.write(image["src"]+'\n')

lambda匿名函数的作用：
  如果你觉得用正则表达式来检索信息是一件很难想的事情，那么采用lambda匿名函数也是个不错的选择，编程就像写书，一个句子这么写可以表达出来的意思，换一种写法也一定可以。
    例子：soup.findall(lambda tag : len(tag.attrs) == 2)
    注意lambda函数的参数必须是tag， 返回值必须是布尔值，或者是一个表达式，但该表达式的值也必须是布尔值。
