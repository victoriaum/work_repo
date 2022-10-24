# JSP

## 1강. 웹과 자바
<hr>

### 웹 관련 기본 용어
+ 웹 : 인터넷 기반의 정보 공유 서비스, 정보 공유 공간
+ 하이퍼텍스트 : 웹 상의 문서로, 텍스트 및 멀티미디어 포함
+ W3C : 국제 웹 표준화 기구
+ 동적 웹문서 -> 작성기술 JSP 
+ 정적 웹문서

### 웹 에플리케이션 실행과 구성요소
+ 웹 서비스의 제공과 구성요소
  + 웹 클라이언트 
  + 웹 서버(Apache, IIS, Nginx)
  + 웹 애플리케이션 서버(웹 컨테이너) WAS -> 실행환경 
  + 데이터베이스
+ 클라이언트 측 실행 : 애플릿, JS, 플래시
+ 서버 측 실행 : 서블릿, JSP, ASP, PHP, CGI(Common Gate Interface) 방식 
+ 컴파일 방식 / 비컴파일 방식

### JSP와 웹 컨테이너
+ 웹 서버에서 서블리시 실행되기 위한 환경
  + 웹 서버 / JDK /  서블릿 컨테이너(Tomcat)
+ JSP 컨테이너
  + JSP 페이지를 서블릿 프로그램으로 변환, 대부분의 서블릿 컨테이너가 JSP 컨테이너 기능을 포함하고 있다.

### HTTP 프로토콜
+ 웹 서버와 클라이언트가 통신하는 규약
+ Connection oriented & Stateless 특성
  + 요청을 위해 접속하고 응답 후 서버는 상태를 유지하지 않으므로 쿠키나 세션으로 상태관리 필요
+ HTTP 요청 메시지 구조
  + 시작라인 -> 요청방식, URI, 버전번호 ex) GET/index.html HTTP/1.1
  + 요청헤더 + 공백라인 + 요청몸체(POST에서만 의미)
+ [HTTP 상태 코드](https://developer.mozilla.org/ko/docs/Web/HTTP/Status)

### 정리하기
+ 웹은 인터넷 상에 분산된 전 세계적 정보 공간 또는 정보 공유 서비스를 의미한다.
+ 웹 클라이언트가 요청하는 웹 문서는 정적인 웹 문서와 동적인 웹 문서로 구분된다.
+ 웹 애플리케이션은 실행 위치에 따라 서버 측/클라이언트 측 기술로 나뉘고, 구현 방식에 따라 컴파일/비컴파일 방식으로 구분된다.
+ JSP는 동적으로 웹 문서를 만들기 위한 서버 측 웹 프로그래밍 기술이다.
+ 웹 애플리케이션 서버(WAS)는 동적으로 웹 페이지를 생성하기 위해 웹 애플리케이션을 실행하고 관리한다.
+ HTTP는 응용 계층의 프로토콜로서 웹 문서의 송수신을 위한 통신 규약이다.

### 연습문제 정리
+ JDBC는 자바 언어로 데이터베이스 프로그래밍을 하기 위한 Java API 규격이다.
+ JSP 페이지에 대한 클라이언트의 요청을 처리하기 위한 것이 웹 컨테이너이다.
+ POST
  + 원하는 방식으로 인코딩 된 데이터를 요청 메시지의 몸체에 포함하여 전송하면서 파일을 요청하고자 하는 경우 사용된다.
<br><br>



## 2강. 개발 환경 설정하기
<hr>

### JDK 설치, Tomcat 설치, 웹 프로젝트 만들기

### 정리하기
+ JSP 페이지는 서블릿 프로그램으로 번역되어 실행되므로 JDK를 설치해야 한다.
+ 서블릿 프로그램이나 JSP 페이지를 실행시키기 위해 톰캣과 같은 웹 컨테이너를 설치해야 한다.
+ 통합 개발환경인 이클립스를 이용하면 편리하게 JSP 프로그램을 작성, 컴파일 및 디버깅 작업 등을 할 수 있다.
+ 실제 웹 서비스를 제공하려면 배포 작업을 통해 웹 컨테이너에 웹 프로젝트를 등록해야 한다.
+ 배포용 WAR 파일은 JSP 페이지, 서블릿, Java 클래스, HTML 파일 등을 묶은 압축 파일이다.

### 연습문제 정리
+ war 파일의 배포는 \[톰캣설치폴더\]\webapps에 배포
<br><br>




## 3강. JSP 개요
<hr>

### JSP 기술
+ 서버측 스크립트 언어
+ 표현언어 EL을 사용한 확장 메커니증
+ JSTL과 같은 태그 라이브러리의 사용
+ 템플릿 데이터 - 정적 데이터로 HTML이나 XML 형식의 텍스트

### JSP 문서의 구성
+ JSP 페이지의 구성요소
  + 스크립트 요소
    + 스크립트릿 ```<% %>``` 
    + 표현식 ```<%= %>``` 
    + 선언 ```<%! %>```
  + 지시어 ```<%@ 지시어이름 속성1="값1" %>```
    + ex) ```<%@ include file="/jsp/userInfo.jsp" %> //정적 include ``` 
    + ex) ```<%@ taglib uri="/mycustomtags" prefix="mycust" %>```
  + 액션태그 ```<jsp:액션이름 속성="값" />```
    + ex) ```<jsp:include page="3-3.jsp" /> //동적 include ```
  + 내장객체
    + request, response, session, application, out,page 등
  + 표현언어 ```${expr}```
    + 표현언어의 내장객체나 JSTL과 함께 사용할 수 있음
  + JSTL과 사용자 정의 태그
    + JSTL : 유용한 사용자 정의 태그들을 모아 표준화한 태그 모음
  + 주석 ```<%-- --%>```

