### 멱등성 (idempotent)
- 연산을 여러 번 하더라도 결과가 항상 동일한 성질

### HTTP 메서드의 안정성과 멱등성
- 멱등성 : 동일한 요청을 여러 번 보내도 응답 내용과 서버의 상태가 동일하게 남음
	- GET, HEAD, OPTIONS, PUT, DELETE, TRACE
		- POST, PATCH, CONNECT는 멱등하지 않다.
	- 어떤 이유로 커넥션이 끊어졌을 경우, 클라이언트가 같은 요청을 다시 보내도 되는지에 대한 판단 근거가 됨.
- 안정성 : 리소스를 변경하지 않음
	- GET, HEAD, OPTIONS
	- 안정성이 보장된 메서드는 멱등성도 보장
	- PUT, DELETE는 멱등하지만 리소스를 변경하여 안정성을 보장하지 않음

### PUT과 PATCH
- 둘 모두 자원을 수정하는 메서드이지만 PUT은 멱등하고 PATCH는 멱등하지 않다.
- PUT : 전체 자원을 덮어씀
- PATCH : 일부 속성만 갱신

### 멱등성을 보장하는 방법
- IETF의 표준으로, 클라이언트 측에서 HTTP 헤더에 Idempotency-Key로 멱등키 삽입
