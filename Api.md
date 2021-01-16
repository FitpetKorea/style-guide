# HTTP API 작성 가이드

- FQDN: `api.fitpetmall.co.kr`, `api.fitpet.co.kr` 

- 보안 프로토콜(TLS)을 사용해야 한다.

- HTTP 1.1 이상을 지원해야 한다.

- REST 혹은 GraphQL 기반으로 작성되어야 한다.

- [OpenAPI](https://swagger.io/specification/) 형식의 스펙문서를 제공해야 한다.

- 통합테스트를 구축하고 자동화해야 한다.
 
- Path Segments를 표현할 때에는 [kebab-case](https://en.wikipedia.org/wiki/Letter_case#Special_case_styles) 를 사용할 것
  - 예) ```/dog-foods/brands/{brand_id}```
   
- Query Parameters에는 snake_case 를 사용할 것
 
- Trailing Slashes 를 사용하지 말 것
  - slash 를 사용한 경우와 사용하지 않은 경우 같은 결과를 반환해야 하고, / 를 붙이지 않는 것을 원칙으로 한다.

- API의 버전 관리를 위해 Path Segment에 `/v1`, `/v2` 따위를 포함하지 말 것
  - 다양한 버전을 관리하는 것은 테스트 및 유지보수 측면에서 매우 복잡하고 어려운 일이다.
  - 가장 좋은 것은 [API 버전을 관리하지 않는 것](https://martinfowler.com/articles/enterpriseREST.html#versioning)이며, 아래의 방법들 중 하나를 우선적으로 고려한다.
    1. 기존 리소스의 호환을 유지하며 확장
       - 기존 필드 삭제 금지
       - 신규 필드 추가만 가능
    2. 새로운 리소스를 정의
    3. 새로운 서비스 엔드포인트를 정의

- Level 2 이상의 REST Maturity Model을 구현할 것
   - https://martinfowler.com/articles/richardsonMaturityModel.html#level2

- 요청과 응답에 사용되는 Payload는 JSON 형식을 따를 것
   - MIME 형식으로는 ```application/json```을 사용할 것
   - 프로퍼티 이름에는 snake_case 를 사용할 것
    
- 날짜와 시간 표기는 ISO 8601 표준을 따를 것


## HTTP 상태 코드
다양한 response code를 사용하면 그 자체로 명시적이지만 코드 관리가 어려워진다는 단점이 있다.
따라서 아래 명시된 보편적인 response code만을 사용하고 더 자세한 내용은 message-body에서 제공한다.

| 상태 코드                     | 의미                      | 용도                                       |
| ------------------------- | ----------------------- | ---------------------------------------- |
| 200 OK                    | 성공적으로 처리                | 에러 응답에 대해서 사용하지 않도록 한다                   |
| 201 Created               | 리소스 생성 완료               | 가능하면 응답 헤더 Location필드에 리소스를 접근할 수 있는 URI를 포함시킨다. |
| 204 No Content            | 내용없음                    | 요청 처리 성공 후 특별히 message body에 포함시킬 내용이 없는 경우 사용한다. |
| 301 Moved Permanently     | 요청한 리소스가 새로운 URI를 부여받았음 | 새 URI를 응답 헤더 Location필드에 명시한다.           |
| 302 Found                 | URI가 임시로 변경됨            | 301과 비슷하지만 일시적으로 옮겨진 경우에만 사용한다.          |
| 304 Not Modified          | 요청한 리소스가 변경되지 않음        | If-Modified-Since 요청 헤더에 대한 응답으로 활용될 수 있다. |
| 400 Bad Request           | 잘못된 요청                  | 정의되지 않은 형식이나 보내면 안되는 요청에 대한 응답.          |
| 401 Unauthorized          | 리소스 접근 권한이 없음           | 가능하면 응답에 인증에 관한 정보를 포함시켜 필요한 경우 클라이언트에서 추가 요청을 보낼 수 있도록 한다. |
| 403 Forbidden             | 숨겨진 리소스에 접근하려 함         | 필요하다면 거부된 이유를 응답에 포함시키고,아예 공개할 의사가 없다면 404: Not Found를 사용한다. |
| 404 Not Found             | 매칭되는 URI가 없음            | 실제 리소스가 존재하더라도 존재 여부를 노출시키지 않고 싶은 경우에 사용할 수 있다. |
| 429 Too Many Requests     | 너무 많은 요청                | 가능하면 얼마나 기다린 후에 새로운 요청을 받을 수 있는지 응답 헤더의 Retry-After필드에 명시한다. |
| 500 Internal Server Error | 서버 에러                   | 요청은 정상적으로 받았지만 서버 처리 중 문제가 발생할 경우 전반에 사용한다. |
| 502 Bad Gateway           | 게이트웨이 에러                | 서버가 게이트웨이나 프록시로 사용 중인 경우 upstream서버에 이상이 있을 때 사용한다. |
| 503 Service Unavailable   | 서비스 이용 불가               | 대기 시간을 알 수 있다면 응답 헤더의 Retry-After필드에 명시한다. |



### 참고

- [OAuth 2.0](https://oauth.net/2/)
- [Choosing an HTTP Status Code — Stop Making It Hard](http://racksburg.com/choosing-an-http-status-code/)
- [API Error Handling](http://nordicapis.com/best-practices-api-error-handling/)
- [그런 REST API로 괜찮은가](http://tv.naver.com/v/2292653)
