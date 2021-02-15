# Healthcare Data Gateways: Found Healthcare Intelligence on Blockchain with Novel Privacy Risk Control
- 개체마다 HDG(Healthcare Data Gateways)를 이용해 제 3자를 신뢰할 필요 없이 자신의 의료 데이터에 대한 권한을 가지도록 하여 EMR(Electronic Medical Record)에 대한 privacy를 보호하면서 데이터를 공유하는 방법
- concerns both sharing data and patient privacy
# HDG-centric healthcare ecosystem
![image](https://user-images.githubusercontent.com/68576770/107001132-7347b280-67cc-11eb-80e7-7cdb1d720892.png)
### 1. Secure Data Storage Layer
- blockchain platform을 storage system으로 활용
    - data가 immutable함
    - cryptographic으로 data 보호
### 2. Data Management Layer
- HDG
- Data gateway = firewall + database
    - firewall : evaluates access requests
    - database : manage patient's data and other's data
- HDG는 또한 metadata(지표, 스키마)도 다룬다. (data와는 다르게 취급)
- HDG에서는 random값을 이용해서 counting function을 구성
    - HDG 소유자는 보호하면서 counting 결과는 얻을 수 있음(보건복지부 통계 등에 쓰일 경우)
- Indicator-centric schema를 storage model로 사용하여 simple하고 unified하게 user가 사용 가능
- purpose-centric access control model 제안
    - access의 목적을 둘로 나눔
        - 1) raw purpose : 의사가 진단을 위해 환자의 데이터가 필요할 때 등은 원래의 data에 접근해야한다.
        - 2) process purpose : to derive some results. 보건복지부에서 총 합계를 구할 때와 같이 raw data가 필요한 것이 아니라 그것들을 활용한 결과가 필요할 때에 해당하는 목적
    - r-users와 p-users로 나누어 data query가 발행된다.(다른 정책 사용)
    - p-users에서는 data의 privacy가 지켜져야하므로 blockchain network내에서 결과를 도출하는 computation을 진행
### 3. Data Usage Layer
- 환자의 data를 사용하는 주체들
    - ex) electronic medical record systems, other's HDG, physicians
