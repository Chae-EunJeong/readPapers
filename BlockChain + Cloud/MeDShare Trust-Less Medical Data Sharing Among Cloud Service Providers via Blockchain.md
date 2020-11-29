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
- 수신한 timestamp의 해시를 processing and consensus nodes는 해시된 request의 timestamp 기록에 연결 
- processing and consensus nodes는 요청된 데이터에 대한 set of rules를 추가하기 위해 smart contract center로 전송
- smart contract가 생성되고, form에 태그 지정
### Package delivery
- results는 authenticator로 전달되어 authenticator contract key 생성, 생성된 암호화 키를 smart contract로 태그
- processing and consensus nodes는 request에 대한 정보를 기반으로 블록을 생성하여 blockchain network로 배포
- 블록은 ordering 방식으로 이미 존재하는 requestor와 관련된 블록의 일부가 되며 identity로 태그되어 고유하게 식별된다.
- data는 암호화되고, 암호화된 패키지를 형성하고, requestor의 ID로 태그되어 트리거를 통해 query system으로 전달된다.
    - package는 data ID, data, smart contract이 포함됨
- query system은 requestor에게 배포한다.
### Auditing and provenance
- requestor는 패키지를 수신하면 자신의 private key를 사용해 decrypt
- data를 decrypt하기 위해 데이터에 태그된 암호화 키를 받기 위한 smart contract를 활성화해야하며, decrypted data의 action을 암호화하기 위해 query system으로 전송한다.
- query system은 processing and consensus nodes로 action에 대한 report를 전달
- processing and consensus nodes는 report를 side-block으로 처리하고, 추적을 위해 그 결과를 parent block에 추가
    - smart contract에 의해 보고된 데이터와 관련된 actions를 side-block이 blockchain netowrk에 기록하며, side-block은 parent block에 생성된다.
### Smart contracts
- MedShare에서 smart contract는 데이터 소유자의 시스템에서 요청자가 수행한 actions를 report할 때 사용된다.
    - 데이터 소유자는 전송된 데이터의 행방을 모니터링하게 되어 데이터의 출처에 대한 assurance와 control을 얻는다.
- 데이터 소유자의 시스템에 report된 데이터는 process, index, broadcast된다.
- basic actions are : read, write, delete, duplicate, move, copy
- actions는 smart contract를 trigger하여 report를 보낸다.
- getAction : smart contract scrips로 actions의 모니터링을 전달하는 함수
- 데이터 sensitivity의 높고 낮음에 따라 smart contract를 수정하여 효과적으로 모니터링한다. 
- comments : 데이터에 대해 수행된 actions를 설명하는 statements로 생성된다. 보통 violation이나 exemption comments.
- retrieve는 getAction과 쌍을 이루어 comments를 encrypt하기 위한 key 추출
- encrypt action을 호출하여 프로세스를 마무리한다.
- accessControl : 데이터 소유자가 설정한 권한
- smart contract의 효율적인 운영 보장을 위해 requestor에 의한 실행 가능한 statement를 삽입하는 것이 중요하다.
- smart contract가 violation action을 받으면, 요청자의 접근 권한을 취소하고 report를 전송한다. 그럼 데이터 소유자는 smart contract permissioned database를 통해 선택적으로 violation을 처리한다.
### Data processing and sharing between existing DB infrastructure and data sharing and provenance layer
![image](https://user-images.githubusercontent.com/68576770/100544206-76d43000-3297-11eb-898a-c961c23e8b16.png)
- 요청된 데이터를 기존 데이터베이스에서 발행할 때 무결성과 가치를 유지하는 것이 중요함
- 검증된 요청은 existing database infrastructure에서 복제본을 만들어 consensus node에 할당한다.
- consensus node는 받은 복제된 데이터로 노드의 고유 ID와 payload를 포함하는 패키지를 생성한다.
- processing and consensus node는 수신된 데이터를 요청과 비교하여 양식을 확인한다.
- 데이터의 민감도가 높거나 낮은지 순위가 매겨지는데, 높은 민감도의 dataset은 추가 익명화가 필요하기 때문에, 이런 action은 processing을 통해 블록의 state가 전환될 양식에 기록된다. 
- 처리된 결과는 두번째 consensus node에 제공되어 첫번째 processing node의 작업을 검증한 후, 검사가 정확하면 첫번째 노드로 반환한다.
---
- processing and consensus node가 데이터 민감도 level을 smart contract generator로 보내면, smart contract는 노드에 script를 출력하고, 노드는 데이터의 현재 처리된 상태에 첨부한다.
- processing and consensus node는 모든 처리 결과, 즉 패키지를 authenticator로 출력한다. 
- authenticator는 요청자의 public key로 패키지를 암호화하고 timestamp를 노드로 출력한다. 
- processing and consensus node는 모든 timestamp를 기록하여 효율적으로 최적화하는 것을 가능하게 한다.
- 데이터에 수행된 모든 actions와 두번째 검증 노드의 ID는 양식에 기록되고 이 양식이 네트워크로 broadcast될 블록으로 처리된다. 
### Parent block structure
![image](https://user-images.githubusercontent.com/68576770/100544784-78075c00-329b-11eb-985b-31f39f9daa8c.png)

### Side-block structure
![image](https://user-images.githubusercontent.com/68576770/100544796-91a8a380-329b-11eb-8f01-f5d192a7db4f.png)
