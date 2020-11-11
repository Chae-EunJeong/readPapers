# Towards Cloud Computing and Blockchain Integrated Applications
- cloud resource를 활용한 blockchain service 제공을 위해 고려해야할 것으로 1)Integration aspects, 2)Modeling, 3)Environment quality and Attribute metrics, 4)Smart contracts and Cloud computing 가 있다.
# Discussion
### 1. Integration Aspects
- cloud computing environments이 제공하는 다양한 서비스들의 통합이 이루어진다.
- 블록체인을 서비스로 사용할 때는 기술의 이점이 많이 알려질수록 통합하는게 보편화된다.
- 하지만 블록체인의 기술이 너무 많아서 통합하는 데 어려움이 있다.
- 따라서, 요구사항에 따라 두 기술(cloud computing and blockchain)의 기능을 적절히 통합해야한다.
### 2. Modeling
- 사용자가 application을 더 쉽게 만들 수 있도록 서비스를 모델링하고 배포하는 도구를 더 발전시켜야한다.
- 모델링 시스템은 blockchain design pattern을 사용하면 도움이 된다.
### 3. Environment Quality and Attribute Metrics
- cloud computing의 특징 중에는 서비스 측정이 있다.
- 측정 기능으로 리소스 사용을 모니터링하고 제어하여 provider와 user에게 투명성을 제공한다.
- Quality of Service(QoS)를 보장하기 위해 availability, functionality, performance등에 대한 정보를 제공하는 Service Level Agreement(SLA)를 사용할 수 있다.
-blockchain을 사용하는 서비스는 cloud computing 사용 비용과 다른 financial 비용이 있기 때문에 모니터링 기능이 필요하기 때문에 적절한 metrics가 식별돼야 한다.
### 4. Smart Contracts and Cloud Computing
- smart contract를 사용한 블록체인과 클라우드 컴퓨팅은 특히 business 쪽에 잠재력을 가지고 있다. 
- performance analysis of environments, security of access, data management, and cost effectiveness of applications 과 같은 challenge를 고려해야한다.
# Examples of Integrated Cloud Computing and Blockchain Environments
### AWS Blcokchain
- AWS Blockchain : Amazon에서 제공하는 블록체인 서비스
- flow of model usage : selects the model, deployment platform, build the network and deploy decentralized applications
- 사용자는 blockchain application 구축에만 집중
    - open source framework를 사용하여 blockchain network를 구축 및 배포
    - container에서 선택한 Blockchain 구조 배포 방법 
        - 1. Amazon Elastic Container Service 클러스터로 배포
        - 2. Docker를 실행하는 EC2로 직접 배포
- blockchain infrastructure에 적용되는 templates
    - 1. AWS Blockchain for Ethereum 
        - public blockchain network
        - peer transactions를 수행하거나, 새로운 public network를 생성하거나, smart contract를 사용해야할 때 이 template를 이용한다.
    - 2. AWS Blockchain for Hyperledger Fabric
        - private blockchain network
        - private network를 생성하거나, 데이터에 대한 접근 제어 및 권한 제공이 필요할 때 이 template를 이용한다.
### Azure Blockchain
- Azure Blockchain : Microsoft에서 제공하는 블록체인 서비스
- 사용자는 비즈니스 로직과 application 개발에 집중
    - consortium blockchain network의 formation, management, governance를 단순화한다.
- 기능
    - deployment of easily managed blockchain networks
    - scale control with codeless consortium management and internal governance
    - building blockchain applications using tools
    - using the blockchain data manager - capturing and storing ledger data out of the chain
- In blockchain data publishing
    - user는 Blockchain Data Manager를 사용해서 smart contract 모니터링, transactions and events에 대응, chain의 data를 외부 data stores로 전송 등의 기능을 수행할 수 있다.