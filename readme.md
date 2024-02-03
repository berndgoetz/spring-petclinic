This is a fork of https://github.com/spring-projects/spring-petclinic.git to show a Thymeleaf issue in Spring 
Boot 3 running in Open Liberty.

Run

```
mvn clean liberty:run
```

and start the application in your browser using http://localhost:9080/

This will trigger the following stack trace:

````
Exception thrown by application class 'org.springframework.web.servlet.FrameworkServlet.processRequest:1022'
jakarta.servlet.ServletException: Request processing failed: java.lang.IllegalArgumentException: Cannot build an application for a request which servlet context does not match with the application that it is being built for.
at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1022)
at org.springframework.web.servlet.FrameworkServlet.doGet(FrameworkServlet.java:903)
at jakarta.servlet.http.HttpServlet.service(HttpServlet.java:527)
at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:885)
at jakarta.servlet.http.HttpServlet.service(HttpServlet.java:614)
at com.ibm.ws.webcontainer.servlet.ServletWrapper.service(ServletWrapper.java:1260)
at [internal classes]
at org.apache.tomcat.websocket.server.WsFilter.doFilter(WsFilter.java:51)
at com.ibm.ws.webcontainer.filter.FilterInstanceWrapper.doFilter(FilterInstanceWrapper.java:203)
at [internal classes]
at org.springframework.web.filter.RequestContextFilter.doFilterInternal(RequestContextFilter.java:100)
at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116)
at com.ibm.ws.webcontainer.filter.FilterInstanceWrapper.doFilter(FilterInstanceWrapper.java:203)
at [internal classes]
at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:101)
at com.ibm.ws.webcontainer.filter.FilterInstanceWrapper.doFilter(FilterInstanceWrapper.java:203)
at [internal classes]
at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:101)
at com.ibm.ws.webcontainer.filter.FilterInstanceWrapper.doFilter(FilterInstanceWrapper.java:203)
at [internal classes]
at org.springframework.boot.web.servlet.support.ErrorPageFilter.forwardToErrorPage(ErrorPageFilter.java:189)
at org.springframework.boot.web.servlet.support.ErrorPageFilter.handleException(ErrorPageFilter.java:174)
at org.springframework.boot.web.servlet.support.ErrorPageFilter.doFilter(ErrorPageFilter.java:141)
at org.springframework.boot.web.servlet.support.ErrorPageFilter$1.doFilterInternal(ErrorPageFilter.java:99)
at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116)
at org.springframework.boot.web.servlet.support.ErrorPageFilter.doFilter(ErrorPageFilter.java:117)
at com.ibm.ws.webcontainer.filter.FilterInstanceWrapper.doFilter(FilterInstanceWrapper.java:203)
at [internal classes]
at org.springframework.web.filter.CharacterEncodingFilter.doFilterInternal(CharacterEncodingFilter.java:201)
at org.springframework.web.filter.OncePerRequestFilter.doFilter(OncePerRequestFilter.java:116)
at com.ibm.ws.webcontainer.filter.FilterInstanceWrapper.doFilter(FilterInstanceWrapper.java:203)
at [internal classes]
Caused by: java.lang.IllegalArgumentException: Cannot build an application for a request which servlet context does not match with the application that it is being built for.
at org.thymeleaf.util.Validate.isTrue(Validate.java:79)
at org.thymeleaf.web.servlet.JakartaServletWebApplication.buildExchange(JakartaServletWebApplication.java:64)
at org.thymeleaf.spring6.view.ThymeleafView.renderFragment(ThymeleafView.java:204)
at org.thymeleaf.spring6.view.ThymeleafView.render(ThymeleafView.java:192)
at org.springframework.web.servlet.DispatcherServlet.render(DispatcherServlet.java:1431)
at org.springframework.web.servlet.DispatcherServlet.processDispatchResult(DispatcherServlet.java:1167)
at org.springframework.web.servlet.DispatcherServlet.doDispatch(DispatcherServlet.java:1106)
at org.springframework.web.servlet.DispatcherServlet.doService(DispatcherServlet.java:979)
at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1014)
... 31 more
````

Reported in https://github.com/thymeleaf/thymeleaf/issues/990.
