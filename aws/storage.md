# AWS 스토리지 서비스
- AWS 스토리지 서비스는 블록 스토리지(EBS)와 파일 스토리지(EFS), 객체 스토리지(S3)가 있다.

### Amazon EBS (Elastic Block Store)
- EBS 스토리지는 AWS 관리 콘솔에서 필요한 용량과 성능에 맞추어서 볼륨을 생성한 후 EC2 인스턴스에 연결하고 파일 시스템을 포맷한 후 사용한다. 포맷이 완료되면 해당 볼륨을 서버에서 마운트한 후 데이터를 해당 디렉터리에 저장해서 사용한다.
- 인스턴스는 다수의 볼륨을 연결하여 사용할 수 있으나 하나의 EBS 볼륨은 한번에 하나의 인스턴스에만 연결할 수 있고, 해당 인스턴스에서 지원하는 형태의 시스템으로 포맷해야만 사용할 수 있다.
- EBS 스토리지의 대표적인 EBS 스냅샷은 말 그대로 특정 시점에 포인트를 찍어서 그 시점으로 되돌아갈 수 있는 지점을 만드는 기능이다.
- 스냅샷은 기본적으로 Amazon S3라는 스토리지 공간에 저장되어 여러 가용 영역에 자동으로 복제된다. 스냅샷은 다른 계정으로 공유할 수도 있고 스냅샷을 이용하여 손쉽게 다른 리전으로 복제할 수 있다.

### Amazon EFS (Elastic File Store)
- 클라우드 환경과 온프레미스 환경에서 사용할 수 있는 완전 관리형 네트워크 파일 시스템
- 완전 관리형이란 클라우드에서 하드웨어 프로비저닝 유지 관리, 소프트웨어 구성, 모니터링, 복잡한 성능 조절 등 모든 것을 관리하기 때문에 사용자 입장에서는 별다른 관리가 필요없단 의미

### Amazon S3 (Simple Storage Store)
- Amazon S3는 객체에 대해 빠르고 내구성과 가용성이 높은 키 기반의 접근성을 제공하여 데이터의 저장 및 검색에 특화된 객체 스토리지다.
  - S3는 하나의 리전에 최소 3개 이상의 물리적으로 분리된 가용 영역에 데이터를 복제해 저장해 매우 높은 내구성과 가용성을 가지는 것이 특징(데이터 손실 최소화)