### page 지시어
+ autoFlush, contentType, import, language, session, buffer, info, errorPage, isErrorPage, pageEncoding, isELIgnored, trimDirectiveWhitespaces
+ contentType ```<@ page contentType="text/html;" charset="UTF-8" %>```
  + 응답문서의 형식과 charset을 설정
+ trimDirectiveWhitespaces ```<@ page trimDirectiveWhitespaces="true" %>```
  + 앞 부분 지시어로 인해 생기는 불필요한 공백 문자를 제거

### 스크립트 요소
+ 스크립트릿, 표현식, 선언
+ 스크립트릿 : JSP 페이지에 삽입되는 Java 코드 조각 ```<% %>```

### 정리하기
+ JSP 페이지를 작성할 때 JSP 태그와 HTML 태그를 함께 쓸 수 있다.
+ 스크립트 요소는 자바 코드인 스크립트릿, 수식의 값을 출력하기 위한 표현식, 메서드나 변수 선언에 사용되는 선언으로 나뉜다.
+ 지시어에 의한 JSP 페이지의 설정은 변역 과정에서 사용된다.
+ 내장 객체는 자주 사용되는 기능을 미리 객체로 구현해 놓은 것이다.
+ 액션 태그는 XML 태그와 같은 형식이며 특별한 기능을 제공한다.

### 연습문제 정리
+ 표현식 ```<%= %>``` / 선언 ```<%! %>```
+ errorPage는 실행 중 에러가 발생했을 때 포워딩될 페이지를 지정한다. 현재 페이지의 에러 페이지 여부를 지정하는 것은 isErrorPage이다.
+ 표현식 : 스크립트릿을 사용하지 않고 변수나 수식의 값을 출력하고자 할 때 사용되는 JSP 요소
<br><br>





## 4장. JSP 동작 원리
<hr>

### JSP 처리과정
+ JSP 페이지 요청하면 웹 서버에서 ```.java```로 변환 후 ```.class```를 생성

