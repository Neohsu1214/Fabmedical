建立私有的 Docker Registry

* 參考文件
```url
https://hub.docker.com/_/registry
```

* 緣起

因為k8s必須從可存取的 Docker Registry 拿到 docker image 才能進行布署的動作
因此要建立私有的 Docker Registry

* 建立方法
```bash
docker run -d -p 5000:5000 --restart always --name registry registry:2
```

* 如何將已存在local registry 的 docker image push進去？
```
docker image tag 本地image名稱 localhost:5000/遠方image名稱
docker image push localhost:5000/遠方image名稱
```