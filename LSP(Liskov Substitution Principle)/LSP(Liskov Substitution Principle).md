# LSP(Liskov Substitution Principle)

### 개요

이번 장에서는 SOLID 중 세 번째 원칙인 Liskov Substitution Principle에 대해서 알아보겠습니다. 

---

### Liskov Substitution Principle

LSP는 간단한 원칙입니다. 작은 예제와 함께 설명하겠습니다.

```java
public class LSP {
		static P P = new P();

		static class T {
				public void doSomething(){
						System.out.println("T#doSomemthing called");
				}
		}

		static class S extends T { // (4) 그 경우 S는 T의 서브타입이다
				public void doSomething(){
						System.out.println("S#doSomemthing called");
				}
		}

		static class P {
				public void doSomething(T p){ // (3)T 타입을 사용하는 프로그램 P에서 원래 들어와야 하는 T대신 S가 들어와도 아무 변경이 필요없다면 
						System.out.println("T#doSomemthing called");
				}
		}

		public static void main(String[] args) {
				T p = new T();
				S c = new S();

				P.doSomething(p); // (1) T 타입의 객체 p
				P.doSomething(s); // (2) S 타입의 객체 c
		}
}
```

> *T 타입의 객체 p, S 타입의 객체 c가 있다. 이 때 T타입을 사용하는 모든 프로그램 p에서 c가 p를 대체해도 아무런 변경이 필요하지 않다면 그 경우 S는 T의 서브타입이다*
> 

위 내용은 리스코프 치환 원칙을 해석한 내용입니다. 조금 복잡하게 느껴질 수도 있는데 쉽게 얘기하면 아래와 같습니다.

1. *클래스 P의 doSomething()의 인자로 들어오는 p는 T 타입이다.* 
2. *이 때 p가 T 타입인지 S 타입인지 상관없이* 
3. *‘p는 T 타입이거나 T의 서브타입이다’ 하고 돌아가게 만들어야 한다는 것*

대부분의 사람들이 객체지향의 재사용을 거론하며 부모클래스에 메서드를 많이 넣어놓고 그걸 상속받은 뒤 자식 클래스에서 부모 클래스의 메서드를 호출하며 사용합니다. 그런데 이것은 다운캐스트를 유발합니다. 이 때문에 타입에 대한 의존성이 아주 강하게 생기죠. 타입에 대한 의존성은 아주 강한 의존성이기 때문에 이를 최대한 지양해야 합니다.

LSP를 지키기 위한 핵심은 **정확한 타입이 무엇인지 알아야하는 일이 없어야 한다**는 것입니다. 이를 위반하게 되면 다운캐스트, instanceof 등을 사용해서 정확한 타입 체크를 수행하는 안티 패턴이 나타나게 됩니다. 만약 LSP가 지켜지지 않게 되면 자식클래스가 추가될 때마다 클라이언트가 수정되는 현상이 발생합니다. 정확한 서브클래스에 타입에 맞춰 로직이 수정되어야 하기 때문이죠. 만약 다운캐스트, instanceof, 자식클래스에 부모클래스의 호출이 보인다면 상속 관계를 끊고 합성 관계로 옮길 수 있는지 확인해보는 습관을 들이면 좋습니다.

---

### *Ref*

- [https://www.youtube.com/watch?v=OfVwuWJSHOY&list=PL7pUrjEGbG8ZMPQ-XukPJsFyMeyvtGcnV&index=17](https://www.youtube.com/watch?v=OfVwuWJSHOY&list=PL7pUrjEGbG8ZMPQ-XukPJsFyMeyvtGcnV&index=17)