# Self-Sovereign Identity on Public Blockchains and the GDPR
### Study three existing technical solutions for a SSI on blockchains
### Analyze the arising issues related to the General Data Protection Regulation(GDPR) of the EU
### Overview of the existing Sovrin SSI on the Hyperledger Indy as well as uPort and Jolocom on the Ethereum
> Hyperledger Indy(public permissioned blockchain), Ethereum(public permissionless blockchain)
### Discussion on the GDPR-compliance of the blockchain-based identity concepts
---
# Introduction
- SSI : 자기의 주권은 자기가 소유하여, 자기의 identity data를 저장하고, identity data를 얼만큼 공유할지, 누구에게 공유할지 모두 자신이 정한다.
- blockchain 기술을 적용한 SSI 특징: decentralization, p2p interactions, data integrity
  - GDPR compliance issues : immutability of data, storage on blockchain
# Self-Sovereign Identity
### The concept
- blockchain-based SSI uses decentralized identifiers(DIDs)
- DID document에 DID에 대한 공개키와 자격 증명등이 포함되며 DID에 대한 개인키를 가진 사람이 제어한다.
- DID method specifications : Sovrin DID Method, ETHR DID Method, Alastria DID Method, Ocean Protocol DID Method, Jolocom DID Method, and others.
### Sovrin
![image](https://user-images.githubusercontent.com/68576770/95706296-70f7a080-0c91-11eb-8867-d4cd67590108.png)
- Sovrin SSI는 Hyperledger Indy public permissioned blockchain에서 작동한다.
- Edge Layer : agent는 mobile phone, tablets, laptops 등의 edge device에서 작동한다.
- Cloud Layer : DID를 가진 agent가 Verifiable Claim을 발행하고 서명할 수 있다. 
                Verifiable Claims는 encrypted private channel인 cloud layer에서 교환된다.
- DIDs Layer : verifier는 Verifiable Claim에 포함된 DID의 정보를 가지고, 블록체인에서 발행자의 public key를 찾아와 서명을 검증할 수 있다.
- Public Blockchain : Sovrin ledger(public blockchain ledger)에는 public DIDs, data types and formats to make credentials(schema), credential definitions, revocation registries 들이 저장된다.
### uPort
##### uPort Architecture
- uPort MobileApp : identity wallet 역할. identities를 관리한다. 
                    request와 response는 서명된 JWTs(Json Web Token)으로 구성되어 오프체인 메시지로 private하게 수행된다. 
                    서명된 메시지는 DID를 포함한다.
- uPort Registry : attribute와 identity를 연결할 때 쓰는 contract.
                    ID에 대한 IPFS hash를 찾을 수 있다.
- IPFS(Interplanetary File System) : DID document를 저장하는 파일 시스템
                                    identity에 해당하는 public key를 가지고 있다.
                                    DID document에서 public key를 추출하여 서명을 검증한다.
### Jolocom
##### Jolocom Framework
- Public Ethereum blockchain : smart contract이며, DIDs를 저장한다.
                            한 사람의 credential에 대해(Base DID) 여러 Child DIDs를 생성하는 것이 가능하다.
- IPFS : DID documents(DDO)를 저장한다.
- Private Storage : local, cloud
                    uPort처럼 credentials와 key recovery를 저장하는 local 저장소를 지원한다.
# The European General Data Protection Regulation
- GDPR은 personal data의 처리만을 규제한다.
- GDPR은 controllers, processors, data subjects 를 구분한다.    
    - controller : 처리의 목적과 수단을 결정
    - processor : 컨트롤러 대신 데이터를 처리
    - data subject : 권리와 보호에 귀속
### How does GDPR apply to SSI?
- GDPR은 personal data에만 적용된다.
    - personal data : 식별가능한 사람과 관련된 정보
- 본 논문에서는 SSI의 4가지 타입의 데이터를 다룬다.
    - DIDs
    - Credentials
    - Revocations of credentials
    - Hashes of one of the first three or other objects
- personal data로 간주되려면 데이터 주체에 대한 정보가 context를 통해 전달되어야 한다.
- 따라서 credentials와 revocations는 personal data이다.
- DIDs와 personal data의 hashes의 경우
    - 데이터 주체가 생성한 DID는 연결된 개인키로 서명되어 DID의 제어를 증명한다.
    - DID를 여러번 사용하면 식별자처럼 작동되어 다른 속성이나 credentials와 연결될 수 있다.

    - 단방향 함수인 암호화 해시함수를 사용한 객체가 있을 때, 객체에 충분한 엔트로피가 포함되지 않은 경우 가능한 모든 값을 시도하여 원래 객체를 알아낼 수 있다.
    - personal data로 간주되기 위해서는 해시 값으로 주체를 식별하는 것만으로는 충분하지 않으며, 해시된 객체의 context는 원래 객체에 포함되지 않은 추가 정보를 전달해야 한다.
### Who is controller of DIDs, credentials and revocations of credentials?
> DIDs와 블록체인에 저장된 hashes의 controller를 결정할 때는 case-by-case 분석이 필요함
- Controller : GDPR의 의무를 따를 책임이 있는 person 혹은 entity
    - joint(공동) controller : 여러 컨트롤러가 공동으로 처리 목적과 수단 정의 가능
    - To determine controller : 데이터가 블록체인에 저장되었는지 여부에 따라 나누어서 결정한다.
- 1. Not store on a blockchain : Sovrin, uPort, Jolocom
    - controller는 발급 기관 / agent / cloud provider / data subject 가 될 수 있다.
    - SSI 시스템에서 data subject가 credential을 추가하는 controller가 될 수 있지만, credential을 revocation할 때는 발급자가 controller로 간주된다.
    - data subject가 data에 대한 controller일 때는 GDPR이 적용되지 않지만,
    data subject를 대신해서 data를 처리하는 processor에는 적용된다.
- 2. Stored on a blockchain : DIDs
    - (1) The controller on the blockchain level
        - public blockchain 
            - uPort와 Jolocom 등
            - CNIL(French data protection authority)는 node operators와 miners를 controller로 간주하지는 않으나 가능성은 열어둔다.
            - 블록체인 수준의 controller는 없다.
        - permissioned blockchain
            - Sovrin 등
            - entity나 consortium이 permissions를 결정하기 때문에 controller로 간주된다.
    - (2) The controller on the transaction level
        - transaction을 개인키로 서명하고 블록체인으로 전송하는 사람이 controller로 간주된다.
    - (3) The controller on the smart contract level
        - CNIL은 smart contract 개발자를 controller로 간주한다.
            - 그러나, 단순한 코드의 공급자나 프로토콜 개발자는 controller로 여기지 않는다.
### Justification
- personal data의 처리에 필요한 justification은 GDPR Art.에서 제공된다.
- justification은 credentials와 revocation에 동의 혹은 계약이 필요한 것 처럼 case-by-case 분석이 필요하다.
### Right to erasure / right to be forgotten
- 블록체인 기반 시스템에서 controller가 data subject에 대해 가져야 할 의무 중 삭제할 권리와 잊혀질 권리가 문제가 된다.
- DIDs(hashes of credentials or hashes of revocations)가 블록체인에 저장되면 case-by-case 분석을 해서 data가 계속 personal data인지 확인해야 한다.
    - hase된 개체가 안전하게 삭제되었다면 personal data로 간주되던 hashes는 더이상 personal data로 간주되지 않는다.
### Revocations of credentials
- revocation은 personal data로 간주되며, justification이 필요하다. 
- revocation을 볼 근거가 있는 사람만 사용할 수 있기 때문에 revocation을 최소화할 수 있다.
# conclusion
- SSI는 중앙기관 없이 data subject가 credential을 제어하여 개인 정보를 보호하고 GDPR을 준수할 수 있다.
- 그러나 use-case별 분석이 요구된다는 것과 기존 법의 불확실성 때문에 기술의 사용에는 부담이 된다.