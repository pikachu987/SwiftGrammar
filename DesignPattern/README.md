## 디자인 패턴 (DesignPattern)

### 설계 5대 원칙 SOLID

#### 단일 책임 원칙 (Single Responsibility Principle: SRP)
- 클래스는 단 한개의 책임을 가져야 한다.
- 클래스가 여러 책임을 맡게 되면 그 클래스는 각 책임마다 변경되는 이유가 발생한다.

#### 개방-폐쇄 원칙 (Open-Closed Principle: OCP)
- 기능을 변경하거나 확장할수 있어야 한다. (상속)
- 그 기능을 사용하는 코드는 수정하지 않는다.

#### 리스코프 치환 원칙 (Liskov Substitution Principle: LSP)
- 파생된 타입은 반드시 그들의 기본 타입으로 교체되어야 한다.
- 자식클래스가 부모클래스로 업캐스팅을 했을때 아무런 문제가 없어야 한다.
- 부모 클래스에 자식클래스들이 상속을 받을때 어색해지는 메서드, 변수가 없어야한다.

#### 인터페이스 분리 원칙 (Interface Segregation Principle: ISP)
- 인터페이스는 인터페이스를 사용하는 클라이언트 기준으로 분리해야한다.
- 클라이언트가 사용하지 않는 인터페이스 때문에 클라이언트가 영향을 받아서는 안된다.
- 하나의 일반 인터페이스보다는 여러개의 구체적인 인터페이스가 좋다.

#### 의존 역전 원칙 (Dependency inversion Principle: DIP)
- 고수준 모듈(상위 클래스)은 저수준 모듈(하위 클래스)의 구현에 의존해서는 안된다.


### 패턴

#### - [데코레이트패턴(DecoratorPattern)](./DecoratorPattern.md "DecoratorPattern")
- 어떤 객체의 원래 특성을 바꾸지 않고 동적으로 어떤 책임, 역활을 덧붙이는 패턴
- Component: 추상 클래스(프로토콜)로 데코레이터로 감싸져 사용될 수 있음
- ConcreateComponent: 인터페이스를 동적으로 추가함
- Decorator: Component 객체를 가지며 자신이 장식할 구성 요소와 같은 추상 클래스를 구현
- ConcreateDecorator: Decorator가 감싸고 있는 Component 객체를 위한 변수가 있어 Component 상태를 확장
- 다른 객체에 영향을 주지 않고 개별적인 객체에게 동적으로 책임을 추가할 때
- 클래스의 정의가 감추어져 있거나 그 클래스의 서브클래스를 만들수 없을 때
- 어떤 클래스의 행동을 하려면 많은 수의 서브클래스가 필요할 때 사용
