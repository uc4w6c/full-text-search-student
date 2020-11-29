## 起動方法
$ sudo docker run --rm -p 8983:8983 -p 7574:7574 --name solr-hello -it solr-hello /bin/bash
$ cd /usr/local/src/solr-8.7.0/bin/
$ ./solr start -e cloud -force
$ cd /usr/local/src/solr-8.7.0/example/exampledocs/
$ post -c gettingstarted *.xml
$ post -c gettingstarted *.json
$ post -c gettingstarted *.csv

$ curl "http://localhost:8983/solr/gettingstarted/select?q=manu_id_s:corsair&wt=json&indent=true"

## 参考
- https://qiita.com/Esfahan/items/8b125be1ac16f5414d4e


