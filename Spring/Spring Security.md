## 정의

---

애플리케이션의 보안(인증과 권한, 인가 등)을 담당하는 스프링 하위 프레임워크. '인증'과 '권한'에 대한 부분을 Filter 흐름에 따라 처리함. 보안과 관련해서 체계적으로 많은 옵션을 제공해주기 때문에 개발자 입장에서는 일일이 보안관련 로직을 작성하지 않아도 된다는 점에서 장점.

## Usage
처음 서버를 실행하면 아래와 같은 인증이 필요한 페이지가 뜸. security가 낚아 챔.

![image](https://user-images.githubusercontent.com/82012938/143729749-b4b89f4a-28e1-40b5-818e-7692ebe44b9a.png)


`user/콘솔창에 뜨는 키`로 로그인하면 접근이 가능함.

`SpringConfig`를 통해 접근 권한에 따른 url 설정 가능.

`@enableWebSecurity` 어노테이션 사용

`redirect`는 함수 재사용이 가능하며 모델의 데이터를 가져올 수 있음.
