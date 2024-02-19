Demo project to demonstrate issue with below version of spring boot resteasy
`<artifactId>resteasy-servlet-spring-boot-starter</artifactId> <version>6.1.0.Final</version>
`
with spring boot starter and few other SB dependencies such as data JPA, JDBC etc

`<groupId>org.springframework.boot</groupId> <artifactId>spring-boot-starter-parent</artifactId> <version>3.2.2</version>
`
**JDK 17 and Spring 6 ( which comes packaged with boot 3.x.x +)**

We are porting our project from legacy JBOSS to Spring boot and wanted to retain REST EASY aspects so thought of using this library.
Our projects starts up fine without reset-servlet-spring-boot-starter dependency or even with older version `(6.0.4.Final)` but with version `6.1.0 Final` we are getting the below error during boot. I have isolated and ran the project without resteasy dependency and it works fine.
Anything i am missing? Because this error related to JPA entity manager is not making sense?

To replicate the issue Run the `DemoApplication.java`

`
Caused by: java.lang.IllegalStateException: RESTEASY013015: could not find the type for bean named jpaSharedEM_entityManagerFactory at org.jboss.resteasy.plugins.spring.SpringBeanProcessor.getBeanClass(SpringBeanProcessor.java:481) at org.jboss.resteasy.plugins.spring.SpringBeanProcessor.processBean(SpringBeanProcessor.java:307) at org.jboss.resteasy.plugins.spring.SpringBeanProcessor.postProcessBeanFactory(SpringBeanProcessor.java:280) at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanFactoryPostProcessors(PostProcessorRegistrationDelegate.java:363) at org.springframework.context.support.PostProcessorRegistrationDelegate.invokeBeanFactoryPostProcessors(PostProcessorRegistrationDelegate.java:197) at org.springframework.context.support.AbstractApplicationContext.invokeBeanFactoryPostProcessors(AbstractApplicationContext.java:788) at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:606) at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) at org.springframework.boot.SpringApplication.run(SpringApplication.java:334) at org.springframework.boot.SpringApplication.run(SpringApplication.java:1354) at org.springframework.boot.SpringApplication.run(SpringApplication.java:1343)`