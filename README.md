<h1> TIL
  <h3>Today I Learned </h3>
● 오늘 배운 내용 정리하고 공부하기 <br>

## 
● [Call by reference VS Call by value](https://github.com/JeonDoHyun/TIL/blob/main/JAVA/Callby.md)<BR>
● [자바 용어 간단정리편](https://github.com/JeonDoHyun/TIL/blob/main/JAVA/JAVA%20%EC%9A%A9%EC%96%B4%20%EB%B0%8F%20%EA%B0%9C%EB%85%90%20%EA%B0%84%EB%8B%A8%EC%A0%95%EB%A6%AC.md)<BR>
●  [가비지 컬렉션(GC)] <BR>
●  [JAVA의 메모리 구조 ](https://github.com/JeonDoHyun/TIL/blob/main/JAVA/JAVA%EC%9D%98%20%EB%A9%94%EB%AA%A8%EB%A6%AC%EA%B5%AC%EC%A1%B0.md) <BR>
● [String 생성방식의 차이점 ( new VS " "(리터럴) )](https://github.com/JeonDoHyun/TIL/blob/main/JAVA/String%20%EC%83%9D%EC%84%B1%20%EB%B0%A9%EC%8B%9D%EC%9D%98%20%EC%B0%A8%EC%9D%B4%EC%A0%90.md)  <BR>

● [SPRING 기본개념](https://github.com/JeonDoHyun/TIL/blob/main/Spring/SPRING%20%EA%B0%9C%EB%85%90%EC%A0%95%EB%A6%AC.md)<br>
● [MVC 처리과정](https://github.com/JeonDoHyun/TIL/blob/main/Spring/MVC%20%EC%B2%98%EB%A6%AC%EA%B3%BC%EC%A0%95.md) <BR>
● [DispatcheServlet에 대하여...] <BR>
● [Interceptor 정리](https://github.com/JeonDoHyun/TIL/blob/main/Spring/%EC%9D%B8%ED%84%B0%EC%85%89%ED%84%B0%20%EC%A0%95%EB%A6%AC.md) <BR>
● [logback 정리](https://github.com/JeonDoHyun/TIL/blob/main/Spring/logBack%20%EC%A0%95%EB%A6%AC.md)  <BR>
● [Spring AOP](https://github.com/JeonDoHyun/TIL/blob/main/Spring/logBack%20%EC%A0%95%EB%A6%AC.md)  <BR>

● [HTTP 정리](https://github.com/JeonDoHyun/TIL/blob/main/WEB/HTTP%20%EC%A0%95%EB%A6%AC.md)<br>

● [Web Storage 정리](https://github.com/JeonDoHyun/TIL/blob/main/WEB/WebStorage%20%EC%A0%95%EB%A6%AC.md)<br>

● [XML Parser 정리](https://github.com/JeonDoHyun/TIL/blob/main/WEB/HTTP%20%EC%A0%95%EB%A6%AC.md)<br>
● [Spring Security]

● 므모생 사이드프로젝트하는데 첫번째 시간걸린것,,,
설정 파일을 서브모듈로 받아야하는데 private repo라 내 계정@github을 해야하는건 알겠는데 모듈 싱크를 맞춰야하는지 몰랐다 <br>

git submodule update 시 레포지토리를 찾지 못하는 경우는 일반적으로 서브모듈의 URL에 접근 권한이 없거나, URL이 올바르지 않을 때 발생합니다. 특히 비공개 레포지토리일 경우, 인증 정보가 필요합니다. 이 문제를 해결하려면 다음 방법을 시도해 보세요.

1. .gitmodules 파일 확인 및 수정
.gitmodules 파일을 열어서 B 레포지토리의 URL이 인증 정보와 함께 정확히 입력되어 있는지 확인합니다. 예를 들어, .gitmodules 파일이 다음과 같이 되어 있어야 합니다.

plaintext
코드 복사
[submodule "path/to/config"]
    path = path/to/config
    url = https://<username>:<token>@github.com/team-meumo/mms-backend-config.git
이 후 .gitmodules 파일을 수정했으면 다음 명령어로 서브모듈 설정을 다시 로드하세요.

bash
코드 복사
git submodule sync
2. 인증 정보 캐시 (Git Credential Manager 사용)
매번 인증 정보를 입력하기 번거롭다면, Git Credential Manager를 사용하여 인증 정보를 캐시할 수 있습니다. 아래 명령어를 실행하여 캐시를 설정하세요.

bash
코드 복사
git config --global credential.helper cache
그런 다음 git submodule update --init --recursive를 실행하면 한 번만 인증 정보를 입력하고 그 후로는 캐시된 인증 정보로 접근할 수 있습니다.

3. 서브모듈 재설정
서브모듈 URL을 수정하고 다시 추가하려면 다음을 수행합니다.

기존 서브모듈을 제거합니다.

bash
코드 복사
git submodule deinit -f -- path/to/config
rm -rf .git/modules/path/to/config
git rm -f path/to/config
인증 정보가 포함된 URL로 서브모듈을 다시 추가합니다.

bash
코드 복사
git submodule add https://<username>:<token>@github.com/team-meumo/mms-backend-config.git path/to/config
추가 후 서브모듈을 업데이트합니다.

bash
코드 복사
git submodule update --init --recursive
이 방법으로도 문제가 해결되지 않는다면, 설정 중 어느 부분에서 오류가 발생하는지 추가로 확인해 볼 수 있습니다.
