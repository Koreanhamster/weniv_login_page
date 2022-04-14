# weniv_login_page

**URL https://koreanhamster.github.io/weniv_login_page/**    
     **미리보기**

![Screen Shot 2022-04-14 at 8 23 12 PM](https://user-images.githubusercontent.com/95600994/163381824-7948b980-fe4d-4b8c-a10a-5e34db3efd39.png)

## 구현시 신경 쓴 점


### 웹 접근성

- 두번 째 로그인 페이지 - 보여지는 순서대로 마크업을 하면 스크린리더 상에서 아이디 입력으로 넘어가기 전에 닫기버튼이 나오기 때문에, 닫기버튼을 마크업 맨 마지막으로 배치하고 CSS를 통해 상단에 위치하게 함

### 소스 절약

- 각 회사 아이콘에 이미지 스프라이트 기법 사용 - 1장의 이미지만 사용함으로서 소스 및 로딩시간 절약



## 부딪혔던 문제점

### 약간의 삽질

![Screen Shot 2022-04-14 at 8 29 37 PM](https://user-images.githubusercontent.com/95600994/163382578-d5a8b8ef-0d36-4f8a-8b10-86ee8ddaa393.png)    

- 회원가입과 아이디/비밀번호찾기 사이에 있는 저 수직라인을 만들고 싶었다. 가상요소를 생성하여 라인을 만들어주려고 했는데, width값과 height값이 조절이 안되서 한 30분을 헤메었다.    

### 해결방법

- 가상요소는 기본적으로 인라인요소기 때문에 컨텐츠의 크기를 조절하고 싶을 땐 꼭 display: inline-block으로 바꿔줘야 한다.


```
.sign-in::after {
  content: "";
  margin: 0 12px;
  display: inline-block;
  width: 1px;
  height: 14px;
  border-right: 1px solid #767676;
  vertical-align: -2px;
}

```
      
![Screen Shot 2022-04-14 at 8 31 30 PM](https://user-images.githubusercontent.com/95600994/163382637-33a51161-5706-4bf0-a5b8-ec2e7f5cd23a.png)      

---
### 두 번 째 삽질  

```
        <ul>
          <li>
            <a class="google-login" href="https://www.google.com/"
              >구글 계정으로 로그인</a
            >
          </li>
          <li>
            <a class="facebook-login" href="https://www.facebook.com/"
              >페이스북 계정으로 로그인</a
            >
          </li>
          <li>
            <a class="naver-login" href="https://www.naver.com/"
              >네이버 계정으로 로그인</a
            >
          </li>
          <li>
            <a class="kakao-login" href="https://www.kakaocorp.com/page/"
              >카카오 계정으로 로그인</a
            >
          </li>
        </ul>
```

```
ul .facebook-login {
  border-color: #2f80ed;
}
```

![Screen Shot 2022-04-14 at 8 39 30 PM](https://user-images.githubusercontent.com/95600994/163383567-4cf466ca-faab-4461-9d91-88dffc35490f.png)     
색깔이 바뀌지 않는다.

### 해결방법

```
ul li .facebook-login {
  border-color: #2f80ed;
}
```
```
ul a[class^="facebook"] {
  border-color: #2f80ed;
}
```

위 두 방식으로 선택자를 지정해 주었다.

        
![Screen Shot 2022-04-14 at 8 39 41 PM](https://user-images.githubusercontent.com/95600994/163383751-13a6606d-a513-4537-83af-817099ec7dd6.png)

## What I learned...

이 과제는 멋쟁이사자처럼 지원시 입과테스트 중 하나였고 다시한 번 만드는거였기에 더 잘 해보고 싶었다.

그때는 어떻게 했나 싶을 정도로.. 

구현을 처음부터 설계하면서, 이걸 어떻게 할지 스스로 생각하는 내 자신이 놀라웠다.(많이 성장했네!)

웹 접근성을 고려한다던가, 이미지 소스 절약을 위해 스프라이트 기법을 사용한다던가, 저 체크박스에 체크를 하면 파란색으로 바뀌도록 만드는 걸(보이는 것 처럼 그냥 뿅 하고 되는게 아니다.) 이제 할 수 있게 되었다던가.



아직 복잡한 선택자를 선택한다던가 부모에게 주고 싶은 속성을 자식에게 줘서 왜 안되는거냐.. 머리 쥐어뜯는   시간을 허비하는 일이 있다. 특히 선택자 선택은 확실하게 잡아놓아야겠다.



만들면서 정말 많이 배운다.


