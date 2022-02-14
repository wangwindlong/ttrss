Tiny Tiny RSS
=============

Web-based news feed aggregator, designed to allow you to read news from 
any location, while feeling as close to a real desktop application as possible.

http://tt-rss.org

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

Copyright (c) 2005 Andrew Dolgov (unless explicitly stated otherwise).

source deploy <https://tt-rss.org/wiki/InstallationNotesHost> 

[Other Reference](https://phower.me/2020/03/Tiny%20Tiny%20RSS%20%E5%AE%89%E8%A3%85%E5%8F%8A%E5%A1%AB%E5%9D%91%E4%B9%8B%E8%B7%AF/#%E6%9C%8D%E5%8A%A1%E5%99%A8%E9%85%8D%E7%BD%AE)

[个人部署笔记](http://wangyl.work/#root/MrExmyhOFh1c/KuPLaGRvkv5I-2QrY)

[ttrss android](https://github.com/wangwindlong/tt-rss-android)

# 部署
### cp config.php-dist config.php   [参考](https://tt-rss.org/wiki/GlobalConfig)

```
putenv('TTRSS_DB_TYPE=mysql');
putenv('TTRSS_DB_PORT=3306');
putenv('TTRSS_DB_HOST=dbhost');
putenv('TTRSS_DB_NAME=dbname');
putenv('TTRSS_DB_USER=dbuser');
putenv('TTRSS_DB_PASS=dbpassword');
putenv('TTRSS_SELF_URL_PATH=https://example.com/tt-rss');
putenv('TTRSS_SIMPLE_UPDATE_MODE=true');
putenv('TTRSS_SESSION_COOKIE_LIFETIME='.(86400*30));
```

php ./update.php --update-schema

https://example.com/tt-rss  admin | password

#配置 + 插件 [参考](https://ttrss.henry.wang/zh) 
* 插件 [feedly主题](https://github.com/levito/tt-rss-feedly-theme)
* 插件mercury_fulltext [加载全文插件](https://github.com/HenryQW/mercury_fulltext)
* RSSHUB [源码](https://github.com/DIYgod/RSSHub)    [RSS源](https://docs.rsshub.app/)


#自动更新文章 [参考](https://git.tt-rss.org/fox/tt-rss/wiki/UpdatingFeeds)
### 一、以systemd方式运行
vi /etc/systemd/system/ttrss_backend.service

```
[Unit]
Description=ttrss_backend
#mysql.service #postgresql.service
After=network.target mysql.service

[Service]
User=www-data
ExecStart=/var/www/html/ttrss/update_daemon2.php

[Install]
WantedBy=multi-user.target
```
* sudo systemctl enable ttrss_backend
* sudo systemctl start ttrss_backend
* sudo systemctl status ttrss_backend
* sudo journalctl -u ttrss_backend

### 二、以crontab方式运行
sudo crontab -u www-data -e
*/30 * * * * /usr/bin/php /var/www/html/ttrss/update.php --feeds --quiet

### 三、每次打开web页面时加载
config.php中增加配置
putenv('TTRSS_SIMPLE_UPDATE_MODE=true');

# 其他信息
* Forum: http://tt-rss.org/forum
* web code: https://github.com/wangwindlong/ttrss
* official install guide: https://tt-rss.org/wiki/InstallationNotes
* origin android code: https://git.tt-rss.org/fox/tt-rss-android
* origin web code: https://git.tt-rss.org/fox/tt-rss/src/branch/master

