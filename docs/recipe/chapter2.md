## linux的应用
### crontab定时器
```js
(1)crontab -e
* * * * * /www/wwwroot/zdomin.com/noteday/update.sh >> /www/wwwroot/zdomin.com/noteday/log

(2)
sudo echo "*/5 * * * * /tmp/produce.sh" > /tmp/time
crontab /tmp/time

(3)crontab -e
查看定时器
```
### 控制该项目在后台进行
```js
（1）$ nohup java -jar test.jar & 
//nohup 意思是不挂断运行命令,当账户退出或终端关闭时,程序仍然运行 
//当用 nohup 命令执行作业时，缺省情况下该作业的所有输出被重定向到nohup.out的文件中 //除非另外指定了输出文件。	
（2）$ nohup java -jar test.jar >temp.txt & 
//这种方法会把日志文件输入到你指定的文件中，没有则会自动创建
（3）$ nohup java -jar test.jar >temp.txt &
//根据端口查看后台进程程序
（4）ps 进程号
//查看进程的详细信息
（5）kill -9 进程号
//杀死进程，-9 表示强迫进程立即停止
（6）$ jobs 
//那么就会列出所有后台执行的作业，并且每个作业前面都有个编号。
（7） $ fg 2
 //如果想将某个作业调回前台控制，只需要 fg + 编号即可。
```

### 查看端口号
```js
netstat -tnlp | grep :22
```
