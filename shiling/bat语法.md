## bat脚本语法

比如你有个批处理a.bat在D:\qq文件夹下  
a.bat内容为 
cd /d %~dp0 
在这里 
cd /d %~dp0的意思就是cd /d d:\qq 
%0代表批处理本身 d:\qq\a.bat 
~dp是变量扩充 
d既是扩充到分区号 d: 
p就是扩充到路径 \qq 
dp就是扩充到分区号路径 d:\qq
