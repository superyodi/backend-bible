# JWT

- 개념: 토큰기반 인증 중 가장 대표적인 방법. JSON 포맷으로 사용자에 대한 속성을 저장하는 웹 토큰
- 종류:
  1. Access Token: 정보들에 접근할 수 있는 권한부여에 사용
  2. Refresh Token: Access Token 이 만료되면 Refresh Token 으로 재발급클라이언트가 처음 인증을 받게 될 때(로그인 시), access, refresh token 두가지를 다 받지만, 실제로 권한을 얻는 데 사용하는 토큰은 access token 이다. Access token의 유효기간이 만료된다면 refresh token을 사용하여 새로운 access token을 발급받습니다. 이때, 유저는 다시 로그인할 필요가 없다.

![jwt의 구조](https://velog.velcdn.com/images%2Fdevjade%2Fpost%2F8e32efec-42e0-4418-83f4-d2325683cd54%2Fimage.png)

1. header : Header는 이것이 어떤 종류의 토큰인지(지금의 경우엔 JWT), 어떤 알고리즘으로 sign(암호화) 할지가 적혀있다.

```
{
"type" : "JWT",
"alg": "HS256"
}
```

이 JSON 객체를 base64 방식으로 인코딩하면 JWT의 첫 번째 부분이 완성된다.

2. payload: Payload에는 정보가 담겨 있습니다. 어떤 정보에 접근 가능한지에 대한 권한을 담을 수도 있고, 사용자의 유저 이름 등 필요한 데이터는 이곳에 담아 암호화 시킨다. 물론 암호화(헤더에서 정의한)가 될 정보지만, 민감한 정보는 되도록 담지 않는 것이 좋다.

```
{
  "sub": "someInformation",
  "name": "phillip",
  "iat": 151623391
}
```

첫번째 부분과 마찬가지로, 위 JSON 객체를 base64로 인코딩하면 JWT의 두 번째 블록이 완성된다.

3. signature: base64로 인코딩된 첫번째, 그리고 두번째 부분이 완성 되었다면(--> 이는 누구나 쉽게 decoding 할 수 있음), 원하는 비밀 키(암호화에 추가할 salt)를 사용하여 암호화한다.
4.  JWT의 최종 형태 : header + "." + payload + "." + signature