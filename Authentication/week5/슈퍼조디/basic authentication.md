# Basic authentication



> HTTP 기본인증



1. 불특정 다수가 접근하는 웹 사이트 특성상 권한 없는 사용자가 리소스에 접근할 수 없어야 한다. 
2. 서버는 리소스를 요청하는 사용자가 누구인지 식별할 수 있어야 한다. 식별 후 접근 권한을 부여해야 한다.
3. HTTP는 자체적으로 엑세스 제어와 인증을 위한 프레임워크를 제공한다. 
   + 가장 일반적인 인증방식은 Basic 인증방식



### HTTP Basic 인증

HTTP 인증 프레임워크는 서버가 클라이언트의 요청을 시도해보고  클라이언트가 인증 정보를 제공할때 사용된다. 

Client의 요청과 Server의 응답 과정은 다음과 같이 작동한다. 

![img](https://mdn.mozillademos.org/files/14689/HTTPAuth.png)



#### 동작 과정

1. Client는 Server에게 리소스를 요청함
2. Client가 요청한 리소스를 이용하기 위해서는 인증이 필요하다. 따라서 Server는 Client에게 **WWW-Authenticate Header**를 통해 인증 필요성을 Client에게 전달한다. Basic 문자열을 통해 Basic 인증 과정이 필요하다는걸 Client에게 알린다. 
3. 인증 요청을 받은 Client는 ID:Password 문자열을 Base64로 Encoding한 String을 Authorize Header에 추가한 뒤 다시 한번 Server에 리소스 요청
   + Authorization: Basic 뒤의 문자열들이 <u> ID:Password 문자열을 Base64로 Encoding한 String</u>
4. Encoding된 ID:Password 문자열을 받은 Server는 자신이 Encoding한 값과 일치하는지 확인한 후 일치하면, 사용자의 요청을 처리한 후 전달한다. 



#### 특징

+ Client가 ID,Password를 알고있고 HTTP를 이용해서 단순한 인증이 필요할때 사용된다. 
+ Base64로 인코딩된 값은 쉽게 디코딩될 수 있어 보안에 매우 취약하다 
+ *악의가 없는 누군가가 의도치 않게* 리소스에 접근하는 것을 막는데 사용하거나 SSL이나 TLS등 암호 기술과 혼용한다.  







> 참고 자료
>
> + https://ssup2.github.io/theory_analysis/HTTP_Basic_%EC%9D%B8%EC%A6%9D/
> + http://iloveulhj.github.io/posts/http/http-basic-auth.html



