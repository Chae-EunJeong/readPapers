# Blockchain-based Database to Ensure Data Integrity in Cloud Computing Environments
- goals : blockchain을 as-is로 적용한 연구 + 클라우드 환경에 적용할 blockchain-based database
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
- 따라서, 무결성을 보장하면서 latency와 throughput 문제를 해결하는 blockchain의 연구가 필요하다.
- performance와 integrity 사이에서 요구사항에 따라 균형을 맞춰 최적의 설계를 해야 한다.
##### Stability
- PoW의 전망에 대한 연구는 여전히 진행중이며, PoW의 incentive mechanism은 장기적으로 좋지 않아 stability에 대한 관심은 여전하다.
- PoW 기반 permisionless blockchain은 저장 비용이 비싸고, 시장에 의존하며, 성능이 열악해서 mining process(currency incentives)를 변경해야 stability가 증가한다.
- 그러나, 그러한 개정은 사실 불가능하기 때문에 incentive가 currency에 의존하지 않는 permissioned blockchain을 이용하는게 가능성이 있다.
- 즉, 무결성을 보장하고, 높은 stability를 가지는 permissioned blockchain은 cloud computing 환경처럼 필요에 따른 분산 database 개발의 안정적인 지원을 보장한다.