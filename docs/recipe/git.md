## git的应用
### 
```js
(1)crontab -e
* * * * * /www/wwwroot/zdomin.com/noteday/update.sh >> /www/wwwroot/zdomin.com/noteday/log

(2)
sudo echo "*/5 * * * * /tmp/produce.sh" > /tmp/time
crontab /tmp/time

(3)crontab -e
查看定时器
```