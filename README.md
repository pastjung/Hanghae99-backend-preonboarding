![spartacodingclub](https://noticon-static.tammolo.com/dgggcrkxq/image/upload/v1719643111/noticon/yeqwdeuiybor5m4hh7zj.png)
# Hanghae99 Preonboarding Backend Course

**취업시장에 침투하기 전에, 실전과 같은 훈련으로 코딩의 감(떫음)을 찾아서 세상에 스파르타st를 보여주자.<br />
어렵다고 느끼는 제군들도 있겠지만, 힌트를 보면서 잘 따라 와주기를 바란다.**



### 🎖️ 훈련 메뉴

---
- [ ]  Junit를 이용한 테스트 코드 작성법 이해
- [ ]  Spring Security를 이용한 Filter에 대한 이해
- [ ]  JWT와 구체적인 알고리즘의 이해
- [ ]  PR 날려보기
- [ ]  리뷰 바탕으로 개선하기
- [ ]  EC2에 배포해보기

### Day 1 - 시나리오 설계 및 코딩 시작!

---
**Spring Security 기본 이해**

- [ ]  Filter란 무엇인가?(with Interceptor, AOP)
  
  - [x] 필터 ( Filter ) 란
  
    서블릿 컨테이너에 의해 관리되며, 특정 URL 패턴에 매핑되어 해당 패턴에 매칭되는 모든 요청과 응답을 가로채 이를 조작하거나 특정 로직을 실행할 수 있도록 하는 컴포넌트
    - 필터는 체인 형태로 구성될 수 있으며, 여러 필터가 순차적으로 실행된다.
    - 필터는 주로 웹 요청의 전처리나 후처리에 사용된다.

  - [x] 인터셉터 ( Interceptor ) 란
  
    스프링 MVC에서 제공하는 기능으로, 컨트롤러의 요청 처리 전후 또는 뷰가 렌더링되기 전에 특정 로직을 실행할 수 있도록 한다.
    - 인터셉터는 주로 인증, 권한 부여, 로깅, 트랜잭션 관리 등의 공통 관심사를 처리하는 데 사용된다

  - [x] AOP ( Aspect-Oriented Programming, 관점 지향 프로그래밍 ) 란
    
    OOP(Object Oriented Programming, 객체지향 프로그래밍)를 돕는 보조적인 기술로, 관심사의 분리(기능의 분리)의 문제를 해결하기 위해 만들어진 프로그래밍 패러다임
    - AOP 는 기능을 핵심 관심사항(Core Concern)과 공통 관심 사항(Cross-Cutting Concern)으로 분리시키고 각각을 모듈화 하는 것을 의미
     
- [ ]  Spring Security란?
      
  스프링 프레임워크 기반의 애플리케이션에서 보안을 제공하기 위한 프레임워크
  - 기본적으로 서블릿 필터를 기반으로 동작
  - 다양한 인증 메커니즘 ( 예: 폼 로그인, HTTP 기본 인증, OAuth 등)을 지원
  - 메서드 수준의 보안, URL 패턴에 따른 접근 제어, CSRF 방지, 세션 관리 등의 다양한 보안 기능 제공
  
  - [x] 주요 개념
  1. 인증 ( Authentication ) : 사용자가 누구인지 확인하는 과정
  2. 권한 부여 ( Authorization ) : 인증된 사용자가 특정 리소스에 접근할 수 있는 권한이 있는지 확인하는 과정
  3. 필터 체인 ( Filter Chain ) : 여러 보안 필터가 순차적으로 요청을 처리하는 구조. 각 필터는 특정 보안 기능을 담당
  
**JWT 기본 이해**

- [ ]  JWT란 무엇인가요?
      
  클라이언트와 서버 사이에서 통신할 때 권한을 위해 사용하는 토큰
  - 웹 상에서 정보를 Json 형태로 주고 받기 위해 표준규약에 따라 생성한 암호화된 토큰으로 복잡하고 읽을 수 없는 String 형태로 저장되어 있다.
  - JWT 는 헤더(Header), 페이로드(Payload), 서명(Signature) 세 파트로 나눠져서 각 부분은 base64url로 인코딩되어 점(.)으로 구분된다.
  
- [ ] JWT 구성
  1. 헤더(Header)
	   - JWT 의 타입과 해싱 알고리즘을 정의
  2. 페이로드( Payload )
  	 - 토큰에 담길 정보인 클레임(Claims)을 포함한다
  3. 서명 ( Signature )
  	 - 헤더와 페이로드를 인코딩한 후, 비밀 키를 사용하여 해싱한 값
  	 - 서명은 토큰의 무결성을 검증하는 데 사용
  
- [ ] JWT 작동 원리
  1. 클라이언트 인증
  	 - 사용자가 로그인하면 서버는 사용자 정보를 바탕으로  JWT를 생성하고 클라이언트에게 반환
  2. 클라이언트 요청
  	 - 클라이언트는 이후의 요청에 JWT를 포함하여 서버에 보낸다
	  ( 일반적으로 HTTP 헤더에 'Authorization: Bearer <token>' 형태로 포함 )
  3. 서버 검증
	   - 서버는 요청을 받을 때마다 JWT의 서명을 검증하고, 토큰의 무결성과 유효성을 확인
  4. 정보 접근
	   - 서명이 유효하면 서버는 JWT의 페이로드에 포함된 정보를 사용하여 요청을 처리
  
- [ ] JWT 장점
  1. 자기 포함
  	 - 필요한 모든 정보를 자체적으로 포함하므로, 서버는 추가적인 데이터베이스 조회 없이 토큰의 유효성을 검증할 수 있다
  2. 확장성
  	 - 분산 시스템에서 인증 정보를 중앙 서버 없이도 쉽게 검증할 수 있다
  3. 보안
  	 - 서명된 토큰은 데이터가 변경되지 않았음을 보장
  	 - TLS ( HTTPS )를 사용하여 전송 중 토큰의 기밀성을 보호
  
- [ ] JWT의 단점 및 고려 사항
  1. 토큰 탈취 위험
  	 - JWT가 탈취되면 만료될 때까지 악용될 수 있다
  	 - 토큰 탈취를 방지하기 위해 HTTPS를 사용하고, 토큰의 만료 시간을 짧게 설정하는 것이 좋다
  2. 페이로드의 크기에 따라 토큰 크기가 커질 수 있다
  3. 무효화 어려움
	   - 한 번 발급된 JWT는 만료 전까지 유효하기 때문에 무효화하는 표준적인 방법이 없어 이를 위한 별도의 메커니즘(예: 블랙리스트)을 구현해야 할 수도 있다.

**토큰 발행과 유효성 확인**

- [ ]  Access / Refresh Token 발행과 검증에 관한 **테스트 시나리오** 작성하기

**유닛 테스트 작성**

- [ ]  JUnit를 이용한 JWT Unit 테스트 코드 작성해보기

  - https://preasim.github.io/39

  - [https://velog.io/@da_na/Spring-Security-JWT-Spring-Security-Controller-Unit-Test하기](https://velog.io/@da_na/Spring-Security-JWT-Spring-Security-Controller-Unit-Test%ED%95%98%EA%B8%B0)


### Day 2 - 백엔드 배포하기

---
**테스트 완성**

- [ ]  백엔드 유닛 테스트 완성하기

**로직 작성**

- [ ]  백엔드 로직을 Spring Boot로
    - [ ]  회원가입 - /signup
        - [ ]  Request Message

           ```json
           {
               "username": "JIN HO",
               "password": "12341234",
               "nickname": "Mentos"
           }
           ```

        - [ ]  Response Message

           ```json
           {
               "username": "JIN HO",
               "nickname": "Mentos",
               "authorities": [
                       {
                               "authorityName": "ROLE_USER"
                       }
               ]		
           }
           ```

    - [ ]  로그인 - /sign
        - [ ]  Request Message

           ```json
           {
               "username": "JIN HO",
               "password": "12341234"
           }
           ```

        - [ ]  Response Message

           ```json
           {
               "token": "eKDIkdfjoakIdkfjpekdkcjdkoIOdjOKJDFOlLDKFJKL",
           }
           ```


**배포해보기**

- [ ]  AWS EC2 에 배포하기

**API 접근과 검증**

- [ ]  Swagger UI 로 접속 가능하게 하기

### Day 3 - 백엔드 개선하기

---
[Git 커밋 메시지 잘 쓰는 법 | GeekNews](https://news.hada.io/topic?id=9178&utm_source=slack&utm_medium=bot&utm_campaign=TQ595477U)

**AI-assisted programming**

- [ ]  AI 에게 코드리뷰 받아보기

**Refactoring**

- [ ]  피드백 받아서 코드 개선하기

**마무리**

- [ ]  AWS EC2 재배포하기
