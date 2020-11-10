# Blockchain-based Database to Ensure Data Integrity in Cloud Computing Environments
![image](https://user-images.githubusercontent.com/68576770/98618654-ffb91500-2344-11eb-8f28-5202dc11637e.png)
- two-layer의 blockchain으로 구성하여 각 층에서 성능과 무결성을 보장한 blockchain-based database
# Problem statement
- cyber-attack에 의한 데이터의 신뢰성을 CIA요소(Confidentiality, Integrity, Availability)로 증명할 때, 특히 data integrity는 치명적이다.
- 클라우드 컴퓨팅 환경에서 data integrity는 더 악화되므로 클라우드에서 data integrity를 보장하는 것은 필수적으로 필요하다.
- 데이터를 분산 저장하면 공격자가 공격하기 힘들어져 무결성 보장에 효과적이지만, cloud provider가 공격에 가담시 피해를 받을 수 있기 때문에, 블록체인 기술로 분산 저장을 발전시킬 수 있다.(blockchain-based database)
### European SUNFISH Project
- SUNFISH(SecUre iNFormatIon SHaring in federated heterogeneous private clouds)는 다양한 클라우드 시스템들이 보안문제를 극복하여 distributed 하고 democratic한 연합 플랫폼 제안
- FaaS(Federation-as-a-Service)
    - leading to a distributed and democratic cloud federation governance
    - advanced data security service and innovative design principles 
    - 연합 구성원 간 정의된 contracts를 준수하는 것에 대한 높은 보장 제공
    - 리더 없이 연합 회원들이 peers network 형성
### PoW Blockchain의 속성에 따른 개선 방안
- blockchain은 database operations의 로그들을 저장하는데 사용될 수 있지만, 있는 그대로의 blockchain을 쓰기에는 여러 문제들이 존재함
##### Data Integrity
- 모든 노드에 full replication되어 블록에 포함되어 영구적으로 블록체인에 남는다면 신뢰도를 얻어, blockchain은 data integrity를 보장하게 된다.
- 즉, data가 block에 포함되어 여러 노드들로 broadcast 될수록 무결성 보장 확률이 높아진다.
- 하지만 transaction이 blockchain에 전달된 직후에는 무결성을 보장한다고 보기 어렵다.
- 따라서, 공격자가 감지되기 전까지 소비하는 노력을 기반으로, quantitive하게 data integrity 보장에 대해 접근할 필요가 있다.
##### Performance
- block의 broadcast가 진행될 때 latency, 그리고 PoW방식으로 mining process가 진행될 때 time-intensive task가 문제가 된다.
- 낮은 transaction 처리량 때문에 PoW-based blockchain은 performance가 좋지 않다.
- 따라서, 무결성을 보장하면서 성능(latency와 throughput) 문제를 해결하는 blockchain의 연구가 필요하다.
- performance와 integrity 사이에서 요구사항에 따라 균형을 맞춰 최적의 설계를 해야 한다.
##### Stability
- PoW의 전망에 대한 연구는 여전히 진행중이며, PoW의 incentive mechanism은 장기적으로 좋지 않아 stability에 대한 관심은 여전하다.
- PoW 기반 permisionless blockchain은 저장 비용이 비싸고, 시장에 의존하며, 성능이 열악해서 mining process(currency incentives)를 변경해야 stability가 증가한다.
- 그러나, 그러한 개정은 사실 불가능하기 때문에 incentive가 currency에 의존하지 않는 permissioned blockchain을 이용하는게 가능성이 있다.
- 즉, 무결성을 보장하고, 높은 stability를 가지는 permissioned blockchain은 cloud computing 환경처럼 필요에 따른 분산 database 개발의 안정적인 지원을 보장한다.
# A blockchain-based database proposal for a cloud federation
- 높은 데이터 무결성 보장과 동시에 성능과 안정성에 대한 요구 사항을 준수하는 two-layer blockchain-based database 제안
- 두 계층간 상호작용을 통해 성능 향상과 데이터 무결성 보장이 가능
- 블록체인 기반 데이터베이스는 무결성 보장을 뿐만 아니라 데이터 베이스의 데이터의 완전 분산 제어도 가능
![image](https://user-images.githubusercontent.com/68576770/98618654-ffb91500-2344-11eb-8f28-5202dc11637e.png)
### first-layer: Mining Rotation-based Blockchain
- 원리
    - 성능 보장
    - low latency와 high throughput을 보장하는 lightweight distributed consensus protocol 사용
    - distributed database에서 사용되는 모든 operation evidence를 빠르고 확실히 저장
    - 그러나 이 계층은 PoW가 부족해 무결성 보장에 대한 부분이 약함
- FaaS federation에서의 흐름
    - 1. member clouds는 Database Interface를 통해 operation을 발생시킴
    - 2. operations은 first-layer blockchain에서 evidence들을 통해 log됨
    - 3. operations은 분산된 DB replics에서 실행됨
- FaaS federation
    - first-layer의 blockchain은 permissioned이며, 각 member cloud에 하나의 miner를 가짐
    - consensus mechanism : 각 miner들은 public/private key를 가지고 메시지에 서명하여 합의하는 mining rotation consensus mechanism 
        - 시간에 따라 나눈 라운드마다 leader miner를 선출하고,
        - leader는 operation을 새로 받으면 개인키로 서명 후 broadcast
        - 다른 miner 모두가 받은 operaration에 서명하면 blockchain에 저장됨
        - 모든 miner가 blockchain에 추가된 operation을 local ledger에 추가 후 local replica에 적용함
### second-layer: PoW-based Blockchain
- 원리
    - 무결성 보장
    - first-layer에서 log된 operation evidence를 저장하는 PoW기반 blockchain
    - evidence들이 강력한 데이터 무결성 보장과 함께 저장되지만 성능은 약함
- FaaS federation
    - first-layer과 secon-layer의 상호작용은 blockchain anchoring 기술을 통해 이뤄진다.
    - 특정 시간 간격으로 witness transaction이 first-layer에서 second-layer로 전송되어 immutable, irreversible transaction으로 저장된다.
        - witness transaction은 현재 operation까지의 first-layer blockchain의 hash를 포함하고, 그 hash는 first-layer에 저장된 data의 integrity를 증명 및 검증하는 forensics evidence이다.
### two-layer blockchain 속성에 따른 기대점
- Data Integrity : evidence가 first-layer에만 있다면 공격자는 first-layer의 모든 replica를 손상시키는 노력이 필요하지만, evidence의 hash가 second-layer에 저장되면 공격자는 작업 증명의 무결성을 파괴해야 하는 노력이 필요하며, 이것은 사실상 불가능하다.
- Performance : 클라이언트는 lightweight consensus mechanism을 사용하는 first-layer blockchain에서 operation이 완료되는 성능을 제공하고, background에서만 PoW를 사용하기 때문에 사용자 입장에서는 성능이 더 나아진다.
- Stability : permissioned PoW blockchain을 사용해 안정성을 높인다.