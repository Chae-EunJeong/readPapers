# Searching an Encrypted Cloud Meets Blockchain: A Decentralized, Reliable and Fair Realization
![image](https://user-images.githubusercontent.com/68576770/104692284-10be4200-574b-11eb-8200-e8c613b1b2eb.png)
- cloud service provider 같은 중앙 서버가 아닌 smart contract를 통한 탈중앙화된 privacy-preserving search scheme의 구축을 통해 공정한 검색을 할 수 있게 한다. 또한 정직한 참여자에게는 incentive를 주어(악의적인 참여자는 nothing) 공정성을 높인다.
- fairness, soundness, confidentially한 scheme
# Problem statement
- central server를 이용하는 방식에서 암호화된 데이터를 검색할 때 일부만 응답하거나 일치하지 않는 데이터를 반환할 수 있다.
- 보안에 대한 위반이나 내부의 공격자가 데이터에 수행된 계산을 바꿀 수 있는 접근 권한을 얻을 수 있다.
- 기존의 검증 가능한 검색 스키마(simple query expressions - single keyword search)는 부정 행위 감지에만 초점을 두고 있다.
- 다양한 검색 스키마에 검증 가능성을 적용할 수 있는 방법은 아직 명확하지 않으며, 부정 행위에 대한 후속 조치도 필요하다.
# To Do
- using smart contract : 중앙 서버를 없애고 검색 쿼리를 스마트 컨트랙트로 아웃소싱하여 misbehaviors를 감지
    - data owner는 계산 작업에 대한 대가를 지불하여 정확한 검색 결과를 얻을 수 있으며 따로 검증하지 않아도 된다.
- multi-user setting and fairness : 데이터를 공유하고자 할 때는 데이터 소유자 뿐만 아니라 데이터 사용자도 존재한다. 
    - 데이터 소유자의 이익을 보호하기 위한 공정성 메커니즘을 통해 정확한 계산에 대해서는 대가를 지불/인센티브 보상을 하는 fair privacy-preserving search scheme을 제안한다.
- implement prototype : prototype을 구현하여 로컬 네트워크와 이더리움 테스트넷에 배포하여 암호화된 데이터에 대한 decentralized search scheme의 가능성을 입증하기 위해 실험한다.
# Decentralized privacy-preserving search scheme
### 1. Setup
- scheme에서 search와 update등을 수행하기 전, data owner는 DB를 암호화한 EDB(Encrypted database)와 개인키, 그리고 data owner's state를 가져야한다.
### 2. Search
- data owner의 1)EDB 그리고 2)개인키, state, search token를 가지고 이더리움에서 3)smart contract를 실행시켜 4)File id를 얻는다.
### 3. Update
- File id를 가지고 Add/Del 작업을 요청한다.
    - data owner의 5)EDB, 그리고 개인키, state, operation{add, del}, file id, a set of keywords를 가지고 이더리움에서 smart contract를 실행시키고 행위의 결과에 대한 6)response를 받는다.
# Multi-user Setting
![image](https://user-images.githubusercontent.com/68576770/104692302-187de680-574b-11eb-9a1a-26cf338267af.png)
- data user가 data owner의 DB에서 data 검색이 가능한 환경
- smart contract는 public한데, scheme에서는 개인키를 가지고 검색해야하기 때문에 이 논문의 scheme에서는 2)data owner가 data user의 query(search keyword)를 수신하면 3)data owner가 search에 필요한 token을 생성해서 smart contract에서 실행시킨다. 
- multi-user 환경에서 smart contract는 fairness를 보장하도록 한다.
    - 3)에서 data owner는 시간 제한 안에 search token을 보내야함
    - data owner가 data user가 원하는 search tx를 대신 실행해주므로 데이터 사용료 뿐만 아니라 smart contract 실행에 필요한 가스 수수료까지 포함하여 지불해야한다.

# Reference
Hu, Shengshan, et al. "Searching an encrypted cloud meets blockchain: A decentralized, reliable and fair realization." IEEE INFOCOM 2018-IEEE Conference on Computer Communications. IEEE, 2018.