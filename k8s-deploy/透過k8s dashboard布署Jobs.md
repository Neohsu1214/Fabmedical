如果資料庫有初始化的需求的話，就必須使用Job來執行一次性的動作

* 透過 K8s Dashboard 新增 Job
1. 打開 K8s Dashboard
2. 點選右上角的＋
3. 選擇『輸入並建立』，並輸入以下內容 (以Fedmedical專案為例)
```yaml
apiVersion: batch/v1
kind: Job
metadata:
  name: init
spec:
  template:
    spec:
      containers:
      - name: init
        image: localhost:5000/content-init
        env:
          - name: MONGODB_CONNECTION
            value: mongodb://mongo:27017/contentdb
      restartPolicy: Never
  backoffLimit: 4
```
4. 點『上傳』後，即建立並執行該 Job