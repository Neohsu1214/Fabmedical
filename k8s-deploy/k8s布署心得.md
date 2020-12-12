今天接續著昨天Workshop沒做完的事情，在Mac上做了以下事情
1. 安裝Docker Desktop for Mac
2. 在 Docker Desktop for Mac上啟動k8s
3. 安裝 Docker Registry 並啟動(k8s不吃local registry)
4. 將昨天Workshop的三個專案pull下來，建置成Docker image
5. 將4.的 Docker image 都 push 到 Docker Registry 服務
6. 於 k8s 安裝 Dashboard
7. 透過 Dashboard Form 建立 mongo  的 pod
8. 透過 Dashboard Form 建立 web  的 pod
9. 透過 Dashboard Form 建立 api 的 pod
10. 透過 Dashboard 輸入 init資料庫的yaml 內容建立 Job
11. 透過 kubectl 備份 mongo, web, api, init 的布署 yaml
12. 把玩 ReplicaSet 的縮放機制 