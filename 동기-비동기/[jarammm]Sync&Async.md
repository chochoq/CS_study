# 동기와 비동기

<br/>

![image](https://user-images.githubusercontent.com/90924434/135394959-06c6a21f-fe95-41b7-bc36-e8e28cf5c1d4.png)

- 처리 과정

![image](https://user-images.githubusercontent.com/90924434/135394974-349d044e-9906-4c8c-b74e-cfe15b337ff0.png)

<br/>

## **Sync vs Async**

일반적으로 동기와 비동기의 차이는 메소드를 실행시킴과 `**동시에**` 반환 값이 기대되는 경우를 **동기** 라고 표현하고 그렇지 않은 경우에 대해서 **비동기** 라고 표현한다. 동시에라는 말은 실행되었을 때 값이 반환되기 전까지는 `**blocking**`되어 있다는 것을 의미한다. 비동기의 경우, `**blocking**`되지 않고 이벤트 큐에 넣거나 백그라운드 스레드에게 해당 task 를 위임하고 바로 다음 코드를 실행하기 때문에 기대되는 값이 바로 반환되지 않는다. 

### **비유를 통한 쉬운 설명**

비동기 방식 예제를 통해서 **블록과 논블록의 차이**를 간략하게 설명하자면, 학생이 시험지를 선생에게 건넨 후 **가만히 앉아 채점이 끝나서 시험지를 돌려받기만을 기다린다면** 학생은 **블록 상태**입니다. 하지만 학생이 시험지를 건넨 후 선생에게 채점이 완료되었다는 전송을 받기 전까지 다른 과목을 공부한다거나 게임을 한다거나 **다른 일을 하게 되면** 학생의 상태는 **논블록 상태**라고 합니다.

<br/><br/>

## 동기식 처리 (Synchronous)

![image](https://user-images.githubusercontent.com/90924434/135395666-c537f0aa-13c4-4d4b-98cc-aeeb3cba534e.png)


- 동기식 처리 모델(Synchronous processing model)은 **직렬적**으로 Task를 수행
- 즉, 작업 **순차적**으로 실행되며 어떤 작업이 수행 중이면 **다음 작업은 대기**하게 됨
<br/>

### 동기식으로 동작하는 자바 코드

```java
public class Synchro {
	public static void main(String[] args) {
		
		method1();
		method2();
		method3();
		
	}
	
	public static void method1() {
		System.out.println("method1");
	}
	public static void method2() {
		System.out.println("method2");
	}
	public static void method3() {
		System.out.println("method3");
	}
	
}
```

- 콘솔창 결과
    
    ```markdown
    method1
    method2
    method3
    ```
    

> 자바의 특성에 의해 위에서 아래로 순차적으로 코드가 실행되고 그 결과의 순서도 마찬가지. 몇 번을 다시 실행해도 결과는 동일!
> 

<br/><br/>

## 비동기식 처리 (Asynchronous)

![image](https://user-images.githubusercontent.com/90924434/135395705-c38d917b-ab18-4970-9f9e-745c526f6fd1.png)


**비동기식 처리 모델(Asynchronous processing model 또는 Non-Blocking processing model)**

- **병렬적으로 태스크를 수행**
- **즉, 태스크가 종료되지 않은 상태라 하더라도 대기하지 않고 다음 태스크를 실행한다.**


### 예시

**서버에서 데이터를 가져와서 화면에 표시하는 태스크를 수행할 때, 서버에 데이터를 요청한 이후 `서버로부터 데이터가 응답될 때까지 대기하지 않고(Non-Blocking) 즉시 다음 태스크를 수행`**

- **이후 서버로부터 데이터가 응답 → 이벤트가 발생**
- **이벤트 핸들러가 데이터를 가지고 수행할 태스크를 계속해 수행**

<br/>

### 비동기식으로 작동하는 자바의 멀티 스레드 코드

```java
public class Asynchro {
	public static void main(String[] args) {
	
	
		Thread t1 = new Thread(()->{
			method1();
		});
		Thread t2 = new Thread(()->{
			method2();
		});
		Thread t3 = new Thread(()->{
			method3();
		});
		
		
		t1.start();
		t2.start();
		t3.start();
		
	}
	
	public static void method1() {
		System.out.println("method1");
	}
	public static void method2() {
		System.out.println("method2");
	}
	public static void method3() {
		System.out.println("method3");
	}
}
```

- 콘솔창 결과
    
    ```markdown
    method1
    method3
    method2
    ```
    

> 호출한 순서대로 수행되지 않았다는 것을 알 수 있다. 이는 자바의 스레드 스케쥴러에 의해 제어된 결과로 그때그때 다른 결과를 보여준다. **따라서 작업의 처리 순서는 보장이 되지 않는 것을 알 수 있다!**
> 

<br/><br/>

## 동기 vs. 비동기

- **동기방식**
    - 장점 : 설계가 매우 간단하고 직관적
    - 단점 : 결과가 주어질 때까지 아무것도 못하고 대기해야 함
- **비동기방식**
    - 동기보다 복잡하고 결과가 주어지는데 시간이 걸림
    - 그러나 결과가 주어지기 전까지 다른 작업을 할 수 있으므로 자원을 효율적으로 사용할 수 있음

<br/><br/>

## Blocking ≠ Synchronous & Non-Blocking ≠ Asynchronous

![image](https://user-images.githubusercontent.com/90924434/135395749-50b0297b-3963-4fa2-a054-032b60558b0c.png)


### Blocking/Non-Blocking

> **호출되는 함수가 바로 리턴하느냐 마느냐가 관심사**
> 

→ 함수를 호출하고 응답을 받기까지 다른 일을 해도 되는지 안되는지

함수 A, B가 있고, A 안에서 B를 호출했다고 가정해보자. 이때 호출한 함수는 A고, 호출된 함수는 B가 된다. 현재 B가 호출되면서 B는 자신의 일을 진행해야 한다. (제어권이 B에게 주어진 상황)

- **Blocking** : 함수 B는 내 할 일을 다 마칠 때까지 제어권을 가지고 있는다. A는 B가 다 마칠 때까지 기다려야 한다.
- **Non-blocking** : 함수 B는 할 일을 마치지 않았어도 A에게 제어권을 바로 넘겨준다. A는 B를 기다리면서도 다른 일을 진행할 수 있다.

즉, 호출된 함수에서 일을 시작할 때 바로 **제어권을 리턴해주느냐, 할 일을 마치고 리턴해주느냐**에 따라 블럭과 논블럭으로 나누어진다고 볼 수 있다.

### **Synchronous/Asynchronous**

> **호출되는 함수의 작업 완료 여부를 누가 신경쓰냐가 관심사**
> 

→ 함수 호출 시 호출된 함수의 수행 상태 및 결과를 호출한 함수가 체크써야하는지 아닌지

아까처럼 함수 A와 B라고 똑같이 생각했을 때, B의 수행 결과나 종료 상태를 A가 신경쓰고 있는 유무의 차이라고 생각하면 된다.

- **Synchronous** : 함수 A는 함수 B가 일을 하는 중에 기다리면서, 현재 상태가 어떤지 계속 체크한다.
- **Asynchronous** : 함수 B의 수행 상태를 B 혼자 직접 신경쓰면서 처리한다. (`Callback`)
    
    ✅**비동기**는 호출시 Callback을 전달하여 작업의 완료 여부를 호출한 함수에게 답하게 된다. (Callback이 오기 전까지 호출한 함수는 신경쓰지 않고 다른 일을 할 수 있음)
    
<br/><br/>

### 예제

👉 [실제 예제](http://homoefficio.github.io/2017/02/19/Blocking-NonBlocking-Synchronous-Asynchronous/)

> 함수 A가 함수 B를 호출할 때
> 

**1) Blocking & Synchronous**

1. 함수 A는 함수 B가 작업을 마칠 때까지 기다림
2. 함수 B는 본인의 일만 할 뿐, 수행 상태를 신경쓰는 것은 함수 A
3. B가 작업을 마칠 때까지 다른 일을 할 수 없음

**2) Blocking & Asynchronous**

1. 함수 A는 함수 B가 작업을 마칠 때까지 기다리지 않음
2. 그러나 B가 작업을 마칠 때까지 다른 일을 할 수는 없음

**3) Non-blocking & Synchronous**

1. 함수 A는 함수 B가 작업을 마칠 때까지 기다림
2. 이때 함수 A는 callback함수를 통해 지속적으로 함수 B에 `상태를 물어봄`
3. (그저 기다리는 것 외의) 다른 일을 할 수 있다고는 하지만 그 다른 일이 바로 `2번`
4. callback함수에 대한 회신이 오기전까지 무언가를 하기에는 너무나 짧은 시간임

**4) Non-blocking & Asynchronous**

1. 함수 A는 함수B가 작업을 마칠 때까지 기다리지 않음
2. 그 동안 다른 일을 할 수 있음

<br/><br/>

## 정리

- **Blocking/NonBlocking은 호출되는 함수가 바로 리턴하느냐 마느냐가 관심사**
    - 바로 리턴하지 않으면 Blocking
    - 바로 리턴하면 NonBlocking
- **Synchronous/Asynchronous는 호출되는 함수의 작업 완료 여부를 누가 신경쓰냐가 관심사**
    - 호출되는 함수의 작업 완료를 호출한 함수가 신경쓰면 Synchronous
    - 호출되는 함수의 작업 완료를 호출된 함수가 신경쓰면 Asynchronous
- 성능과 자원의 효율적 사용 관점에서 가장 유리한 모델은 **`Async-NonBlocking`** 모델이다.

<br/><br/><br/>

---

**참고**

[Ready-For-Tech-Interview/동기와 비동기.md at master · WooVictory/Ready-For-Tech-Interview](https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Operating%20System/%EB%8F%99%EA%B8%B0%EC%99%80%20%EB%B9%84%EB%8F%99%EA%B8%B0.md)

[동기와 비동기의 개념과 차이](https://private.tistory.com/24)

[[Java]동기와 비동기 방식(Asynchronous processing model)](https://webheck.tistory.com/entry/Java%EB%8F%99%EA%B8%B0%EC%99%80-%EB%B9%84%EB%8F%99%EA%B8%B0-%EB%B0%A9%EC%8B%9DAsynchronous-processing-model)

[[Network] Blocking/Non-blocking & Synchronous/Asynchronous | 👨🏻‍💻 Tech Interview](https://gyoogle.dev/blog/computer-science/network/Blocking,Non-blocking%20&%20Synchronous,Asynchronous.html#blocking-non-blocking)

[Blocking-NonBlocking-Synchronous-Asynchronous](http://homoefficio.github.io/2017/02/19/Blocking-NonBlocking-Synchronous-Asynchronous/)
