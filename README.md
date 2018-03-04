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
