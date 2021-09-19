https://github.com/docker-solr/docker-solr
https://qiita.com/junk1400/items/4905a821638516dcb4fe

## 実行メモ
$ docker-compose up -d
$ docker exec -it solr-find-array-only_solr_1 bash

---
以下サーバで
$ solr create_core -c my_core

---
以下ローカルで
$ curl -X POST -H 'Content-type:application/json' -d my_core_schema.json http://localhost:8983/solr/my_core/schema
これだとなぜかエラーになる・・・

$ curl -X POST -H 'Content-type:application/json' --data-binary @my_core_schema.json http://localhost:8983/solr/my_core/schema
これでOK

$ curl -X POST -H 'Content-type:application/json' --data-binary '{"add-field" : {"name" : "name","type" : "string"},"add-field" : {"name" : "numbers","type" : "string","multiValued" : true}}' http://localhost:8983/solr/my_core/schema
これでもOK

データ投入
$ curl -X POST -H 'Content-type:application/json' --data-binary @my_core_data.json 'http://localhost:8983/solr/my_core/update?commit=true&indent=true'

全削除
$ curl -X POST -H 'Content-type:application/json' -d '{ delete: { query: "*:*" }}' 'http://localhost:8983/solr/my_core/update?commit=true'

検索
$ curl 'http://localhost:8983/solr/my_core/query?q=numbers:1'


できた
$ curl -g 'http://localhost:8983/solr/my_core/query?q=numbers:1+AND+NOT+numbers:{1+TO+*}+AND+NOT+numbers:{*+TO+1}'  




---
色々試す
$ curl 'http://localhost:8983/solr/my_core/query?q=numbers:2+AND+NOT+numbers:{2+TO+*}'


