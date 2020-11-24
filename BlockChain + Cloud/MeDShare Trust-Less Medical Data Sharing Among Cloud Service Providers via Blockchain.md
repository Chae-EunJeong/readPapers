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
* 2) Data Query layer : 시스템의 쿼리에 접근, 처리, 전달, 응답하는 쿼리 구조의 집합(sets of querying structures)으로 구성되어있다. 1) 사용자와 3) Data Structuring and Provenance layer 사이에서 actions를 해석하고 변환함. 
    - Querying system : 3) Data Structuring and Provenance layer에서 원하는 형식으로 request를 처리하는 역할. requestor는 query system이 처리한 쿼리를 전송하고, query system은 requester에게 response를 전송
    - Trigger : smart contract 환경에서 혹은 환경으로부터 오는 actions를 젼환하는 역할
* 3) Data Structuring and Provenance layer : 데이터 접근 관련 요청 처리와 인증을 하는 역할. 4) Existing Database Infrastructure layer의 데이터 접근 요청 처리. 데이터에 대한 계산을 추가로 수행함. 완료된 모든 actions의 결과는 broadcast되어 trustless하고 fair한 감사를 보장. 전체 시스템의 데이터 접근과 관련된 모든 requests와 actions를 인증할 책임을 가짐
    - Authenticator : 요청자가 소유자에게 보낸 요청의 합법성을 확인하는 역할. authenticator contract keys를 생성. encryption key에 태그를 지정. 요청한 데이터가 포함된 패키지 암호화.
    - Processing and consensus nodes : requests에 대해 생성된 forms을 처리. 요청된 데이터와, requestor에게 전달될 smart contract를 포함한 패키지를 생성
    - Smart Contracts : 전송된 데이터에 대해 수행된 actions를 식별하고, data를 database에 report하는 역할. 암호화 키를 가지고 있어서 생성된 보고서를 암호화할 수 있다. 허가받지 않은 requestor에 대한 접근 취소
    - Smart Contract Permissioned Database : contracts 위반시 데이터 소유자가 수행할 작업 목록이 저장되며, 활성화된 actions에 대한 receipts가 보관됨
    - Blockchain Network : 데이터의 전달과 요청에 대한 actions를 chronological하게 담은 distributed immutable database. smart contracts에 의해 보고된 특정 데이터와 관련된 actions를 side-block으로 유지
* 4) Existing Database Infrastructure layer : 개별 당사자가 특정 업무 수행을 위해 미리 구축한 database. 민감한 데이터를 보호하기 위한 보안 메커니즘이 필요함
# Process of MedShare
### System setup
- user가 private key로 서명한 request를 query system으로 전송
- query system은 받은 request를 triggers로 translate하여 authenticator로 전송
- authenticator는 user의 public key로 verify
- 해당 process를 승인할지 삭제할지 결정
### Request file
- authenticator는 valid request를 processing and consensus nodes로 전달
- request를 form으로 처리하는 걸 완료한 processing and consensus nodes는 tag를 하기 위한 data를 얻기 위해 request를 existing database infrastructure layer로 전달
- existing database infrastructure layer는 form에 맞는 data를 내려받아 processing and consensus nodes에게 전송