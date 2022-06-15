# 비밀번호 암호화 (bcrypt, scrypt)



> [Naver D2 안전한 패스워드 저장](https://d2.naver.com/helloworld/318732) 을 정리한 글입니다. 근데이제 bcrypt와 scrypt를 중심으로 



### 단반향 해시함수 

패스워드를 보안을 신경써서 저장하고자 하는 경우 단방향 해시 함수를 사용해서 패스워드를 암호화하는 방법을 생각해 볼 수 있다. 

단방향 해시함수는 원본 데이터에서 해시값은 얻을 수 있지만 해시값으로는 원본 데이터를 얻지는 못한다. 



사용자가 패스워드를 저장할때 원본데이터가 아닌 해시값으로 저장하고 비밀번호를 맞춰볼때도 사용자가 입력한 값을 해시함수로 돌려서 나온 값 (다이제스트)과 디비에 저장된 해시값이 일치하는지 여부를 판단한다. 



하지만 이렇게 단방향 해시함수를 사용할 때 발생할 수 있는 문제점이 있다 



### 단방향 해시함수 문제점 

1. 인식가능성 
2. 속도 

#### 1. 인식가능성 

동일한 key에 동일한 해시값을 가지는 단방향 해시함수의 특징은 보안 취약점을 유발할 수 있다.

만약 해커가 임의의 입력값에 대한 해시값들을 모두 모은 사전을 가지고 있을때 보안은 뚫린다 



#### 2. 속도

해시값의 길이가 짧을수록 해시 함수 처리속도는 굉장히 빠르다 

찰나의 시간동안 해커는 임의의 값을 대입해보면서 보안을 뚫을 수 있다 



너무 빠른 해시함수 속도는 보안을 취약하게 한다 





### 단방향 해시함수 보완하기 

1. 솔팅(Salting)
2. 키 스트레칭 (Key Stretching)



#### 1. 솔팅 

해시값의 길이가 짧을수록 보안이 취약하다 

이를 해결하기 위해 해시값을 생성할때 소금을 뿌린다. 여기서 소금은 바이트 단위의 임의의 문자열이다. 

솔트는 32바이트 이상의 길이를 가진다.



![helloworld-318732-1](https://d2.naver.com/content/images/2015/06/helloworld-318732-1.png)

#### 2. 키 스트레칭

속도가 빠를수록 보안이 취약하다 

이를 해결하기 위해 원본 데이터의 해시값을 생성하고 생성된 해시값을 입력값으로 다시 해시값을 생성하는 과정을 반복한다. 이런 과정은 해커가 부르트 포스로 원본 데이터를 알아내려 할때 많은 시간이 소요되도록 하기 위한것이다. 



![helloworld-318732-2](https://d2.naver.com/content/images/2015/06/helloworld-318732-2.png)



### Key Derivation Functions



+ 해시값을 생성할때 <u>솔팅과 키 스트레칭을 반복</u>하면서 원본 데이터 외에도 입력값을 추가

+ 공격자가 쉽게 해시값을 유츄할 수 없도록 하고 <u>보안 강도 선택 가능</u> 

+ 병렬화를 어렵게하는 기능 제공 
  + 해커의 부르트포스 어텍을 어렵게 만든다 



#### PBKDF2

PBKDF2(Password-Based Key Derivation Function)



+ 해시함수의 컨테이너
+ 솔트 적용 후 함수의 <u>반복횟수를 임의로 선택</u> 가능 
+ 가볍고 구현하기 쉬움 
+ SHA함수같이 검증된 해시함수만 사용 



`DIGEST = PBKDF2(PRF, Password, Salt, c DLen)`

+ PRF: 난수 (eg. HMAC)
+ Password: 패스워드 (원데이터)
+ Salt: 솔트
+ DLen: 원하는 다이제스트 길이 



#### bcrypt

+ 패스워드 저장을 목적으로 설계됨 

+ 가장 강력한 해시 매커니즘 중 하나 
+ `work factor`
  + 다이제스트 처리 과정의 반복수 결정 
  + 이 변수로 보안성을 조절할 수 있다 
+ **제약**
  + 입력값으로 72 bytes character를 사용해야함 



```java
// Sample code for jBCrypt is a Java
// gensalt is work factor and the default is 10
String hashed = BCrypt.hashpw(password, BCrypt.gensalt(11));

// Check that an unencrypted password matches one that has
// previously been hashed
if (BCrypt.checkpw(candidate, hashed))  
    System.out.println("It matches");
else  
    System.out.println("It does not match");
```





#### scrypt

+ PBKDF2와 유사함 
+ 다이제스트 생성시 메모리 오버헤드를 갖게 함 
  + 부르트포스 어택 상황에서 병렬화 처리가 어렵도록 함 (메모리 오버헤드 때문에)




```
DIGEST = scrypt(Password, Salt, N, r, p, DLen)  
```

- Password: 패스워드
- Salt: 암호학 솔트
- N: CPU 비용
- r: 메모리 비용
- p: 병렬화(parallelization)
- DLen: 원하는 다이제스트 길이





---

## 정리 



MD5, SHA함수들과 같은 해시함수들은 메시지 인증과 [무결성](https://azurecourse.tistory.com/556) 체크를 위한 것

이런 해시 함수들을 패스워드 인증을 위해 사용하면 해시함수의 특징인 '인식가능성'과 '빠른 속도'때문에 보안상에 취약점이 생긴다 



이를 해결하기 위해서 패스워드 저장은 KDF를 사용하는 것이 좋다 











---

