# Access Control for Electronic Health Records with Hybrid Blockchain-Edge Architecture
![image](https://user-images.githubusercontent.com/68576770/106689855-0e495c80-6614-11eb-856e-9e265afcf98e.png)
- EHR data를 효과적으로 관리하기 위해 edge노드와 hyperledger composer fabric 구조를 결합한 접근 제어 메커니즘이다.
# Problem Statement
- 늘어나는 EHR data의 기록이 노출되는 것으로부터 보호가 필요하다.
- 암호화를 한다고 효과적으로 접근 제어를 할 수는 없다.
- EHR을 위한 접근 제어 방법이 필요하다.
### Blockchain managing EHR data
- traditional blockchain은 data integrity를 보장하지만 다른 사람이 수행한 작업을 포함할 접근 제어 메커니즘이 없다.
- EHR은 Xray, MRI 등으로 용량이 크지만 blockchain의 용량에는 한계가 있다.
# Main access control 
### 1. Blockchain
- identity-based access control with ACLs(Access Control List)
### 2. Edge Node
- attribute-based access control(ABAC) with ALFA(Abbreviated Language For Authorization)
# Hybrid Blockchain-Edge Architecture
![image](https://user-images.githubusercontent.com/68576770/106697944-25dc1180-6623-11eb-9be2-d073c9aff3c9.png)
### 1. Patient
- EHR data 소유자
- specify the access policies for EHR data
### 2. Healthcare provider
- 환자의 EHR data를 필요로 하는 의사/간호사
- access 가능한 환자 목록을 가지고 있으며, 환자의 ID를 가지고 요청하여 EHR data에 접근
### 3. Smart sensor/imaging equipment
- EHR data를 모아서 edge node로 보내는 device이다.
- sensor equipment는는 맥박 등을 측정하는 것이고, image equipment는 Xray나 CT scan 등이다.
### 4. EHR data
- 환자가 소유하는 환자의 정보
- 의사가 접근해야 할 데이터
### 5. Edge node
- computing and storage device
- EHR data를 저장하거나 ABAC polices를 적용한다.
# Evaluation
- transaction processing time과 average response time 측정
- 참가자인 의사는 접근 가능한 환자 목록을 가지고 있고, 환자의 ID로 요청하여 EHR에 접근한다.
- 참가자인 환자는 자신의 EHR은 읽을 수 있지만 다른 환자의 어떠한 정보도 얻을 수 없다.
- 두 경우 모두 average transaction processing time과 average response time이 40ms, 30ms 로 굉장히 빠른 시간 내에 결과를 얻을 수 있다.
- 따라서 실시간으로 정보를 얻기 적합하고 접근 제어를 하는데도 효과적이다.
- 환자 수를 늘려도 시간의 변화가 거의 없이 빨리 진행되어 확장 가능함을 보였다.