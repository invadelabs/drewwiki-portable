drewwiki-portable
=================
Spin up [DrewWiki](https://drew.invadelabs.com) from MediaWiki official Docker container in a pinch.

## Extract LocalSettings.php and drew_wiki.sqlite
```
tar -Jxvf ~/Google\ Drive/Backup/Web/invadelabs.com.20180219232926.tar.xz drew_wiki.sqlite LocalSettings.php
```

## Comment out of LocalSettings.php
```
###require_once "$IP/extensions/googleAnalytics/googleAnalytics.php";
### $wgArticlePath = "/$1";
### require_once "$IP/extensions/OpenGraphMeta/OpenGraphMeta.php";
### require_once "$IP/extensions/Description2/Description2.php";
```

## Start the container
```
docker run --name drewwiki \
-p 8080:80 \
-v $(pwd)/LocalSettings.php:/var/www/html/LocalSettings.php \
-v $(pwd)/omgz_square.gif:/var/www/html/omgz_square.gif \
-v $(pwd)/drew_wiki.sqlite:/var/www/data/drew_wiki.sqlite \
-d \
mediawiki
```

## Browse to
[http://localhost:8080](http://localhost:8080)
