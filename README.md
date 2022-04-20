# 코딩애플 JS 강의
## Level 1 
### 6강 서브메뉴 만들어보기와 classList 다루기

#### 부트스트랩 
- cdn   
link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet"   
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js"></script>   
---
   
   
#### 탈부착 class 

- class명을 원하는 요소에 추가하는 법은   
&nbsp;&nbsp; 셀렉터로찾은요소.classList.add('클래스명') 이렇게 쓰면 됩니다.

- class명을 원하는 요소에서 제거하는 법은   
&nbsp;&nbsp; 셀렉터로찾은요소.classList.remove('클래스명') 이렇게 쓰면 됩니다.

- toggle
document.getElementsByClassName('list-group')[0].classList.toggle('show');   
toggle 한번누르면 추가 두번누르면 삭제   
![img_001](https://github.com/chu9400/Re_Zero_JS/blob/master/img/img_001.png "img_001")

---

#### querySelector

![img_002](https://github.com/chu9400/Re_Zero_JS/blob/master/img/img_002.png "img_002")


---

#### input, change 이벤트

- input에 키보드 입력마다 이벤트 발생   
document.getElementById('email').addEventListener('input', function(){
  console.log('안녕')
});


- input에 포커스를 잃어야 이벤트 발생   
document.getElementById('email').addEventListener('change', function(){
  console.log('안녕')
});

---