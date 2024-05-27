# 쿠버네티스 명령어
쿠버네티스는 매니페스트라는 텍스트 파일을 이용해 클러스터를 조작한다. 매니페스트는 yaml이나 json 형식으로 선언한다.

- 파드 : 생성, 실행 확인, 변경, 삭제, 파드 내부에서 명령 실행
- 레플리카셋 : 생성, 실행 확인, 변경, 삭제
- 디플로이먼트 : 생성, 실행 확인, 변경, 삭제
- 서비스 : 생성, 실행 확인, 변경, 삭제
    ```
    ## 파드 - 생성, 실행 확인, 변경, 삭제, 파드 내부에서 명령 실행
    
    # 파드 생성(실행)
    kubectl apply -f pod.yaml
    # 파드 실행 확인
    kubectl get pods
    # 실행 중인 파드 내부에서 명령 실행
    kubectl exec -it my-pod -- echo Hello Kubernetes
    # 실행 중인 파드 변경
    kubectl apply -f pod.yaml
    # 실행 중인 파드 삭제
    kubectl delete -f pod.yaml
    ```
    ```
    ## 레플리카셋 - 생성, 실행 확인, 변경, 삭제
    # 레플리카셋 생성(실행)
    kubectl apply -f replicaset.yaml
    # 레플리카셋 실행 확인
    kubectl get replicasets
    # 레플리카셋 삭제
    kubectl delete -f replicaset.yaml
    ```