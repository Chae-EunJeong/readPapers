# Blockchain Access Control Ecosystem for Big Data Security

# BIBAC vs BRBAC
### BIBAC(Blockchain Identity-Based Access Control)
![image](https://user-images.githubusercontent.com/68576770/101443829-9fc48700-3961-11eb-8ab5-eb7b84dba3f4.png)
- 사용자별로 접근 권한을 부여(user-by-user)
- asset의 owner가 언제든지 접근을 허용하거나 거부할 수 있다.
- consists of : person(participant), data(asset), request, grant, revoke, verify, and view.
- 자신의 asset을 보거나 보려고 시도한 사람을 business network  history로 볼 수 있어서, auditability와 integrity를 허용하여 데이터 침해로부터 보호한다.
### BRBAC(Blockchain Role-Based Access Control)
![image](https://user-images.githubusercontent.com/68576770/101445262-883acd80-3964-11eb-8aaf-e5ef96ba1d36.png)
- 사용자에게는 역할이 할당되고 역할에는 권한이 할당된다.
- 사용자가 asset을 보려고 요청하면, smart contract는 그 자산에 대한 권한이 있는 역할이 있는지 확인한다.
- consists of : person and organization(participant), data(asset), request, grant, revoke, verify, and view.