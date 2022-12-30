# 노트북 재부팅 후, k9s에서 minikube를 확인할 수 없는 문제

## 환경

window10, WSL2, k9s, minikube

## 문제

노트북 재부팅 후, k9s에서 minikube를 확인할 수 없었음. docker container에서 minikube가 실행된 것을 확인했으나, 여전히 연결이 안되었음. 

- k9s는 wsl2위에서 실행

<br/>

다음의 결과를 반환했음

```
The connection to the server 127.0.0.1:57453 was refused - did you specify the right host or port? 
```

<br/>

## 원인

WSL2에서 `minikube status`명령어를 통해, 아래의 결과를 얻었음



```
type: Control Plane
host: Running
kubelet: Stopped
apiserver: Stopped
kubeconfig: Misconfigured  
```

<br/>

다시 말해, minikube에 필요한 구성요소들이 실행되지 않았음. 따라서 이들을 실행해줘야함.

<br/>

## 해결

`minikube start`를 이용하여 minikube를 구성하는 요소들을 실행상태로 만들어준다.

그리고 `minikube status`를 입력하면 정상적으로 실행되는 것을 확인할 수 있다.



```
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: configured  
```
