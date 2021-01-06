# Blockchain-based fair payment smart contract for public cloud storage auditing
![image](https://user-images.githubusercontent.com/68576770/103737698-078bf180-5036-11eb-8fe8-0d8bbff37ec8.png)
- 기존의 블록체인 기반 cloud storage auditing에서 verifier와 CSP가 interact해야하는 단점을 보완하여, smart contract와 csp가 컨트랙트를 실행할 때, 상호작용 없이, non-interactive하게 데이터를 입증하는 스키마
# System model - NIPPDP(Non-Interactive public provable data possession) scheme
### 1. Data owner
1) key generation : public key와 secret key 생성
2) tag generation : data file과 public key, secret key를 사용해 File에 대한 tag 생성
3) uploads file and tag : CSP로 file과 tag 업로드
4) submits contract : smart contract platform으로 contract(T0) 전송
  - ![image](https://user-images.githubusercontent.com/68576770/103742015-7a4c9b00-503d-11eb-9a5a-1414c880a3b7.png)
### 2. Cloud storage provider
5) proof generation : public key, data tags, data file 그리고 current state(time-varying public information)을 가지고 proof를 생성
  -  proving that the owner stores complete data 
6) submits contract : smart contract platform으로 contract(T1) 전송
  - ![image](https://user-images.githubusercontent.com/68576770/103742135-aec05700-503d-11eb-86b3-e768fffcbe9a.png)
##### Data Validation
7) submits contract : smart contract platform으로 contract(T2)를 주기적으로 전송
![image](https://user-images.githubusercontent.com/68576770/103743607-cac4f800-503f-11eb-939a-a79f5f454ce3.png)
  - 서비스 요금을 받기 위해 non-interactive data possession proof가 포함된 contract를 주기적으로 제출한다.
  - 그러면 smart contract platform의 consensus network에서 verify를 하여 유효성 검사를 진행한다.
    - 유효성 검사 성공시 T0 활성화 : data owner가 cloud server에 서비스 요금 지불
    - 유효성 검사 실패시 T1 활성화 : CPS가 data owner에게 패널티(보상) 지불
  ![image](https://user-images.githubusercontent.com/68576770/103743661-e3cda900-503f-11eb-87e2-2f31dd74b3b0.png)
### 3. Smart Contract Platform
1) verify : public key와 proof로 proof에 대한 correctness 여부를 판단하여 검증
  - 누구나 (publicly) verify할 수 있다.
# Reference
- Wang, Hao, et al. "Blockchain-based fair payment smart contract for public cloud storage auditing." Information Sciences 519 (2020): 348-362.
