## 정적페이지(static pages)와 동적페이지(Dynamic Pages) 

Static Pages
Web Server는 파일 경로 이름을 받아 경로와 일치하는 file contents를 반환한다.
항상 동일한 페이지를 반환한다.
Ex) image, html, css, javascript 파일과 같이 컴퓨터에 저장되어 있는 파일들
Dynamic Pages
인자의 내용에 맞게 동적인 contents를 반환한다.
즉, 웹 서버에 의해서 실행되는 프로그램을 통해서 만들어진 결과물 * Servlet: WAS 위에서 돌아가는 Java Program
개발자는 Servlet에 doGet()을 구현한다.
https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html





동적 페이지 : 사용자가 요청하면 이미 만들어진 페이지를 보여주는 것이 아닌 요청이 들어오면 데이터를 만들어서 보내줌

[동적인 페이지(서버페이지)의 필요성]: https://www.youtube.com/watch?v=0UEX6j5IJgY

- servlet은 동적인 문서, 서버에 의해서 만들어지 서버문서

정적 페이지: 이미 만들어놓은 페이지 (html 문서)



html로 먼저 문서를 만든다. 



# 웹서버(Web Server)

- 인터넷이 동작하기 위해서는 컴퓨터는 최소 2대가 있어야 한다. 
  - 웹브라우저 -------인터넷--------웹 서버 
  - (클라이언트)                              (서버)
  - (request)                                 (response)

- 클라이언트가 서버에 페이지 요청을 하면 요청을 받아 **정적** 컨텐츠(.html, .png, .css등)를 제공하는 서버



클라이언트에서 요청이 올 때 **가장 앞에서** 요청에 대한 처리를 한다.

클라이언트의 요청을 기다리고 요청에 대한 데이터를 만들어서 응답하는 역할 (정적 데이터)

CASE

정적 컨텐츠를 요청(request)했나?

\1. 정적 컨텐츠구나! 내가 제공해줄게 => .html, .png 등 응답(response)

\2. 정적 컨텐츠가 아니구나.. 웹서버에서 간단히 처리 못하겠군. WAS에게 처리를 부탁해야겠다! => 결국 WAS가 처리해준 컨텐츠를 받은 웹서버는 응답(response)을 해줌

대표 : Apache, nginx

출처: https://jeong-pro.tistory.com/84 [기본기를 쌓는 정아마추어 코딩블로그]





# WAS (Web Application Server)

**- WAS (Web Application Server)**

**동적** 컨텐츠를 제공하기 위해 만들어진 애플리케이션 서버 (DB조회, 로직처리가 요구되는 컨텐츠)

JSP,Servlet 구동 환경 제공

컨테이너, 웹컨테이너, 서블릿 컨테이너라고도 부름

\* JSP, servlet을 실행시킬 수 있는 소프트웨어 = 컨테이너

동작 프로세스

\1. 웹서버로부터 요청이 오면 컨테이너가 받아서 처리

\2. 컨테이너는 web.xml을 참조하여 해당 서블릿에 대한 쓰레드 생성하고 httpServletRequest와 httpServletResponse 객체를 생성하여 전달한다.

\3. 컨테이너는 서블릿을 호출한다.

\4. 호출된 서블릿의 작업을 담당하게 된 쓰레드(2번에서 만든 쓰레드)는 doPost()또는 doGet()을 호출한다.

\5. 호출된 doPost(), doGet() 메소드는 생성된 동적 페이지를 Response객체에 담아 컨테이너에 전달한다.

\6. 컨테이너는 전달받은 Response객체를 HTTPResponse형태로 바꿔 웹서버에 전달하고 생성되었던 쓰레드를 종료하고 httpServletRequest, httpServletResponse 객체를 소멸시킨다.

대표 : Tomcat, Jeus, JBoss



출처: https://jeong-pro.tistory.com/84 [기본기를 쌓는 정아마추어 코딩블로그]

