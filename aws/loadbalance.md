# AWS 부하 분산 서비스

### Amazon ELB (Elastic Load Balance)
- 부하 분산 서비스
- Amazon ELB 구성 요소
  - 로드 밸런서
  - 대상 그룹
  - 리스너 : 리스너는 로드 밸런서에 연결된 프로토콜과 포트를 사용하여 클라이언트 요청을 수신하고, 요청을 처리할 대상 그룹을 선택해 라우팅한다.
- Amazon ELB를 생성하면 설정한 가용 영역별로 로드 밸런서 노드가 생성되고 앞단에 리스너를 실행한다. 이런 리스너는 다양한 프로토콜(HTTP, HTTPS, TCP 등)을 지원하며, 요청에 대한 대상 그룹의 라우팅을 정의한다. 이에 따라 로드 밸런서는 가용 영역에 속한 대상 그룹의 인스턴스로 트래픽을 전달한다.
- Amazon ELB 종류
  - CLB(Classic Load Balance)
  - ALB (Application Load Balance)
    - HTTP/HTTPS 같은 웹 애플리케이션 프로토콜 지원 (L7 로드밸런서)
    - 웹 애플리케이션에 특화된 세밀한 라우팅을 제어할 수 있어서 웹 애플리케이션을 위한 로드벨런서로 사용한다.
  - NLB (Network Load Balance)
    - TCP, UDP, TLS 프로토콜 지원(L4 로드밸런서)
    - 대규모 네트워크 트래픽을 처리하고 대상 그룹의 대상이 IP 주소로 식별될 때 유용
    - 다른 로드 밸런서보다 높은 처리량과 빠른 응답시간을 보장하므로 게임 서버, VoIP 서비스, 미디어 스트리밍 등에서 사용된다.
  - GWLB (GateWay Load Balance)

