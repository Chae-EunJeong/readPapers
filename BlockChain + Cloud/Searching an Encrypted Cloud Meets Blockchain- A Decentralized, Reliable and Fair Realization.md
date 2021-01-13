# Searching an Encrypted Cloud Meets Blockchain: A Decentralized, Reliable and Fair Realization
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
- multi-user setting and fairness : 데이터 소유자의 이익을 보호하기 위한 공정성 메커니즘을 통해 정확한 계산에 대해서는 대가를 지불/인센티브 보상을 하는 fair privacy-preserving search scheme을 제안한다.
- implement prototype : prototype을 구현하여 로컬 네트워크와 이더리움 테스트넷에 배포하여 암호화된 데이터에 대한 decentralized search scheme의 가능성을 입증하기 위해 실험한다.