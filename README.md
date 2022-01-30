# Kubernetes-Demo
Developed a Fronend php app and connected in to the Backend database server using kubernetes

Commands used : kubectl exec -it pod-id bash

kubectl get services;

kubectl get pods;


farooqui@Farooqui-Vostro:~/Documents/Projects/Kubernetes-Demo$ kubectl get services
NAME              TYPE           CLUSTER-IP      EXTERNAL-IP                                                              PORT(S)          AGE
angular-app-svc   LoadBalancer   10.100.147.49   a265b719425d74c26bc737fa17cc8981-818505107.us-east-2.elb.amazonaws.com   8085:31052/TCP   11d
kubernetes        ClusterIP      10.100.0.1      <none>                                                                   443/TCP          14d
webapp-sql        LoadBalancer   10.100.5.170    a5d139aa8492648dd8fe47391bae1d9d-342123394.us-east-2.elb.amazonaws.com   80:32305/TCP     114m
webapp-sql1       ClusterIP      None            <none>                                                                   3306/TCP         107m
farooqui@Farooqui-Vostro:~/Documents/Projects/Kubernetes-Demo$ kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE
my-ak-deployment-7d76966ff4-dwzcg   1/1     Running   0          11d
my-ak-deployment-7d76966ff4-qpz8m   1/1     Running   0          11d
sqldb-74c987f4f6-r6fls              1/1     Running   0          120m
webapp1-6b7b4cdbd8-r89r7            1/1     Running   0          145m
farooqui@Farooqui-Vostro:~/Documents/Projects/Kubernetes-Demo$ kubectl exec -it webapp1-6b7b4cdbd8-r89r7 bash
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
root@webapp1-6b7b4cdbd8-r89r7:/# nano var/www/html/index.php
root@webapp1-6b7b4cdbd8-r89r7:/# 
  
  ---------------------------------------------------------------------------------------------------------------------------------------------------
  
  Contents from database container :
  
  farooqui@Farooqui-Vostro:~/Documents/Projects/Kubernetes-Demo$ kubectl exec -it sqldb-74c987f4f6-r6fls bash
kubectl exec [POD] [COMMAND] is DEPRECATED and will be removed in a future version. Use kubectl exec [POD] -- [COMMAND] instead.
root@sqldb-74c987f4f6-r6fls:/# mysql -u ************* -p******************
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 38
Server version: 5.5.60 MySQL Community Server (GPL)

Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| Product_Details    |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.00 sec)

mysql> use Product_Details;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+---------------------------+
| Tables_in_Product_Details |
+---------------------------+
| product                   |
+---------------------------+
1 row in set (0.00 sec)

mysql> select *from product;
+-----------------+--------------+
| product_name    | product_id   |
+-----------------+--------------+
| AirCondition    | AC89328712   |
| Refrigerator    | RF2586322    |
| Gyser           | GY097865     |
| Washing Machine | WS0892552322 |
| Washing Machine | WS0892552322 |
| Led             | Ld8976555    |
+-----------------+--------------+
6 rows in set (0.00 sec)

mysql> exit
Bye
root@sqldb-74c987f4f6-r6fls:/# exit
exit
farooqui@Farooqui-Vostro:~/Documents/Projects/Kubernetes-Demo$ 




