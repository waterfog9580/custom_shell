# custom_shell

 명령어를 입력받아 처리하는 간단한 쉘 프로그램입니다.

- Default command set
ls, cd, help, exit로 구성된 쉘에서 미리 실행할 수 있는 명령어를 구현하였습니다.


# 기본 명령어
설명
- ls 
dirent.h 헤더파일의 구조체에 있는 readdir함수를 이용하여 
현재 디렉토리의 파일 정보를 읽어와 출력하도록 작성하였습니다.
- cd 
chdir 함수를 이용하여 두 번째 인자에 입력된 주소로 현재 디렉토리를 변경합니다
- help
쉘의 기본 명령어를 출력하도록 하였습니다.
- exit 
쉘을 종료합니다.



- Shell logic

exec_handler()는 입력받은 command line을 tokenizer를 통해 토큰화하여 저장합니다. 

parse_default()를 통해 명령어가 기본명령어인지 확인하고 기본 명령어 셋에 포함되어 있으면 
exec_default()을 통해 명령어에 해당하는 함수를 실행합니다
만약 기본명령어가 아니면 fork를 통해 자식프로세스를 생성합니다

parse_Redirect()를 통해 redirect를 지시하는 인자(>)가 포함되어 있는지 확인하고 포함되어 있으면 exec_redirect()를 실행하여 해당 인자 다음의 인자로 출력을 재지정하여 수행합니다.

parse_Background()는 background를 지시하는 인자(&)가 포함되어 있는지 확인하고 포함되어 있으면 부모 프로세스가 wait()를 실행하지 않게 하여 자식 프로세스의 백그라운드 프로세싱을 수행합니다.