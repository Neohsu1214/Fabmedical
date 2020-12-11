此專案為微軟 Azure Cloud Native in a Day 的演示範例

專案來源：https://github.com/microsoft/Cloud-Native-In-a-Day

資料夾/檔案 說明

* content-api: 演示範例前端，為Angular的npm專案
* content-init: 演示範例資料初始化到mongodb的ETL，為npm專案
* content-api: 演示範例後端API，為 express 的 npm專案
* .github/workflows: 當github偵測到此目錄，會觸發CI機制產出 Docker image(當然專案包裡要有Dockerfile)，並可設定要將 Docker image push 到哪個 Docker Registry
* docker-compose.yml: 一次布署多個container的yml檔
1. 可透過以下指令把一群container叫起來
```
docker-compose -f docker-compose.yml -p fabmedical up -d
fabmedical為自行建立的network名稱(docker network create fabmedical)
```

2. 可透過以下指令把 1. 的同一群 container 關掉
```
docker-compose -f docker-compose.yml -p fabmedical down
```
* docker-compose.init.yml: 一次布署初始化資料container的yml檔
* 課程註記.txt: 課程中要點的筆記（超讚）