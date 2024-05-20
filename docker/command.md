# 도커 명령어
### 라이프 사이클
도커에서 컨테이너가 취할 수 있는 상태는 생성, 실행, 정지, 일시정지, 삭제가 있다.
도커 명령어는 도커에서 컨테이너 또는 컨테이너 이미지를 조작할때 사용하는 명령어다.

### 도커 명령어
- 컨테이너 시작 / 분리 / 표시 / 정지 / 삭제

  **분리 : 컨테이너 실행한 상태에서 컨테이너 빠져나가는 방법
    ```
    docker container run i -t centos:lastest /bin/bash
    # 컨테이너 상태 확인
    docker container ls
    # 컨테이너 정지
    docker container kill
    # 정지한 컨테이너 확인
    docker container ls -a
    # 컨테이너 삭제
    docker container rm 0123456789ab
    ```
- 컨테이너 이미지 생성 / 표시 / 삭제
  ```
  # 컨테이너 이미지 생성
  docker container commit 0123456789ab my-repository:my-tage
  # 컨테이너 이미지 상태 확인
  docker image ls
  # 컨테이너 이미지 삭제
  docker image rm my-repository:my-tag
  ```
- 도커 파일로 컨테이너 이미지 생성
  - 수동으로 터미널에 명령어 쳐서 컨테이너 이미지 만드는 대신, 파일에 컨테이너 이미지 생성 명령어를 넣어놓고 자동으로 컨테이너 이미지 생성하도록 한다.
  