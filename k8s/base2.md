### 레플리카셋
- 파드를 관리하기 위한 단위
- 대상 파드의 복제를 지정한 수만큼 유지하는 기능
- 파드는 하나 이상의 컨테이너 그룹이고, 레플리카셋은 하나 이상의 파드 그룹
- 파드는 다양한 유형의 컨테이너를 포함하고 있는 반면, 레플리카셋은 한 유형의 파드만 포함 가능
- 레플리카셋을 사용하면 파드 수를 지정한 만큼 일정하게 유지할 수 있어서 컨테이너를 헬스 체크할 수 있고, 중지한 컨테이너를 다시 시작할 수 있다. 또한 파드 수를 늘리거나 줄여서 스케일링 할 수도 있다.

### 디플로이먼트
- 하나 이상의 레플리카셋 그룹
- 레플리카셋이 유지하는 파드 수를 증감하거나 레플리카셋을 생성
- 자신을 포함하는 레플리카셋이나 파드를 자동으로 갱신하기 위한 구조를 갖추고 있기 때문이다.
  - 레플리카셋을 이용하여 파드 수를 조절하여 스케일링 및 롤링 업데이트를 할 수 있긴 하지만, 디플로이먼트를 사용하면 쿠버네티스가 자동으로 파드 수를 조절하고 새 레플리카셋을 생성할 수 있다.
- 디플로이먼트 컨트롤러 : 디플로이먼트를 특정한 상태로 유지하는 컨트롤러

### **쿠버네티스의 서비스란 컨테이너에 접속하기 위한 창구인 엔드포인트를 제공하는 방식**
- 외부에서 컨테이너에 접속하려면 직접 접속하는 것이 아니고 엔드포인트를 이용해 간접적으로 접속하는 것이다.
- 가상 IP 주소에 접속하면 네트워크 주소 변환에 따라 대상 컨테이너로 전달된다.
- 쿠버네티스 클러스터 내에 서비스를 생성하면 엔드포인트가 되는 IP 주소가 생성되고, 이 IP 주소를 대상으로 하는 패킷은 서비스 뒤에 있는 파드로 전달된다.

### 플라넬
컴퓨터 파드끼리 통신하는 방식
- 파드 내 통신 : 같은 파드 내 컨테이너는 네임스페이스를 공유하니깐 로컬 호스트를 이용하여 컨테이너 간 통신이 가능
- 파드 간 통신 : **파드에 고유한 IP가 할당되고, 할당된 IP로 접속하는 방식**으로 외부 파드 간 통신을 한다.
- flanneld : 플라넬이 IPv4 네트워크를 구축하기 위해 쿠버네티스 클러스터를 구동하는 모든 컴퓨터에서 구동되는 에이전트 프로그램
  - IP 주소로 파드 간 통신할 때, 목적지가 되는 파드의 컴퓨터를 특정해 컴퓨터에 패킷을 전송하는 역할을 담당한다.
 