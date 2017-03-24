## gradlew常用命令
<ul>
<li>gradlew -v 版本号</li>
<li>gradlew clean 清除工程目录下的build文件夹</li>
<li>gradlew build 检查依赖并编译打包</li>
</ul>
这里注意的是 ./gradlew build 命令把debug、release环境的包都打出来，如果正式发布只需要打Release的包，该怎么办呢，下面介绍一个很有用的命令 assemble, 如

<ul>
<li>gradlew assembleDebug 编译并打Debug包</li>
<li>gradlew assembleRelease 编译并打Release的包</li>
</ul>

### gradlew用于buildeclispe的bat脚本如下
cd %~dp0
call gradlew clean
cd %~dp0

cd %~dp0
call gradlew eclipse
cd %~dp0

## 学习springboot
网址：https://spring.io/
