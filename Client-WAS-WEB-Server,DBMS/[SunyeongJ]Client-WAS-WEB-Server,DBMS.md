### Server

서버란? 컴퓨터, 하드웨어

서비스를 제공해주는 컴퓨터 = 서버

서비스를 제공받는 컴퓨터 = 클라이언트

### Web Server

서버 역할을 하도록 해 주는 소프트웨어를 ~~~서버라고 일컫는데 웹 개발자(백엔드 개발자)가 서버를 개발하기 위해 사용하는 소프트웨어, 웹사이트를 제공해 주는 서버를 웹 서버라고 한다.

웹 서버는 웹사이트를 구성하는 HTML, CSS, Javascript와 같은 소스코드, 이미지, 기타 파일 등에 외부에서 지정된 주소를 통해 접근 가능하게 만들어 주는 역할을 한다.

대표적으로 Apache, NginX, IIS가 있다.

- **Apache** 안정성⬆️

    제일 대중적인 웹 서버. 아파치는 다중 프로세스로 일을 처리하는데 이를 Multi Process Module(MPM) 방식이라고 부른다. MPM 방식은 많은 자원을 요구한다.

    - mpm_prefork : 사용자마다 새로운 프로세스를 생성하는 것
    - mpm_worker : 한 프로세스에서 사용자마다 새로운 스레드를 생성하는 것
- **NginX** 성능, 가벼움⬆️

    요즘 Apache와 비슷하게 이용되는 추세. 엔진엑스는 이벤트로 일을 처리하는데(event driven 방식) MPM 방식보다 자원이 덜 필요하다.

### Web Server의 기능

- **Proxy**

    클라이언트에게 중복되는 요청을 받을 때마다 서버까지 가져가서 요청을 처리하려면 자원 낭비, 속도 저하 등의 문제가 생길 수 있다. 이 때문에 프록시를 중간에 두고 중복되는 요청은 프록시 서버에서 처리한다.

    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bd942f9c-acf4-452c-923d-aac580d22ee9/Untitled.png)

    - **Forward proxy**

        서버에 접근하는 사용자들의 아이피 주소를 숨길 수 있도록 포워드 프록시를 통하여 데이터를 주고받게 한다.

        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ac6087bf-ccab-4f32-b587-14924eb45823/Untitled.png)

    - **Reverse proxy**

        웹 서버의 역할 중 하나, 서버에 접근하는 사용자들에게 서버를 숨겨 내부 구조 등 보안상 중요한 것들을 보이지 않게 해 준다.

        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/996d30df-3cf1-4391-82c6-76af78cf85b0/Untitled.png)

- **Load balancing**

    여러 개의 웹 서버를 앞에서 묶어주어 트래픽을 분산 처리 해 주는 것으로 서버의 과부하를 방지하기 위해 사용되는 기술이다.

- **Caching**

    사용자가 웹사이트에 방문할 때 불러왔던 데이터(HTML, JS, 이미지 등)들의 복사본을 저장함으로써 매번 방문할 때마다 웹 서버에서 불러오지 않아도 되어 처리 속도를 더 빠르게 만들어 주는 기술이다.

### Web Application Server(WAS)

단순히 만들어진 웹사이트를 제공해주는 것뿐만 아니라 프로그래밍 된 것을 처리해주어 주로 동적 웹을 서비스할 때 사용한다.

WAS만으로도 웹사이트를 서비스할 수 있지만, 보통 웹 서버를 기본적으로 앞에 두고 뒤에 WAS를 두는 방식을 쓴다. (웹 서버의 보안 기능때문에)

자바 언어에서는 대표적으로 Tomcat이 있고 다른 언어에서는 WAS가 아닌 각자 다른 용어로 부른다.

- **Tomcat**

    자바와 JSP로 만든 웹 또는 API를 실행할 때 사용하는 것, 보통 스프링을 통해 개발할 때 사용한다.

    이 외에도 자바에 쓰이는 것으로는 Jetty, Undertow 등도 있다.

- **Node.js**

    Java가 JVM 환경 안에서 런타임이 구동되듯이 Node.js는 브라우저에 종속적인 자바스크립트를 외부에서 실행할 수 있는 런타임 환경을 제공해 준다. 런타임이지만 WAS 역할까지 해 준다.

- .**Net**

    닷넷도 JVM과 같은 가상 런타임 환경이다. (ASP, C#, C++ 관련 지식 필요)

- 참고 자료

    [아파치, NginX, 톰캣이 뭔가요? (+ 웹서버, WAS, 로드밸런싱, 프록시)](https://youtu.be/Zimhvf2B7Es)

    [[웹 서버] Proxy 서버와 Forward, Reverse 프록시](https://jcdgods.tistory.com/322)
