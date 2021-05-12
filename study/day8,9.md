HLM의 체인코드 : 스마트 컨트랙트와 같은 개념 (data 정의 기능)
허가받은 사람만 접근 가능하기 때문에 책임을 물을 수 있음

보증정책 : app 레벨에서 원장에 접근하는 일반적인 체인코드와는 달리 HLF의 시스템 레벨에서 수행되는 체인코드
Endorser - 체인 코드 수행
Committer - 원장정보 가짐

levelDB,CouchDB - NoSQL , 개인 데이터나 world state 저장할때 효율 
world state : 현재값 변경될때마다 블록체인으로 이력 저장

블록체인은 확장성, 검색이 단점, 이력 검색의 효율 매울 떨어짐(비트코인,이더리움)
HLF는 인덱스 이용해서 쿼리 지원

노드의 구성
- 블록체인 (분산원장)
- 체인코드 : 도커에서 실행됨
- 월드스테이트 (key-value state)

주요 체인코드 관련 처리
- 배포 Deploy
- 호출 Invoke / 블록생성 ws 변경, 자산생성,수정,삭제 = Ordering(블록 생성)
- 조회 Query


네트워크 -> 체인코드 -> 웹 서비스

네트워크 구축
1. Ordering Service (블록 생성)  // solo,kafka,RAFT
2. 컨소시움 구성 (CA부터 생성)
3. 컨소시움이 이용하는 채널 생성, 그룹간 커뮤니케이션 메카니즘

peer에 설치 채널에 인스턴스

기업용 요구사항
- 신원관리 : 책임 스푸핑 방지
- 개인정보 보호
- 액세스 제어
- TX의 기밀성
- 재생공격 대처
- PKI 인증서와 전자서명

Ecert : enrollmentID + 공개키
Tcert : 암호화된 enrollmentID, 공개키, 암호화 키

private data : 권한 부여, 개인정보 보호의 내용

합의 : BC 모든 참여자의 원장에 일관성이 있는지 확인, 탈중화 서버이기 때문에 데이터 동일화 체크 필요

HLF 합의 : Endorse -> Order (멀티체인 방지) -> Validate (data가 꼬이지 않도록, os에서 race condition)
