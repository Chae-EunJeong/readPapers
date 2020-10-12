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