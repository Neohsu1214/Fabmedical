當 k8s Dashboard 可以登入後
可參考以下步驟一步一步建立服務

* 從表單建立服務
1. 點擊右上角的＋號
2. 點選『從表單建立』
```
應用名稱: mongo
容器映像檔: mongo (預設會從Dockerhub抓下來)
Service: Internal (如果DB沒有要開放外部存取的話)
    27071:27071
環境變數: 如果有需要特別加到container內的linux環境變數，要在這邊加上去
```

* 修改已布署服務之Deployment yaml檔內容，使可連線到需要的服務
1. 假如我們布署一個 api 如下
```
應用名稱: api
容器映像檔: localhost:5000/content-api
Service: Internal 
    3001:3001
```
2. 但是我們忘記給定環境變數，或者我們想要利用原本的布署資訊再增加內容，則可以透過以下指令取得 Deployment 的 yaml 內容
```bash
kubectl get -o=yaml --export=true deployment api > api.deployment.k8s.yaml
或者也可以透過 dashboard 的 Deployment 點選編輯後查看複製，但此方法不適用於CLI
```
3. 如此即可修改yaml檔內容來增加其他資訊後，透過dashboard來讀取yaml檔進行布署...要先刪除原有的 Deployment 後才能再重新布署！
4. 也可以透過以下指令直接讀取 yaml 檔內容進行布署
```bash
kubectl apply -f api.deployment.k8s.yaml 
```
