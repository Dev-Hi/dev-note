# spring initializr으로 생성한 프로젝트를 WSL2로 가져오기



spring initializr에서 생성한 프로젝트를 window10에 다운받고, 압축을 해제하는 것은 window10에서 intellij로 개발할 때랑 동일하다. 

<br/>여기서 추가적으로 작업해야할 것은 압축 해제한 폴더를 WSL2로 옮기는 것이다. WSL2를 실행하고, spring project를 위치할 경로 위에 `explorer.exe .`를 입력한다.

그러면 window10에 wsl2에 대한 파일탐색기가 다음과 같이 열리는 것을 확인할 수 있다.

![](C:\Users\abc123\AppData\Roaming\marktext\images\2022-12-31-20-19-50-image.png)



<br/>

window10에 있는 압축해제된 spring project 폴더를 drag & drop으로 위의 탐색기 위에 올려두면 된다. 사실 언급된 방법으로 spring project에대한 폴더로 gateway를 wsl2에 반영했다. WSL2에서 해당 폴더가 있는 경로에 `ls` 입력하면 정상적으로 spring project 폴더가 존재하는 것을 확인할 수 있다.




