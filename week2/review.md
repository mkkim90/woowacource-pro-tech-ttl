# 학습목표

## 경험해야할 학습 목표
	- TDD 기반으로 프로그래밍하는 경험
	- 메소드 분리 + 클래스를 분리하는 리팩토링 경험
	- 점진적으로 리팩토링하는 경험
	
## 경험할 객체지향 생활 체조 원칙
	- 규칙1 : 한 메서드에 오직 한 단계의 들여쓰기만 한다.
	- 규칙2 : else 예약어를 쓰지 않는다.
	- 규칙3 : 모든 원시값과 문자열을 포장한다.
	- 규칙5 : 줄여쓰지 않는다(축약금지)
	- 규칙8 : 일급 콜렉션을 쓴다.


# Clean Code 가이드

## 의미 있는 이름
	- 의도를 분명히 밝혀라
	- 그릇된 정보를 피하라 
	- 의미 있게 구분하라
	- 인터페이스와 구현 클래스 의도를 드러낼 수 있는 이름을 짓는 것을 추천
	- 클래스 이름 (명사나 명사구가 적합)
		- Customer, WikiPage, Account, AddressParser (적합)
		- Manager, Processor, Data, Info (안티)
	- 메소드 이름 (동사나 동사구가 적합)
		- postPayment, deletePage, save (적합)
		
	- 개념 하나에 단어 하나를 사용하라
		- 추상적인 개념 하나에 단어 하나를 선택해 이를 고수한다.
	
	
## 경계

	- 외부코드 사용하기 
		
		- Sensors를 추가함으로써 필요한 인터페이스 하나만 노출하는 것도 가능
		- 또 하나의 장점은 Sensors 내부의 자료구조가 Map이 아닌 다른 자료구조로 변경 되더라도 외부에 변경이 발생하지 않음
		- 경계 인터페이스인 Map을 Sensord 라는 클래스 안으로 숨긴다.
		
```
Map<Integer, Sensor> sensors = new HashMap<>();
Sensor s = sensors.get(sensorId);
```

```
public class Sensors {
	Map<String, Sensor> sensors = new HashMap<>();

	public Sensor getById(String id) {
		return sensors.get(id);
	}
}
```
		
```
public class Sensors {
	List<Sensor> sensors = new ArrayList<>();

	public Sensor getById(String id) {
		return sensors.get(id);
	}
}
```
