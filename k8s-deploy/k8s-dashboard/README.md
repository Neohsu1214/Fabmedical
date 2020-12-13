建立k8s dashboard

* 參考文件
```URL
https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/
```

文件中提到的URL如果必須透過proxy取得，則要先下載下來，以下的流程都是先下載下來後執行的說明

* 執行步驟
1. 建立k8s Dashboard 服務
```
 kubectl apply -f .\recommended.yaml
```
如此則會在

2. 建立k8s的 service-account: admin-user
```
kubectl.exe apply -f .\create-service-account.yaml
```

3. 建立k8s的 Cluster Role Binding機制
```
kubectl.exe apply -f .\create-cluster-role-binding.yaml
```

4. 取得 admin-user 的 Bearer token

Bash版
```bash
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')
```

Powershell版
```Powershell
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | sls admin-user | ForEach-Object { $_ -Split '\s+' } | Select -First 1)
```

5. 建立 k8s 對外的 proxy
```
kubectl proxy
```
預設是開啟 8001

6. 以瀏覽器開啟 k8s Dashboard URL

http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

此時會出現登入畫面，要求輸入 token

7. 輸入步驟4取得的 token 後即可登入