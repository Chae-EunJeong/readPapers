<<<<<<< HEAD
# A Privacy-Preserving E-Commerce System Based on the Blockchain Technology
- 전자 상거래 시 일어나는 개인 정보 보호 문제를 해결하기 위해 영 지식 증명을 사용하여 소유권을 증명하는 프로토콜
# Problem statement
- 전자 상거래에서 사용자의 신원, 주소, 전화번호와 같은 개인 정보의 공개와 판매자의 리뷰(악의적리뷰/리뷰조작)에 관한 문제를 해결해야한다.
- 개인 정보를 모든 과정을 거칠때까지 보호할 모델이 필요하다.
# Privacy-preserving model based on the private smart contract technology
- 소유권 증명과 동시에 사용자의 개인 정보 보호
### Background
- cause : 기존 전자상거래 플랫폼에서 사용자의 개인 정보를 절대 보호하는 것은 불가능하기 때문에 변조가 불가능하고 추적할 수 있는 신뢰성을 갖춘 플랫폼이 필요하다. 또한, 구매자가 상품 수령 전에 소유권을 확보할 수 있는 Escrow protocol도 필요하다.
- scenario : Alice는 팔고자 하는 상품에 대한 소유권을 인증하고, 구매자 Bob은 그 상품을 사고싶어함과 동시에 그의 신원과 주소를 밝히고 싶지 않다.
### Business model based on blockchain 
![image](https://user-images.githubusercontent.com/68576770/110077202-1211ff80-7dc9-11eb-85f4-66ef2b176324.png)
##### Model composed of
1. CA(Certificate Authority)
- user들에게 PKI 기반 인증서 발급
  - 각 구성원들에게는 root certificate(rootCert) 발급
  - 권한이 부여된 사용자에게 enrollment certificate(ECert)를 발급
2. Clients(Users and logistics)
- Blockchain network 및 smart contract와 상호작용
- 네트워크의 애플리케이션 체인(채널)에 가입하기 전 CA로부터 유효한 identity certificate을 받아야함
3. Ledger
- smart contract와 상호작용하여 프로세스를 캡슐화함
4. Smart contract
- 이벤트 반응형이며 원장의 상태를 다룸
  - 참가자가 contract를 제출하면 상태가 바뀜
##### Improvement of model
- Ledger and Chain
  - Service-oriented chain 도입 : 특정 서비스의 트랜잭션만 포함됨
  - 세 가지 special chain 설계 
    - payment chain : note-contract가 실행되며, 사용자가 자금을 교환할 수 있음
    - trading chain : 상품의 note-contract를 추가하거나 업데이트함
    - logistic chain : 배송 단계에서 정보를 유지함
- Contract and Transaction
  - 이 모델에서 note-contract는 shielded transactions로 토큰화된 자산을 발행함 (note-contract : tokenized assets = 1 : 1)
  - note-contract는 main ledger에서 호스트하고, 여러 거래의 결제를 진행할 수 있음
  - 각 거래는 private contract로 표현되며, 거래 유형, 상대방, 기본 자산, 가격, 기타 매개 변수를 정의한다.
  - 트랜잭션 : 상태 전환을 나타냄
  - 클라이언트가 트랜잭션을 요청하면 ledger에 기록된다.
  - 거래시 사용자는 상대방에게 shielded transactions으로 note를 전송하여 전송 중에 외부로의 정보 노출을 막을 수 있다.

=> note-contract를 사용해 shielded transaction으로 토큰화된 자산을 발행한 사용자는 shielded transaction으로 note를 전송하면 privacy-preserving 가능

# Reference
Jiang, Yiming, et al. "A privacy-preserving e-commerce system based on the blockchain technology." 2019 IEEE International Workshop on Blockchain Oriented Software Engineering (IWBOSE). IEEE, 2019.
