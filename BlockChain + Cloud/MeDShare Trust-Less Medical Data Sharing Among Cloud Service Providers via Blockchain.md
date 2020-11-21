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
- 키를 사용해 confidentiality를 보장하여 보안성을 높임
    - MedShare에서는 데이터 공유시 쿼리 결과의 안전한 전송을 위해 키 사용
- 키 사용 과정
    - 요청
        - data owner의 records에 접근하고 싶은 requestor가 key pair 생성
        - requestor의 private key는 저장해놓고 public key를
        - requestor는 자신의 private key로 서명한 후 data owner에게 요청
        - data owner가 수신을 하면 requestor의 public key로 서명 검증 후 요청 확인
    - 공유
        - 요청한 데이터에 대한 결과는 데이터에 태그가 지정되고(tagged), 추가로 처리(processed)
        - data owner는 authenticator contract key로 전체 패키지를 암호화할 후 requestor와 공유(encrypt and share) - 
        - requestor가 수신하면, decrypt해서 해당 데이터 사용
    - requestor로부터 data owner에게 데이터에 대해 수행된 actions의 전송을 안전하게 하기 위해서, 데이터에 플래그가 붙은 암호화 함수로부터 생성된 actions의 report는, data owner로부터 생성된 contracts에 태그된 authenticator contract key를 사용해 암호화되어야하며, 보안된 database로 전송되어야한다.
### C. Triggers
- query 구조와 블록체인 환경 사이의 프로세스들을 연결하는 entity
- smart contract가 시스템 외부에서 MedShare 시스템으로 직접 연결될 수 있도록 구현
    - Data Query Layer와 Data Structuring and Provenance Layer 사이의 중개자 역할
# System Model
* 1) User layer : 연구를 목적으로 데이터를 분석하기 위해 데이터에 접근하는 모든 사용자 부류
    - ex) hospitals, research institutions, universities, government bodies
* 2) Data Query layer : 