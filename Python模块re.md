
### re.match()  
原型：match(pattern, string, flags=0)  
pattern: 匹配的正则表达式  
string:  要匹配的字符串  
flags:   标志位，用于控制正则表达式的匹配方式，如下：  
* **re.I  忽略大小写**
* re.L  做本地户识别
* **re.M  多行匹配，影响^和$**  
* **re.S  使.匹配包括换行符在内的所有字符**  
* **re.U  根据Unicode字符集解析字符，影响\w,\W,\b,\B**  
* re.X  使我们以更灵活的格式理解正则表达式      

功能： 从字符串开头匹配，返回从开始匹配成功的位置，若从开始未匹配到或不在开始位置匹配到，返回None


```python
import re
addr = "Www.baidu.com"
re.match("www", addr, re.I)
```




    <_sre.SRE_Match object; span=(0, 3), match='Www'>



### re.search()
原型：search(pattern, string, flags=0)  
功能：扫描整个字符串，并返回第一个成功的匹配


```python
import re
addr = "www.baidu.com"
print(re.match("bai", addr))
print(re.search("bai", addr))
```

    None
    <_sre.SRE_Match object; span=(4, 7), match='bai'>
    

### re.findall()
原型： findall(pattern, string, flafs=0)  
功能： 扫描整个字符串，并返回所有结果的列表


```python
import re
addr = "www.baidu.com"
print(re.findall("w", addr))
```

    ['w', 'w', 'w']
    

### 字符串切割


```python
import re
str1 = 'wang    is a good man'
print(str1.split())
print(str1.split(" "))
print(re.split(r" +", str1))
```

    ['wang', 'is', 'a', 'good', 'man']
    ['wang', '', '', '', 'is', 'a', 'good', 'man']
    ['wang', 'is', 'a', 'good', 'man']
    

### re.finditer()
原型： finditer(pattern, string, flags=0)  
功能： 与findall类似，扫描整个字符串，但返回的是一个迭代器  


```python
import re
strs = "wang is a good man! wang is a nice man! wang is a very handsome man!"
d = re.finditer(r"wang", strs)
for i in d:
    print(i.group())
```

    wang
    wang
    wang
    

### 字符串的替换和修改
**sub(pattern, repl, string, count=0, flags=0)  
subn(pattern, repl, string, count=0, flags=0) **
* pattern: 正则
* repl: 指定的用来替换的字符串
* string: 目标字符串
* count: 最多替换次数，默认为0，表示替换所有匹配到的字符串
* 功能： 在目标字符串中以正则匹配字符串，把匹配到的替换成指定字符串


```python
import re
str2 = "wang is a good good good boy"
print(re.sub("good", "nice", str2))
print(re.subn("good", "nice", str2, count=2))
```

    wang is a nice nice nice boy
    ('wang is a nice nice good boy', 2)
    


```python
import re
pat = r'^1(([3578]\d)|(47))\d{8}$'
re_tele = re.compile(pat)
print(re_tele.match("13600000000").group())
```

    13600000000
    
