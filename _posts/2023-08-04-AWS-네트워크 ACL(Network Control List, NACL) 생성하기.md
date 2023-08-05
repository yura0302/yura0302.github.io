---
layout: post
title: AWS-네트워크 ACL(Network Control List, NACL) 생성하기
---

![인바운드 규칙](/assets/images/inbound.png)

인바운드 규칙

![아웃바운드도 위와 동일한 규칙 적용중](/assets/images/outbound.png)

아웃바운드도 위와 동일한 규칙 적용중

- 모두 허용 규칙이 적용되어 있으므로 블랙 기반 결합 방식임을 확인할 수 있다.

![networkACL](/assets/images/network.png)

- 새로 만든 NACL은 연결된 서브넷이 없으며 기본 NACL이 아님을 확인할 수 있다.
- 새로 생성한 NACL은 모두 거부 규칙만 최하단에 저장돼 있어 화이트 기반 결합 방식임을 알 수 있다. (아웃바운드도 이와동일)

![스크린샷 2023-08-02 오전 3.46.31.png](/assets/images/inbound-2.png)

![스크린샷 2023-08-02 오전 3.47.18.png](/assets/images/outbound-2.png)

- 인바운드와 아웃바운드 규칙을 위 과정처럼 변경 (유형값이 다름에 유의)

![신규 NACL](/assets/images/acl.png)

신규 NACL

- 기본 NACL에 연결되었던 서브넷 2개를 새로운 NACL에 연결
- 기본 NACL에는 연결이 해제되어 4개의 프라이빗 서브넷만 연결된 상태

![기본NACL](/assets/images/acl-2.png)

기본NACL

- **NACL 생성 결과**
  - 새로운 NACL을 만들어 클라이언트가 서브넷에 접속할 수 있는 환경 구축
  - 기본 NACL과 연결을 해제하고 새로운 NACL에 연결
