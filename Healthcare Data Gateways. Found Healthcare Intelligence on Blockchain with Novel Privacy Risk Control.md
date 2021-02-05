# Healthcare Data Gateways: Found Healthcare Intelligence on Blockchain with Novel Privacy Risk Control
- 개체마다 HDG(Healthcare Data Gateways)를 이용해 제 3자를 신뢰할 필요 없이 자신의 의료 데이터에 대한 권한을 가지도록 하여 EMR(Electronic Medical Record)에 대한 privacy를 보호하면서 데이터를 공유하는 방법
- concerns both sharing data and patient privacy
# HDG-centric healthcare ecosystem
![image](https://user-images.githubusercontent.com/68576770/107001132-7347b280-67cc-11eb-80e7-7cdb1d720892.png)
### Secure Data Storage Layer
- blockchain platform을 storage system으로 활용
    - data가 immutable함
    - cryptographic으로 data 보호
### Data Management Layer
- HDG
- Data gateway = firewall + database
    - firewall : evaluates access requests
    - database : manage patient's data and other's data
- HDG는 또한 metadata(지표, 스키마)도 다룬다. (data와는 다르게 취급)
### Data Usage Layer
- 환자의 data를 사용하는 주체들
    - ex) electronic medical record systems, other's HDG, physicians
