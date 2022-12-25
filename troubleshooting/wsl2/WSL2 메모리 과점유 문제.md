# WSL2 메모리 과점유 문제

## 상황

윈도우10에서 WSL2로 작업하다가, 컴퓨터가 느려지는 기분이 들어서 작업 관리자를 통해 확인했는데, 사용 중인 메모리가 15GB에 달했음. 

<br/>



## 원인

작업 관리자를 통해 VMMEM process가 메모리를 9GB 점유하고 있음을 확인함. 문제의 원인을 인터넷에서 찾아봤는데, 대략적으로 다음과 같았음

- 리눅스에서 파일에 접근할 때, 리눅스는 파일 접근에서 사용한 정보를 메모리에 캐싱

- WSL2는 리눅스의 메모리 사용량에 따라, 메모리 크기를 동적으로 증가 또는 감소 시킴

<br/>

결과적으로 리눅스에서 캐싱을 많이하면 할 수록, WSL2는 사용할 메모리 크기를 증가 시킴

작성된 시점이 2022년 12월 25일인데, 지금까지 관련된 issue는 여전히 open된 상태.

- [WSL 2 consumes massive amounts of RAM and doesn&#39;t return it · Issue #4166 · microsoft/WSL · GitHub](https://github.com/microsoft/WSL/issues/4166) 참고

<br/>

## 해결

`C:\Users\사용자명` 경로에서 `.wslconfig`를 만들고, 다음의 내용을 추가한다.

- 위의 경로는 window10에 대한 경로(i.e WSL2에 대한 경로가 아님)

```
[wsl2]
 memory=4GB
 swap=0
 localhostForwarding=true
```

window10에서 명령 프롬프트(cmd)를 열어서 `wsl --shutdown` 입력
