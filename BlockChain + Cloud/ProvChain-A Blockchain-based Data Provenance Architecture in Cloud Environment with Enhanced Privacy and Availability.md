# ProvChain: A Blockchain-based Data Provenance Architecture in Cloud Environment with Enhanced Privacy and Availability
- 

---
- issue? : 
### Architecture of ProvChain System
![image](https://user-images.githubusercontent.com/68576770/98079568-5cd14880-1eb7-11eb-83e3-569231b8efb7.png)
- Consist of : Cloud User, Cloud Service Provider, Provenance Database, Provenance Auditor, Blockchain Network
    - Cloud User : data의 owner이자 다른 user와 data를 공유하는 역할
    - Cloud Service Provider(CSP) : cloud storage service를 제공하며, user registration을 담당하는 역할
        - audit the data changes
        - provenance data를 통한 비정상적 침입 탐지
        - 또 하나의 User로 여길 수 있음(자신의 records 보호)
    - Provenance Database : 블록체인 네트워크의 모든 provenance data를 익명으로 기록
    - Provenance Auditor(PA) : Provenance database를 유지하고, blockchain receipt를 validation하는 역할
    - Blockchain Network : 참여 노드로 구성되며, provenance data는 블록 형태로 기록되고, 노드들에 의해 verification
- Concepts
    - File Provenance Use Case : 모든 파일 provenance에 대해 create, copy, read/write, share, delete 등으로 기록한다. Username, Filename, AffectedUser 또한 모두 기록한다.
    - Block Structure : ProvChain은 block header와 transaction lists으로 구성
        - block header : block hash, height(block index), comfirmations, nonce, merkle root
        - transaction lists : 각 data record는 해시되어 merkle tree node가 되고, merkle tree root node는 한 블록에서의 하나의 트랜잭션이 된다.