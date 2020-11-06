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
- Key Establishment
    - Provenance Auditor(PA)를 완전히 신뢰할 수 없기 때문에 키를 생성하여 데이터를 보호한다.
        - User Registration Key : user는 cloud data를 운영하기 위해 registration key를 생성한다.
        - Data Encryption Key : user는 encryption key를 생성하여, 클라우드에 저장될 데이터를 암호화하여 key holder외의 접근을 제어한다.
        - Data Sharing Public/Private Key Pair : data owner는 private key로 서명하고, owner외의 사람들은 public key로 ownership을 검증한다.  private key를 공유하여 ownership을 변경해서 데이터를 공유한다.
        - Provenance Verification Key : cloud service provider가 provenance verification key를 생성하여 provenance auditor와 공유한다.
### Implementation of ProvChain
- User는 cloud에 저장된 data에 일어나는 모든 operation을 metadata로 명시하고, data record는 blockchain network로 publish되며, blockchain receipt가 생성되어 provenance auditor가 validation을 요청했을 때 쓰인다. Provanence data와 validation은 provenance database에 저장된다.
- data record : Merkle tree로 hash된 형태
- blockchain receipt : information of blockchain transaction, Merkle proof and Merkle root 등으로 구성
