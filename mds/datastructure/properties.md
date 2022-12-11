## Properties
- 키와 값을 String 타입으로 제한한 Map 컬렉션
- 주로 Properties는 프로퍼티(*.properties) 파일을 읽어 들일 때 주로 사용
    - 프로퍼티(*.properties)파일
        - 옵션정보, 데이터베이스 연결정보, 국제화(다국어)정보를 기록하여 텍스트 파일로 활용
        - 애플리케이션에서 주로 변경이 잦은 문자열을 저장하여 관리하기 때문에
          유지보수를 편리하게 만들어 줌
        - 키와 값이 ‘=’기호로 연결되어 있는 텍스트 파일로 ISO 8859-1 문자셋으로 저장되고,
          한글은 유니코드(Unicode)로 변환되어 저장

## Properties 객체에 저장 및 가져오기
- getProperty(String key) : Properties 인스턴스에 해당 key 값에 해당하는 value 값 리턴
- setProperty(String key, String value) : Properties 객체에 해당 key 값과 value 값이 세트로 저장

## 파일 입출력
- store(OutputStream out, String comments) : 바이트 스트림으로 저장된 정보를 파일에 출력 저장
- store(Writer writer, String comments) : 문자 스트림으로 저장된 정보를 출력 저장
- storeToXML(OutputStream os, String comment) : 저장된 정보를 바이트 스트링으로 xml 로 출력 저장
- load(InputStream InStream) : 바이티 스트림으로 저장된 파일의 내용을 읽어와서 Properties 인스턴스에 저장
- load(Reader reader) : 문자 스트림으로 저장된 파일의 내용을 읽어와서 Properties 인스턴스에 저장
- loadFromXML(InputStream In) : 바이트 스트림으로 저장된 xml 파일의 내용을 읽어와서 Properties 인스턴스에 저장