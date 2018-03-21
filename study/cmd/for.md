# 1. for /f (解析文本)
## 1.1 切分字符串的利器：delims=
## 1.2 定点提取：tokens=
## 1.3 跳过无关内容，直奔主题：skip=n
## 1.4 忽略以指定字符打头的行：eol=
## 1.5 userbackq
## 1.5 变量延迟
## 示例：
for /f "eol=# delims=, tokens=1-3" %%i in (%~dp0repoInfo.txt) do command -- 用","切割, 获取第1,2,3   
for /f "eol=# delims=, tokens=1,*" %%i in (%~dp0repoInfo.txt) do command -- 用","切割, 获取第1和剩下所有的   
for /f "eol=# delims=, tokens=1,3,7" %%i in (%~dp0repoInfo.txt) do command -- 用","切割, 获取第1,3,7三个   

# 2. for /r (递归遍历)
## 格式: for /r 目录 %%i in (元素集合) do 命令语句集合
## 示例： 
for /r d:\test %%i in (.) do echo %%i -- 遍历指定目录d:\test和子目录下的所有文件和文件夹
for /r d:\test %%i in (*.txt) do echo %%i -- 列举 d:\test 及其所有子目录下的txt文本文件(以.txt结尾的文件夹不会被列出来)

# 3. for /d (遍历第一层目录, 不会搜索文件，也不搜索子目录)
## 示例：
for /d %%i in (test*) do @echo %i -- 列举当前目录下test开头的文件夹

# 4. for /l (计数循环)
## 格式1：FOR /L %variable IN (start,step,end) DO command [command-parameters]   
## 格式2：FOR /L %variable IN (start,step,end) DO command [command-parameters]    
## 格式3：FOR /L %variable IN (start,step,end) DO command [command-parameters]    
## 格式4：FOR /L %variable IN (start,step,end) DO command [command-parameters]    
该集表示以增量形式从开始到结束的一个数字序列。可以使用负的 Step 
## 示例： 
　　for /l %%i in (1,1,5) do @echo %%i --输出1 2 3 4 5    
　　for /l %%i in (1,2,10) do @echo %%i --输出1,3，5,7，9    
　　for /l %%i in (100,-20,1) do @echo %%i --输出100,80,60,40,20    
　　for /l %%i in (1,1,5) do start cmd --打开5个CMD窗口    
　　for /l %%i in (1,1,5) do md %%i --建立从1到5共5个文件夹    
　　for /l %%i in (1,1,5) do rd /q %%i --删除从1到5共5个文件夹   
  
# 5. for
切割符：逗号、空格、跳格或等号
## 示例：
for %%i in (bbs.bathome.net) do echo %%i -- 输出一行
for %%i in (bbs,bathome,net) do echo %%i -- 输出三行


# 6. Demo
## 6.1 扫描当前硬盘的分区
	@echo off
	set str=c d e f g h i j k l m n o p q r s t u v w x y z
	echo 当前硬盘的分区有：
	for %%i in (%str%) do if exist %%i: echo %%i:
	pause


reference:   
https://www.cnblogs.com/DswCnblog/p/5435300.html   
http://blog.csdn.net/wh_19910525/article/details/7912440
