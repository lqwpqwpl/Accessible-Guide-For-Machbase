# 설치
Machbase가 설치되지 않았다면 다음 링크를 참고해 설치해 주시기 바랍니다.
윈도우즈 설치 가이드: https://machbase.atlassian.net/wiki/spaces/M7M/pages/417759611/Windows

물론, 다른 OS에 대한 설치 가이드 또한 위 문서의 좌측에 위치한 목차에 존재합니다.

# machsql 접근 방법

## 윈도우즈에서 UI를 통해 접근하기
- 설치한 이후, `C:/Machbase/programs/` (혹은 그에 해당하는) 경로에 있는 `machwin.exe` (혹은 설치된 OS에 해당하는 실행) 파일을 실행해 주세요.
- 프로그램 UI의 좌측 최상단에 있는 `Machbase` 버튼을 클릭한 뒤, `machsql` 옵션을 선택해 주세요.
- 실행한 뒤 로그인하라는 문구가 뜰 것입니다. 접근 IP 주소, ID, 비밀번호를 각각 순서대로 입력한 뒤 machsql을 사용할 수 있습니다.
- [여기](#설치-후-기본값-계정)에서 계속하시면 됩니다.

## 명령어 실행을 통해 접근하기
- 쉘에서 다음과 같은 명령어를 입력하면 machsql에 로그인해 명령어를 전송할 수 있습니다.
```sh
machsql -s localhost -u SYS -p manager
```

자세한 명령어 사용 방법은 https://machbase.atlassian.net/wiki/spaces/MANUAL/pages/159612968/MACHSQL 문서를 참고해 주시기 바랍니다.

# 설치 후 기본값 계정

```
id: SYS
pw: manager
```

💡 올바르지 않은 비밀번호를 입력할 경우 machsql에서 명령어를 전송하실 수 없다는 점 참고해 주세요.

계정 변경과 관련된 내용은 https://machbase.atlassian.net/wiki/spaces/M7M/pages/417761757 문서를 참고해 주시기 바랍니다.

# 테스트 코드

다음은 machsql이 제대로 작동하는지 검증하기 위한 간단한 코드입니다.

테스트용 테이블을 생성한 후, 행을 추가하고 출력한 뒤 테이블을 삭제합니다.

```sql
CREATE TABLE test_table (id INTEGER, name VARCHAR(100) PROPERTY(MINMAX_CACHE_SIZE = 0)); -- 테스트할 테이블 생성
INSERT INTO test_table values (0, "test"); -- 값 추가
SELECT * FROM test_table; -- 값 출력
DROP TABLE test_table; -- 테이블 삭제
```
