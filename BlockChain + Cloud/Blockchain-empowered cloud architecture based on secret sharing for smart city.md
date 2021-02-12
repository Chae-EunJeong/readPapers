# Blockchain-empowered cloud architecture based on secret sharing for smart city
![image](https://user-images.githubusercontent.com/68576770/107753541-8f66c900-6d63-11eb-9ba4-3fa9836d3104.png)
- 여러 블록체인의 CSP에 데이터를 저장하며, secret sharing algorithm은 특정 CSP가 데이터를 변조하거나 잃어버려도 원래 데이터를 복구할 수 있게 하고, 블록체인을 사용해 CSP가 저장한 데이터의 무결성을 확인할 수 있다.
# Methodological flow of the proposed architecture
![image](https://user-images.githubusercontent.com/68576770/107743748-d1d4d980-6d54-11eb-8d79-d2eef92dc4c1.png)
### 1. Gathering Data 
- 각 IoT 장치에서 생성된 데이터는 Inter-Network Server로 전송됨
- 각 데이터는 다양한 IoT 장치의 데이터이므로 보호되어야함
### 2. Processing
- privacy와 통신 효율성을 고려하여 IoT 장치의 데이터 분류
- Secret Sharing 알고리즘을 적용하여 데이터 보호
### 3. Data Transaction
- CSP consortium blockchain network에서 트랜잭션 생성
- 비밀 정보를 블록체인의 블록으로 저장하여 데이터의 무결성 보호 
### 4. Secret Sharing
- SSA-1(Secret Sharing Algorithm)이 두 개의 CSP에 두 개의 분산 정보 S1과 S2를 제공
- SSA-2는 세 개의 CSP에 세 개의 분산 정보 S1, S2, s3를 제공
![image](https://user-images.githubusercontent.com/68576770/107750026-c686ab80-6d5e-11eb-9b43-8e0fc65e2f6e.png)
- 세 개의 CSP중 두 개에서 받은 데이터로 재구성
### 5. Data Reconstruction
- SSA-2를 사용한 분산데이터는 CSP 세 개 중 두 개에서 데이터를 수집해야 재구성 가능함
- 따라서 원본 데이터를 추론하기 어렵기 때문에 privacy 문제를 해결할 수 있음