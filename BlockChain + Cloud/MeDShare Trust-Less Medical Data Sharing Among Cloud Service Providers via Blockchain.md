# MeDShare: Trust-Less Medical Data Sharing Among Cloud Service Providers via Blockchain
- 데이터에 대한 data provenance, auditing, 그리고 control을 제공하는 시스템이며, smart contract와 access control mechanism으로 data의 behavior를 추적하고, 권한 위반 감지시 access를 revoke한다.
# Problem statement
- 데이터 보급과 클라우드 스토리지에 대한 관심이 증가했으며, 클라우드 서비스 제공자는 데이터 제어와 유연한 데이터 공유 제공의 의므를 가진다.
- (문제 : 데이터 통제력 상실)데이터가 관리자 시스템을 벗어나면, 제어가 더이상 불가능해지며, 데이터 남용과 여러 법적 문제가 발생할 수 있다.
- 대책으로는 암호화방법이 있으나 문제 해결을 위해 충분하지 않다.
- 블록체인이 가진 특징들을 사용해 적합한 솔루션을 찾는 것이 가능하다.
### A. Blockchain Network
### B. Cryptographic Keys
- Requestor private key : 데이터 접근 요청에 서명할 때
- Requestor public key : 데이터 소유자에게 전송되는 공개키이자, authenticator가 패키지를 요청자에게 보낼 때 사용
- Authenticator contract key : report를 암호화할 때 쓰이는 패키지의 smart contract에 첨부됨
### C. Triggers
