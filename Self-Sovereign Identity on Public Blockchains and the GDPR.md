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