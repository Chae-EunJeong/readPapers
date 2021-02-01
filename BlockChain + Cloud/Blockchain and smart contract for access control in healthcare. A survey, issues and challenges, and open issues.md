# Blockchain and smart contract for access control in healthcare: A survey, issues and challenges, and open issues
- EHR(Electronic Health Records)에 대한 접근 제어에 중점을 두어 의료 분야에서 블록체인 기술과 스마트 컨트랙트를 적용한 사례들을 정리한 서베이 논문
# Taxonomy of blockchain-based EHR access control methods
![image](https://user-images.githubusercontent.com/68576770/106426486-07520b00-64a9-11eb-91d2-8bd32e32220d.png)
# Open issues and challenges
### 1. User and Attribute Revocation in Smart Contract-bases access Control Methods
- smart contract로 접근 제어를 하는데, data owner가 한 user에 대해 revoke하려면 그것도 새 블록에 기록해야함
- 큰 회사일수록 revoke하는 user도 많으므로 비용이 많이 든다.
- ABE와 IBE 메서드를 사용해 접근제어를 하긴 했지만 새로 가입한 user가 권한 없이 EHR을 decrypt할 수 있어서 안전하지 않다.
- 효율적으로 키를 업데이트하는 지연 취소 암호시스템(lazy revocation cryptosystem)으로 문제를 극복할 수 있다.
### 2. Privacy of Outsourced Data in Cloudchain
- blockchain의 auditable 특성에도 불구하고 CSP가 호기심을 가졌을 때는 위험하다.
- 1) 클라우드로 아웃소싱 하기 전 익명화를 해서 해결할 수 있다.(K-Anonymity)
- 2) 기계학습을 해서 원본은 로컬에 저장, 학습 결과는 cloud chain에 아웃소싱을 해서 문제를 해결할 수 있다.
### 3. Blockchain Scalability
- 확장성 : 더 많은 저장소나 자원을 사용하지 않고도 더 많은 작업을 처리하는 것
- 의료 분야에서 확장 가능한 접근 제어 방법이 이루어져야 함
    - 1) IoT architecture 개발하여 장치 간 안정적인 연결 제공
    - 2) 동기화 및 검증단계를 병렬화하여 더 높은 처리량을 달성하기 위한 PoW 합의 프로토콜 개발
    - 3) 메시지 복잡성을 줄여 확장 가능한 BFT 합의 프로토콜 개발
### 4. Latency in Blockchain Network
- 의료 기록은 수집되고 기록되는 데 대기 시간이 중요하다.
- 특히 아웃소싱을 할 때 상당한 네트워크 지연이 발생한다.
- 오프체인 데이터를 edge computing이나 IPFS에 저장하여 문제를 해결할 수 있다.
    - 단, IPFS는 bandwidth를 많이 소비하기 때문에 IoT에선 적합하지 않음
