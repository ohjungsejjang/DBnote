오라클 다운법 계정 활성화.

*DATABASE DOWNLOAD

1) oracle.com 사이트에 들어간다

2) 사이트에 회원가입을 한다.

3) 가입 후 로그인을 한다.

4) 사이트 화면상에 Downloads 를 클릭한다.

5) Database를 누른다.

6) Database 11g Enterprise/Standard Editions를 누른다.

7) 맨위 상단에 

   "You must accept the OTN License Agreement to download this software".라고 있다
.
   대충 해석해보면 다운을 위해서는 뭐 동의해야된다는 그렇 뜻인거 같다.

   아무튼 Accept License Agreement를 누른다.

8) 아래로 커서를 내리다보면 Oracle Dabtabase Express Edition 이라고 나온다.

   거기에 Oracle Database 11g Releas 2 Express Edition for Window 64 를 누르고 다운받는다.

9) Download 받은 파일경로 들어가서 오른 클릭후 압축 풀기한다.

10) 압축풀기 후 새로 생긴 파일 들어가서 setup 다운

11) 오라클 파일 설치중에 패스워드 화면이 나온다

이것은 SYSTEM계정이 되므로 신중하게 입력한다.
그리고 계속 설치 진행을 하면된다.




*DEVELOPER TOOLS DOWNLOAD

1) 사이트 화면상에 Downloads 를 클릭한다.   

2) Developer Tools를 누른다.

3) SQL Developer를 누른다.

4) 맨위 상단에 

   "You must accept the OTN License Agreement to download this software".라고 있다
.
   대충 해석해보면 다운을 위해서는 뭐 동의해야된다는 그렇 뜻인거 같다.

   아무튼 Accept License Agreement를 누른다.   

5) Windows 64-bit with JDK 8 included 옆에 Download를 누른다.

6) Download 받은 파일경로 들어가서 오른 클릭후 압축 풀기한다.

7) sqldeveloper 압축 해제된 파일을 c드라이브로 복사한다.

8) sqldeveloper 폴더에 들어가면 sqldeveloper.exe 파일이 있다. 

9) 오른쪽 클릭후 보내기에서 바탕화면으로 보내기 한다.


*계정 활성화 하기.

1) 윈도우버튼+R 버튼을 누르면 실행창이 뜬다.

2) 실행창에 cmd를 입력한다.

3) 그러면 시스템 cmd.exe 프로그램이 화면상에 나온다.

4) cmd입력란에 sqlplus를 입력한다.

5) 그러면 SQL*Plus: Release 11.2.0.2.0 Production on 일 7월 7 22:10:57 2019

Copyright (c) 1982, 2014, Oracle.  All rights reserved.

대충 이런 버전내용과 같이 Enter user-name: 이 나온다.

6) Enter user-name: 옆에 system을 입력한다.

7) Enter password: 옆에 비밀번호를 입력한다.

(커서만 깜빡이고 입력된 내용이 화면상에 표시되지 않으니 당황하지 말자.)

8) Connected to:

Oracle Database 11g Express Edition Release 11.2.0.2.0 - 64bit Production라는 내용이 나오면

system계정으로 잘 접속 된 것이다.

9) 그다음 hr이라는 계정을 활성화 시키기 위해서는 계정 생성을 해야한다.

CREATE USER 사용자 아이디 IDENTIFIED BY 사용자 비번;

CREATE USER hr IDENTIFIED BY hr; 을 입력하면 생성완료된다.

11) 그다음 계정의 잠금을 해제해야 접속이 가능하다.

alter user 아이디 identified by 비번 account unlock;을 해주어야 잠금이 해제된다.(system 계정으로만 가능.)

alter user hr identified by hr account unlock;

반대로 잠금은 unlock을 lock으로 입력하면된다.

12) 접속이 되는지 확인해보자
지금은 system 계정으로 들어와져 있기떄문에 exit을 사용하여 계정을 빠져나간다.

13) 계정이 빠져나갔으면 다시 입력란에 sqlplus를 입력한다.

14) 그러고 위와같이 똑같은 방법으로 hr계정을 접속하면된다.

*Developer tool 접속

1) sqldeveloper파일을 누른다.

2) 왼쪽 상단에 보면 초록색 +표시를 누른다.

3) Name hr 기입, 사용자 이름 hr기입, 비밀번호 자기가 설정한 비번 입력.

4) 그러고 밑에 테스를 누른다. 그러면 왼쪽 하단에 상태:성공 또는 다른내용이 나올것이다.

5) 성공으로 떳다면 접속을 누르고 접속하면되고 그렇지 않다면 잠금을 풀어줘야 하기 때문에

cmd.exe프로그램을 들어가서 계정 활성화 과정에서 나온 잠금 해제 방법을 사용한다.

6) 그래도 안된다하면 권한 설정이 안되어 있기 때문에 system 계정으로 들어가서 접속 권한을 부여하여야한다.

7) 부여하는 방법은 system계정으로 들어가서 grant 권한리스트 to 아이디;를 입력.

grant connect to hr;를 입력하면 된다.

제가 알고 있는 권한 부여는 3가지로

```
1. connect : 로그인 권한

2. resource : 자원을 사용 할 수 있는 권한

3. dba : db 관리자 권한
```

이렇게 있다.

권한 부여는 위에 내용과 같이 grant connect, resource, dba to hr;

즉 내가 부여하고싶은 권한리스트를 사용하면된다.






