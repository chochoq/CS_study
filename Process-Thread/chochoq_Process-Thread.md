
![Untitled](https://persistent-fruit-85b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F263547de-fab5-4fc3-b8c3-5cb33d65ad5f%2FUntitled.png?table=block&id=52a8e70f-37e8-4cdf-b303-d76beb522914&spaceId=a07b9679-e55c-4b34-ad51-a4e7fac6c83a&width=1920&userId=&cache=v2)

# Process / Thread

# What is a Process?

- 운영체제로부터 시스템의 자원을 분할해서 할당하는 작업의 단위
- 메모리에 적재되고 CPU 자원을 할당받아 실행되고 있는 [컴퓨터 프로그램]()
(CPU 작업목록에서 확인이 가능하다)
- 하나 이상의 [쓰레드를]() 통해 실행된다.
(프로세스는 기본적으로 하나 이상의 쓰레드를 가지고있다.)
- 프로세스는 각각 독립된 메모리영역(Code, Data, Stack, Heap)을 할당받는다.

> 👌**Program**
작업을 수행하는 명령들의 집합 = 특정 작업을 위해 실행할 수 있는 파일 혹은 프로그램
> 

**동시성**

여러개의 작업을 한번에 하는 것. 컨텍스트 스위칭이 일어난다

**병렬성**

코어가 여러개 달려 동시에 작업을 분담하여 일을 하는 것

![Untitled](https://persistent-fruit-85b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8e26757b-1a1f-415e-acad-260b8cd2f4c3%2FUntitled.png?table=block&id=ea51d7fe-b561-4148-b09b-9ad2834f9a08&spaceId=a07b9679-e55c-4b34-ad51-a4e7fac6c83a&width=1920&userId=&cache=v2)

## Multi Process

- 하나의 프로그램 안에서 둘 이상의 프로세스를(실행흐름, 각각의 코드)구성해 하나의 작업을 처리한다.
(ex. game-2인이상의 게임인경우 2개의 입력)
- 부모 - 자식 프로세스간의 독립된 메모리 영역을 가지기 때문에 서로의 코드를 공유하지않는다.

![Untitled](https://persistent-fruit-85b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb781b529-f21f-4bfd-a271-546fb02abb6b%2FUntitled.png?table=block&id=dc640cf2-9e82-404a-8304-fb2017afa2ae&spaceId=a07b9679-e55c-4b34-ad51-a4e7fac6c83a&width=960&userId=&cache=v2)

## **장점**

- 서로의 코드를 공유하지 않아 안정성이 높다.

## **단점**

- 서로의 코드를 공유하기 위해(프로세스간의 통신) IPC이용한다. 
(IPC의 종류 → 메일슬롯, 파이프, 파일, 소켓 등)
- 이 때문에 자원의 낭비, 딜레이가 발생된다.
- 프로세스의 갯수가 여러개로 늘어나면 [컨텍스트 스위칭]()이 발생해 성능이 저하될 가능성이 있다.

> 👌**Context Switching(컨텍스트 스위칭, 문맥교환)**
CPU에서 여러 프로세스를 돌아가면서 작업을 처리하는 과정
CPU는 한가지 명령만 처리할 수 있기 때문에 프로세스를 번갈아가며 실행하고 관리한다.
>
>동작 중인 프로세스가 대기를 하면서 해당 프로세스의 상태(context)를 보관하고 대기하고 있다가 다시 실행시 복구하는 비용(시간)
> 
> 
> ![Untitled](https://persistent-fruit-85b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fed9f5388-eb6a-4d29-8d19-2c78bfdf18cd%2FUntitled.png?table=block&id=abfd3966-e69e-49e7-b3f9-4db56748a52c&spaceId=a07b9679-e55c-4b34-ad51-a4e7fac6c83a&width=1150&userId=&cache=v2)
> 

---

# Thread

- 프로세스 내에서 실행되는 흐름의 단위
- 하나의 프로세스 안에서도 여러개의 일이 진행된다. 프로세스를 공유하여 진행되는 작업의 갈래를 쓰레드라고 함.
(하나의 실행흐름(코드)는 공유하고, 스택을 별도로 가져가 자식프로세스를 생성하지 않고 쓰레드로 작업을 시켜줄 수 있다 - 메인 함수 코드를 공유하는 것은 아니다→ 스택을 제외한 다른 영역의 전역변수,함수들은 공유가된다)
- 즉 하나의 프로세스가 다수의 작업을 개별 스레드를 이용하여 동시에 수행할 수 있다.
- 쓰레드는 Stack만 별도고 나머지 영역은 공유한다.
- 같은 작업을 하는데, 쓰레스가 아닌 프로세스로 작업을 한다면 자원이 낭비된다.

![Untitled](https://persistent-fruit-85b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F8567013b-7022-483e-8289-33054dc30640%2FUntitled.png?table=block&id=1c1e2f2b-0ddd-4ad3-bb20-2f86cafde14a&spaceId=a07b9679-e55c-4b34-ad51-a4e7fac6c83a&width=770&userId=&cache=v2)

## Multi Thread

하나의 응용프로그램을 여러개의 스레드로 구성하고 각 쓰레드마다 하나의 작업을 처리하도록 하는 것

## **장점**

- 프로그램의 응답시간이 단축된다.
- 시스템의 자원 소모가 감소되어 자원의 효율적으로 관리할 수 있다.
- 쓰레드간의 데이터를 주고받는 것이 간단해져 시스템의 자원 소모가 줄어들게 된다.
- 쓰레드 사이의 작업량이 작아져 컨텍스트 스위칭이 빨라진다.
- 작업이 분리되어 코드가 간결하다

## **단점**

- 메모리 영역을 공유하기 때문에 디버깅 작업이 까다로울 수 있다.
- 각각의 쓰레드가 같은 시점에, 같은 작업을 하게될 때 문제가 생길 수 있어, 이를 방지하는 코드를 만들어야한다.(동기화 문제를 해결해야한다)

---

# 메모리 영역

하나의 프로세스는 각각 독립된 메모리 영역(Code, Data, Stack, Heap)을 할당받는다. 

![스크린샷 2021-09-25 오전 10.08.07.png](https://persistent-fruit-85b.notion.site/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F425443f7-7ef6-47ae-aef9-e9fd4339b770%2F%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-09-25_%E1%84%8B%E1%85%A9%E1%84%8C%E1%85%A5%E1%86%AB_10.08.07.png?table=block&id=4688d7f9-197e-45b2-a901-60a09f9cd252&spaceId=a07b9679-e55c-4b34-ad51-a4e7fac6c83a&width=970&userId=&cache=v2)

**코드(Code)**

코드 영역은 실행할 프로그램의 코드 및 매크로 상수가 기계어 형태로 저장되는 영역이다. CPU는 코드영역에 저장된 명령어를 하나씩 처리한다.
프로그램 명령을 수행한다.

**데이터(Data)**

데이터 영역은 코드에서 선언한 전역 변수와 정적(static) 변수가 저장되는 영역이다. 데이터 영역은 프로그램의 시작과 함께 할당되어 종료될 때 소멸된다.
초기화된 데이터를 저장한다.

**스택(Stack)**

스택 영역은 함수 안에서 선언된 지역변수, 매개변수, 리턴값, 등이 저장되고 함수 호출시 기록하고 종료되면 제거한다. 스택이라는 자료구조 명칭에서도 알 수 있듯이 후위선출(LIFO) 메커니즘을 따른다.

흔히 재귀함수를 통해 너무 많은 함수를 호출하게 되는 경우 스택 영역이 초과하면서 Stack Overflow(스택오버플로우)에러가 발생한다. (여러분이 잘 아는 그 [스택오버플로우](http://stackoverflow.com/)가 여기서 따온것이다)

임시 메모리 영역

**힙(Heap)**

힙 영역은 관리가 가능한 데이터 이외의 다른 형태의 데이터를 관리하기 위한 공간(Free Space)이다. 이 공간은 동적 메모리 할당 공간이므로 사용이 끝나면 운영체제가 쓸수 있도록 반납해야 한다. 프로그램이 실행하는 순간 프로그램이 사용할 메모리 크기를 고려하여 메모리의 할당이 이루어지는 데이터 또는 스택과 같은 정적 메모리 할당과는 대조적이다. 동적 메모리 할당은 어느 시점에 어느 정도의 공간을 할당할 수 있을지 정확히게 예측할 수 없으므로, 런타임에 확인가능하다.

동적 할당 시 에 사용한다( new(), mallock())

---

### 예상 면접질문

프로세스와 쓰레드의 차이(특징)

멀티 프로세스와 멀티 쓰레드

쓰레드 세이프

컨텍스트 스위칭

동기, 비동기

**Q. Thread Safe 란?**

Thread safe란 것은 여러 thread가 동시에 사용되어도 안전하단 것을 뜻한다.

특정 함수 A 와 변수 AA 가 여러 스레드에서 호출되어도 하나의 스레드에서 호출했을 때와 같은 결과가 보장되어야 한다는 의미

함수가 전역 변수를 참조하게 된다면 그 함수는 thread safe 하지 않은 결과가 나올 수 있다.

Thread Safe 하지 않은 조건을 만드는 방법의 예를 들어보라고 한다던가, Thread Safe 하지 않은 환경을 Thread Safe 하게 변경하는 방법등을 물어볼 수 있다.

프로세스와 다르게 쓰레드간에 자원을 공유하고 있고 있고 이 때 무엇을 조심해야 하는지를 묻는 질문이다.

[Process, Thread 차이가 뭐예요?](https://brunch.co.kr/@babosamo/100)

---

[11장. 프로세스 vs. 쓰레드(2)](https://youtu.be/ELl_DYmQpsc)

[Process와 Thread 이야기](https://charlezz.medium.com/process%EC%99%80-thread-%EC%9D%B4%EC%95%BC%EA%B8%B0-5b96d0d43e37)

[[OS]프로세스(Process)와 스레드(Thread)의 차이/멀티 프로세스와 멀티 스레드의 개념 ,특징, 장단점](https://devuna.tistory.com/21)

[process와 thread](https://velog.io/@ouo_yoonk/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%93%B0%EB%A0%88%EB%93%9C)