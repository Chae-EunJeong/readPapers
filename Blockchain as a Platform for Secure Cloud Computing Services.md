# Blockchain as a Platform for Secure Cloud Computing Services

### Operate mechanisms on cloud@blockchain
![image](https://user-images.githubusercontent.com/68576770/96947157-5dfc9000-151d-11eb-9e62-3d811a1dd5c5.png)
- Consist of : Blockchain, Smart Contract, Cloud Storage, File Owner
    - Blockchain : 모든 applications(Users) 은 blockchain 플랫폼을 기반으로 한다.
    - Smart Contract : communication 담당으로, owner가 올린 데이터를 처리하고 저장한다.
    - Cloud Storage : online storage service를 제공한다. Auth Unit, Upload Unit, File Storage unit, Mapper를 통해 owner의 권한을 검증한다. 
    - File Owner : 암호화 알고리즘(ECDSA)를 통해 데이터 owner의 신원을 빠르게 확인한다.
- no one can hold all of the operation rights.
##### A. Anonymous file sharing
- user의 용량이 큰 데이터들도 익명 파일로 공유할 수 있게 하여 privacy를 보호한다.
1) Uploading on cloud@blockchain
![image](https://user-images.githubusercontent.com/68576770/97245861-513eab80-183f-11eb-8671-1085cce82981.png)
- 1. file information(Metadata)을 blockchain에 올리고, Cloud에 파일을 upload한다.
- 2. cloud는 blockchain에서 metadata를 읽어와, file의 hash를 Auth System을 통해 비교한다.
- 3-1. 이미 같은 hash가 있다면, 파일이 이미 있는 것이므로, block한다.
- 3-2. 비교 후 문제가 없으면 cloud의 Catch와 DB unit에 Read와 write 한다.
2) Downloading on cloud@blockchain
![image](https://user-images.githubusercontent.com/68576770/97246228-2bfe6d00-1840-11eb-9ff2-841b2e18dd1c.png)
- 1. download 요청을 받으면 cloud는 blockchain에서 metadata를 읽어온다.
- 2. cloud의 download unit에서 SimHash를 사용해 Auth System에서 유사성 비교를 한다.(요청받은 파일과 읽어온 metadata 간 유사성 비교?)
- 3. Catch와 DB unit에서 Read 한다.
- 4. similar file들을 보여줘서 original file과 가장 유사한 파일을 user가 결정한다. 
- 5. user가 file을 download 할지 결정한다.
##### B. Inspection for illegally uploaded files
- 블록체인에 user의 고유 정보가 저장되기 때문에, 파일 소유자임을 인증하고 검증할 수 있다.
- upload 과정에서, hash ID verification과 signature authentication 으로 사용자를 확인한다.
- blockchain auth system은 cloud와 독립적이다.
![image](https://user-images.githubusercontent.com/68576770/97248606-7f26ee80-1845-11eb-9ae9-6957ed84b6d8.png)
- hash_f : upload file을 hash하여 verification
- sig : user_id를 signature하여 authentication
- 1. Req가 upload 일 때,
    - upload file 정보와, signature 검증 결과를 반환
- 2. Req가 download 일 때,
    - file의 모든 정보의 유사성을 percentage로 계산하여 download unit으로 전송
### Performance Analysis
- Ethereum Wallet Backend를 사용한 타당성 검증
    - sendTransaction, call method, lookup accounts, sign 기능이 포함되어 있음
- Method 1 : pure blockchain
- Method 2 : hybrid blockchain with cache
- Method 3 : traditional database
- throughout과, response time은 method 3, method 2, method 1 순으로 좋다. 따라서 사용자 체감 성능도 traditional database가 좋다.
- 하지만, cloud@blockchain은 authentication and validation 과정때문에 느린 것이고, 대신 privacy를 보호해준다.
- 즉, 기존 db에 비해 cloud@blockchain이 처리량도 적고 반응 속도도 느리지만, more secure, easy to cross platform, high anonymity, return the right to file's owner의 장점이 있다.