# MAP

- 키(key)와 값(value)로 구성되어 있으며, 키와 값은 모두 인스턴스
- 키는 중복 저장을 허용하지 않고(Set 방식), 값은 중복 저장 가능(List 방식)
- 키는 중복되는 경우, 기존에 있는 키에 해당하는 값을 덮어 씀
- Collection 인터페이스와는 다른 저장 방식을 가진다.
- key 란 value 를 찾기 위한 이름 역할을 하는 객체를 의미한다.
    - 요소의 저장 순서는 유지하지 않는다.
    - 키는 중복을 허용하지 않지만, 키가 다르면 중복되는 값은 저장 가능하다.
- 구현 클래스 : **HashMap**, HashTable, LinkedHashMap, Properties, TreeMap
    - HashMap 이 가장 많이 사용되며 HashTable 은 JDK 1.0부터 제공되었지만
    - HashMap 과 동일하게 동작한다. 다만 하위 호환을 위해 남겨놓았기 때문에 가급적 HashMap 을 이용하게 된다.

## 주요 메소드
### 인스턴스 추가
- put(K key, V value) : 주어진 키와 값을 추가, 저장이 되면 값을 리턴
### 인스턴스 검색
- containsKey(Object key) : 주어진 키가 있는지 확인하여 결과 리턴
- containsValue(Object Value) : 주어진 값이 있는지 확인하여 결과 리턴
- entrySet() : 키와 값의 쌍으로 구성된 모든 Map, Entry 인스턴스를 set 에 담아서 리턴
- get(Object key) : 주어진 키의 값을 리턴
- isEmpty() : 컬렉션이 비어있는지 여부
- keySet() : 모든 키를 Set 인스턴스에 담아서 리턴
- size() : 저장된 키의 총 수를 리턴
- values() : 저장된 모든 값에 Collection 에 담아서 리턴
### 인스턴스 삭제
- clear() : 모든 Map, Entry 를 삭제함
- remove(Object key) : 주어진 키와 일치하는 Map, Entry 삭제, 삭제가 되면 값을 리턴한다.

## HashMap

- Map 중에서 가장 많이 사용되는 클래스
- JDK 1.2부터 제공되는 클래스로 해시 알고리즘을 사용하여 검색 속도가 매우 빠르다.