### 출력 버퍼와 응답
+ 출력 버퍼는 응답 결과의 임시 저장소, 응답을 만들 때 출력 버퍼에 기록하고 클라이언트에 전달
+ page 지시어의 ```autoFlush``` 속성이 ```true```라면, 버퍼를 비우고 전달(flush)
  + ```false```인 경우 예외가 발생 -> 500 에러

### 서블릿 프로그래밍
+ 자동으로 만들어지는 서블릿 클래스는 ```생성자, doGet(), doPost()```를 가지고 있음
+ 실제 서블릿을 실행하면 생성자, init(), service(), doGet(), doPost() 순으로 실행됨.
  + 실행 URL : ```http://localhost:8080/JSP/HelloServlet```
  ```html
  <form action="HelloServlet" method="get"></form>
  <form action="HelloServlet" method="post"></form>
  
  response.setContextType("text/html;charset="UTF-8");
  request.setCharacterEncoding("UTF-8");
  ```
  
### 정리하기
+ JSP 페이지에 대한 요청이 들어오면, JSP 페이지는 서블릿 프로그램으로 변환되고 컴파일되어 실행된 후, 그 결과가 클라이언트에 응답으로 전송한다.
+ 응답 결과를 즉시 전송하지 않고 임시로 출력 버퍼에 저장할 수 있다. 실행이 끝나거나 버퍼가 차면 클라이언트로 결과를 전송하여야 한다.
+ page 지시어를 통해 JSP 컨테이너에게 페이지의 속성과 실행 옵션을 알려줄 수 있다.
+ GET 방식 요청인가 POST 방식 요청인가에 따라 서블릿 클래스의 doGet( ) 또는 doPost( ) 메서드가 실행되어 요청이 처리된다.

### 연습문제 정리
+ 서블릿 프로그램은 추상 클래스 HttpServlet을 상속받는 클래스를 작성한다.
+ ```service() 메소드```는 HTTP 요청 방식이 무엇이냐에 따라 적당한 메소드를 호출해 주는 기능을 하며 HttpServlet에 이미 정의되어 있다. ```재정의할 필요가 없다.```
<br><br>





## 5장. 요청과 응답
<hr>

