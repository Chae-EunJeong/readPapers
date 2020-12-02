# BBDS: Blockchain-Based Data Sharing for Electronic Medical Records in Cloud Environments
> Medshare보다 한단계 전 논문(BBDS에는 Smart contracts 내용 없음)
![image](https://user-images.githubusercontent.com/68576770/100832712-c3905480-34ab-11eb-81c8-ed1b80bf7457.png)
- 블록체인을 의료 데이터에 대한 접근을 제어하는 데에 사용해, 사용자를 식별하고 인증하여 안전한 데이터 공유 환경을 제공하는 방법
# System Implementation
![image](https://user-images.githubusercontent.com/68576770/100833314-0e5e9c00-34ad-11eb-8c97-75b9c1367796.png)
### A. System setup
- Issuer : 
    - Membership verification key를 생성하여 Verifier에게 전송
    - User가 group에 join하겠다는 request를 보내면, User를 authentication
    - User를 인증하면 Membership verification key를 User에게도 전송(User가 group에 join됐음을 의미)
- User :
    - Membership verification key를 가지고 Transaction private/public keys를 생성
    - Verifier에게 Membership verification key를 전송
- Verifier : 
    - User에게 받은 Membership verification key에 대한 challenge를 보내고, User에게 response가 오면, User를 verification(User의 Membership이 검증되었음을 의미)
    - Membership private key를 생성하여 User에게 전송
    - User에게서 transaction public key를 받아 Verifier의 private database에 저장해 놓는다.
### B. Request file/Grant request
- User : 
    - Membership private key를 가지고 data에 접근하겠다는 request를 생성
    - transaction private key로 request를 서명
    - 서명된 request를 Pool of unprocessed request로 전송
- Pool of unprocessed request : 
    - Consensus node에 의해 processing 되기 전의 블록들로 구성
    - block은 request된 순간부터 블록체인으로 broadcast되기까지의 event이다.
- Consensus node : 
    - Pool of unprocessed request에서 block을 가져오고 User의 sign을 검증한다(Verifier으로부터 transaction public key를 통해 검증)
    - 검증이 완료되면 Storage Infrastructure로부터 data를 받아온다
- Storage Infrastructure : 
    - Cloud Environments에 저장된 requested data를 복사해서 Consensus node로 전달한다. 
### C. Access file
- Consensus node :
    - Storage infrastructure로부터 받은 복사된 데이터를 User에게 전달한다.
    - 블록이  blockchain network로 broadcast되기 직전의 상태가 되어 블록의 형태를 다 갖춘다.
- Blockchain network : 
    - broadcast되어 받은 블록을 Blockchain network에 저장된다.
# Block structure
![image](https://user-images.githubusercontent.com/68576770/100836577-e114ec80-34b2-11eb-9c2d-dc2e0ec07941.png)
- blockchain 기술의 주요 문제인 확장성을 해결하기 위해 블록의 크기에 신경써서 블록을 구성함
- 총 679bytes(각 4,4,80,9,578,4bytes)
- 기존 bitcoin 블록체인의 블록 크기는 1MB임
# Reference
Xia, Qi, et al. "BBDS: Blockchain-based data sharing for electronic medical records in cloud environments." Information 8.2 (2017): 44.