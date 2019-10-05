## List

- 순서를 보장
- 데이터 중복 허용
- ArrayList, Vector, LinkedList 가 존재
    - Vector 는 예전에 사용 현재는 잘 사용하지 않음
    - ArrayList 는 검색이 빈번할 때 사용하는 것이 유리
    - LinkedList 는 추가 / 삭제가 빈번할 때 사용하는 것이 유리

## Set

- 데이터 중복을 허용하지 않음
- HashSet, TreeSet, LinkedSet
    - HashSet 은 빠른 접근 속도를 갖는다.
    - TreeSet 은 정렬된 순서대로 보관하며 정렬 방법을 지정할 수 있다.
    - LinkedSet 은 추가된 순서, 또는 가장 최근에 접근한 순서대로 접근한다.

## Map

- Key 와 Value 의 쌍으로 이루어졌다.
- HashMap, HashTable, TreeMap, LinkedHashMap, ConcurrentHashMap
    - HashMap
        - 중복을 허용하지 않음
        - 순서를 보장하지 않음
        - key 와 value 로 null 을 허용

    - HashTable
        - HashMap 보다는 느리지만 동기화가 지원
        - key 와 value 로 null 이 허용되지 않음

    - TreeMap
        - 이진검색트리의 형태
        - 정렬된 순서로 저장, 빠른 검색이 가능
        - 저장 시 정렬(오름차순)을 하기 때문에 저장시간이 오래 걸림

    - LinkedHashMap
        - HashMap 을 상속받아 HashMap 과 매우 유사
        - Map 에 있는 엔트리들의 연결 리스트가 유지되므로 입력한 순서대로 반복 가능
         
    - ConcurrentHashMap
        - 동기화를 지원
        - key 와 value 로 null 이 허용되지 않음