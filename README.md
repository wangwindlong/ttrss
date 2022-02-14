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

[My note](http://wangyl.work/#root/MrExmyhOFh1c/KuPLaGRvkv5I-2QrY)

[ttrss android](https://github.com/wangwindlong/tt-rss-android)

cp config.php-dist config.php   [参考](https://tt-rss.org/wiki/GlobalConfig)

```
putenv('TTRSS_DB_TYPE=mysql');
putenv('TTRSS_DB_PORT=3306');
putenv('TTRSS_DB_HOST=dbhost');
putenv('TTRSS_DB_NAME=dbname');
putenv('TTRSS_DB_USER=dbuser');
putenv('TTRSS_DB_PASS=dbpassword');
putenv('TTRSS_SELF_URL_PATH=https://example.com/tt-rss');
```

php ./update.php --update-schema

https://example.com/tt-rss  admin | password

* Forum: http://tt-rss.org/forum
* web code: https://github.com/wangwindlong/ttrss
* official install guide: https://tt-rss.org/wiki/InstallationNotes
* origin android code: https://git.tt-rss.org/fox/tt-rss-android
* origin web code: https://git.tt-rss.org/fox/tt-rss/src/branch/master