+ [Java EE API](https://docs.oracle.com/javaee/7/api/)

### request 내장 객체
+ HttpServletRequest 유형
+ 클라이언트의 요청 관련 정보를 얻을 수 있다.

### response 내장 객체
+ HttpServletResponse 유형
+ 클라이언트에 응답을 제공하기 위해 구현한 객체
+ ```response.sendRedirect(String location)```
  + 웹 서버가 웹 브라우저에게 다른 페이지로 이동하라고 지시하는 것
  + 요청에 대한 임시 응답이 가고, 브라우저가 재차 URL을 요청하게 됨.
  + ```<jsp:forward>```와 차이가 있음.

### 정리하기
+ request 내장 객체는 클라이언트와 서버의 정보, 클라이언트가 전달하는 데이터, 요청 헤더와 쿠키 등의 읽기 기능을 제공한다.
+ GET은 요청 URL에 전송할 파라미터를 붙여서 전송하는 방식이고, POST 방식은 요청 몸체에 파라미터를 넣어 전송한다.
+ 클라이언트로부터 전송된 파라미터가 하나의 값을 가질 때는 request.getParameter() 메서드를 사용하여 읽고, 여러 값을 가질 수 있다면 getParameterValues() 메서드를 사용하여야 한다.
+ 톰캣에서 POST 방식으로 전달된 파라미터를 읽기 전에 request.setCharacterEncoding(charset) 메서드를 이용하여 디코딩할 때 사용할 charset을 지정해야 한다.
+ response 객체를 이용하여 다른 페이지로 이동, 상태 코드 설정, 응답 헤더 설정, 쿠키 추가 등을 할 수 있으며 응답 몸체를 만들기 위한 출력 스트림을 얻을 수 있다.

### 연습문제 정리
+ 응답을 만들 때 사용되는 객체는 response 객체이다.
<br><br>





## 6장. 내장 객체와 Scope
<hr>

### 내장 객체
+ 객체의 종류
  + 사용자 정의 객체
    + ```<jsp:useBean>``` 이나 스크립트릿을 통해 선언한 객체
  + JSP 내장 객체
    + request, response, pageContext, session, application, out, config, page, exception

### page 내장 객체
+ 페이지별로 page 영역을 관리하는 객체

### application 내장 객체
+ 특정 웹 애플리케이션에 포함된 모든 JSP 페이지는 하나의 application 객체를 공유함.
+ web.xml에 저장된 설정 정보의 조회
  ```xml
  <web-app>
    <context-param>
        <description>파라미터 설명</description>    
        <param-name>파라미터 이름</param-name>    
        <param-value>파라미터 값</param-value>    
    </context-param>
  </web-app>
  ```

### application 내장 객체
+ 특정 웹 애플리케이션에 포함된 모든 JSP 페이지는 하나의 application 객체를 공유함.
+ web.xml에 저장된 설정 정보의 조회

### out 내장객체
+ print(인자)는 인자를 꼭 필요로 한다. println()은 없어도 됨.
+ 버퍼 관련 메서드
  + clear(), clearBuffer()
    + 버퍼가 비워져 있어도 clearBuffer()는 IOException을 발생시키지 않는다.
  + flush()
    + 버퍼의 내용을 비워 출력시킴

### 내장 객체와 영역
+ JSP 객체들은 scope 속성을 가짐 -> 영역 표시 속성은 ```page, request, session, application```이 존재 (크기순)
1. page 영역: 1개의 JSP 페이지 내부, 내장 객체: ```pageContext```
2. request 영역: 같은 요청을 처리하는 페이지들로 이루어짐, ```<jsp:forword>``` 또는 ```<jsp:include>```를 사용할 때, 내장 객체: ```request```
3. session 영역: 일련의 요청을 처리하는 페이지들로 이루어짐, 세션은 하나의 웹브라우저에서 유지됨, 내장 객체: ```session```
4. application 영역: 1개의 웹 애플리케이션 전체 영역, 웹 컨테이너를 다시 시작하면 기존 영역이 없어진 후 다시 만들어짐, 내장 객체: ```application```

### 속성을 이용한 데이터 공유
+ 데이터 공유 방법
  + 새로운 속성을 정의하여 사용
    + 속성은 <이름, 값> 형태 
    + ```setAttribute(String name, String Value)```
    + ```getAttribute(String name)```
    + ```removeAttribute(String name)```

### 정리하기
+ 내장 객체는 JSP 컨테이너가 자동으로 만들어 제공하므로 자유롭게 사용할 수 있다.
+ pageContext 객체는 하나의 JSP 페이지와 1:1로 대응되는 객체로서 JSP 페이지에서 사용되는 내장 객체를 리턴하는 메서드를 제공한다.
+ application 객체는 웹 애플리케이션의 정보를 저장하고 관리하는 객체로서 특정 웹 애플리케이션에 포함된 모든 JSP 페이지는 하나의 application 객체를 공유한다.
+ 웹 애플리케이션 폴더의 WEB-INF 폴더에 있는 web.xml 파일은 웹 애플리케이션의 설정 파일로서 초기화 파라미터, 서블릿과 서블릿 매핑 등의 설정 정보를 포함한다.
+ JSP 페이지에서 브라우저로 보낼 결과의 출력을 위해 out.print( )나 out.println( )을 사용한다.
+ request 영역은 한 번의 요청을 처리하기 위한 JSP 페이지들, session 영역은 세션이 생성되어 브라우저가 종료될 때 까지 사용되는 JSP 페이지들, application 영역은 웹 애플리케이션에 포함된 모든 JSP 페이지들로 구성된다.

### 연습문제 정리
+ application 내장 객체는 ServletContext 유형의 객체
<br><br>




## 7장. 모듈화된 JSP 페이지 만들기
<hr>

### 
+


### 정리하기
+ 

### 연습문제 정리
+ 
<br><br>