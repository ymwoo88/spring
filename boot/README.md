스프링부트 프로젝트의 경우 임베디드 톰캣 설정이 가능하여 아파치톰캣을 설정 안해도
java -jar exmple.war 형태로 서비스를 가동 시킬 수 있다.

이때! 중요한 부분은 main class not found가 될 수 있는데 그것은 main자바에 SpringBootServletInitializer 상속 및 configure메소드가 구현이 
안되어있을 때이다.
임베디드톰캣으로 배포를 원할 경우 아래와 같은 설정이 필수라는 것을 알고 프로젝트에 진행해보자!!

@SpringBootApplication
public class Application extends SpringBootServletInitializer {

    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
        return application.sources(Application.class);
    }
}

[참고사이트]
https://docs.spring.io/spring-boot/docs/1.5.10.RELEASE/reference/html/howto-traditional-deployment.html#howto-create-a-deployable-war-file
