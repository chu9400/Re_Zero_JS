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
### 움직이는 UI
- 속성  
scale - 크기를 변형함   
skew - 기울어짐을 변형함   
rotate - 회전을 줌   
translate - 위치를 이동함   
perspective - 3D효과를 위한 원근감을 부여함 (부모요소에 적용시킴)   
matrix - perspective를 제외한 모든 요소들을 한번에 일괄 적용시킴      

- 문법   
transform: translate (50px 50px);   
transform: translateX (100px);   
transform: translateY (-100px);   
transform: translateZ (-100px);   


---

### 함수 소수점 다루기
- (555 * 1.1).toFixed();   
소수점들을 생략해줌   

- 문자 '숫자'를 숫자로 바꾸기   
let num = (555 * 1.1).toFixed();
parseFloat(num);   
parseint(num);   
toFixed는 문자로 반환하는데 이걸 다시 숫자로 반환하기.

---

### Scroll 속성
 - 스크롤 위치 : scrollTop;
 - 스크롤 가능한 높이 : scrollHeight;
 - 화면에 보이는 높이 : clientHeight;

 - if (scrollTop + scrollHeight == clientHeight -10)   
  코드 활용 예) 먄약 스크롤바(약관) 다 내리면 이후 코드.    
  디바이스 마다 clientHeight가 달라서 clientHeight - 10 정도 해줘야함.

- Scroll 속성은 1초에 60번이라서 컴퓨터에 부담, 방지 방법있음.   
- Scroll 속성은  body 태그 끝나기 전에 넣기.   


---   

### 반응형 가로 스크롤 bar 코드
    <style>
        .line {
            border-bottom: 5px solid black;
            width: 0%;
            position: fixed;
            transition: all 0.1s; 
        }
    </style>
    <!-- 스크롤 주려고 2000px -->
    <div style="height: 2000px;">
        <div class="line"></div>
    </div>
    <script>
         window.addEventListener('scroll', function() {
            let scrollTop = document.querySelector('html').scrollTop;
            let scrollHeight = document.querySelector('html').scrollHeight - document.querySelector('html').clientHeight;
            let result = document.querySelector(".line").style.width = (scrollTop / scrollHeight) * 100;
            document.querySelector(".line").style.width = result + '%';
        });
    </script> 

---   

### 반복문

* ### for   
<pre><code>
for(let i = 0; i < item.length; i++>){
  console.log("test");
}    
</code></pre>
   
   
* ### forEach   
<pre><code>
var pants = [28, 30, 32];   
pants.forEach(function(a, i){   
  console.log(a,i)   
});  
</code></pre>   
- forEach 콜백함수 안에 파라미터 2개 입력 가능   
- 첫 파라미터는 반복문 돌 때 마다 array 안에 있던 하나하나의 데이터가 되고   
둘 째 파라미터는 반복문 돌 때 마다 0부터 1씩 증가하는 정수가 됨.   
   


* ### for in   
<pre><code>
var obj = { name : 'kim', age : 20 }   
for (var key in obj){   
  console.log(key);   
  console.log(obj[key]);   
}   
</code></pre>   
 for in 반복문 쓰면 object 자료 안에 있는 key와 value를 다 출력해볼 수도 있습니다.   

지금 key라고 작명하는 부분은 반복문이 돌 때 마다 object자료 안에 있던 key값이 됩니다.   
   


* ### arrow function 문법  
<pre><code> 
var pants = [28, 30, 32];   
pants.forEach(function(a){   
  console.log(a)   
});   
   
pants.forEach((a) => {   
  console.log(a)   
});   
</code></pre>   
혹은   
let 함수 = function(){ console.log('안녕') }   
let 함수 = () => { console.log('안녕') }   
   
이렇게 쓰기도 함.

#### 주의사항   
함수 안에서 this를 써야할 경우   

- 그냥 함수는 함수 안에서 this를 알맞게 재정의해줍니다.
- arrow function은 함수 안에서 this를 재정의해주지 않고 바깥에 있던 this를 그대로 씁니다.
그래서 이벤트리스너 콜백함수안에서 this를 써야하면 arrow function 쓰면 의도와 다르게 동작할 수도 있습니다.
그런데선 쓰지마십시오

---
