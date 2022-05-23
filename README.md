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


### 1. forEach   
<pre><code>
  var pants = [28, 30, 32];   
  pants.forEach(function(a, i){   
    console.log(a,i)   
  });  
</code></pre>   
- forEach 콜백함수 안에 파라미터 2개 입력 가능   
- 첫 파라미터는 반복문 돌 때 마다 array 안에 있던 하나하나의 데이터가 되고   
둘 째 파라미터는 반복문 돌 때 마다 0부터 1씩 증가하는 정수가 됨.   
   


### 2. for in   
<pre><code>
  var obj = { name : 'kim', age : 20 }   
  for (var key in obj){   
    console.log(key);   
    console.log(obj[key]);   
  }   
</code></pre>   
 for in 반복문 쓰면 object 자료 안에 있는 key와 value를 다 출력해볼 수도 있습니다.   
지금 key라고 작명하는 부분은 반복문이 돌 때 마다 object자료 안에 있던 key값이 됩니다.   
   


### 3. arrow function 문법  
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

### 정렬   

#### sort / filter / map   
   
##### sort
 - 원본이 변형됨.
 - 배열 정리해줌.   

<pre><code>
  var 어레이 = [7,3,5,2,40];
  어레이.sort(function(a, b){
    return a - b
  });

  console.log(어레이);
</code></pre>   

1. a, b는 array 안의 자료들입니다.

2. return 오른쪽이 양수면 a를 오른쪽으로 정렬해줍니다.

3. return 오른쪽이 음수면 b를 오른쪽으로 정렬해줍니다.

4. 그리고 array 안의 자료들을 계속 뽑아서 a, b에 넣어줍니다. 

이렇게 동작해서 a - b 저렇게 쓰면 숫자순 정렬이 되는 것입니다. 
예를 들면 a, b가 7과 3일 경우 7 - 3 하면 4가 남습니다.

4는 양수죠? 그러면 7을 3보다 오른쪽으로 보내줍니다.

그래서 숫자 오름차순 (123순) 정렬이 완성되는 것입니다.



#### 문자 역순 정렬   
<pre><code>
  var arr = ['a','c','b'];
  arr.sort((a,b) => {
    if (a < b) {
      return 1;
    } else if (a > b) {
      return -1;
    }
  });
  console.log(arr);
</code></pre>   
   
#### filter      
 - 원본 변형이 되지 않음.
 - 내가 원하는 값만 나오게 해줌
 - 변수에 저장해야 됨   

<pre><code>
  var 어레이 = [7,3,5,2,40];

  var 새어레이 = 어레이.filter(function(a){
    return a < 4
  });
  console.log(새어레이);
</code></pre>   

- 예를 들어 여러 숫자가 있는데 그 중에 4 미만인 것만 남기고 싶으면 이렇게 쓰면 됩니다.
새어레이 출력해보면 [2, 3] 이것만 들어있겠군요. 
이런거 응용하면 쇼핑몰에서 "6만원 이하 상품만 보기" 이런 필터기능도 만들 수 있는 것입니다.
products라는 자료에서 6만원 이하만 필터하고 새로 html 생성하면 될 것 같군요 



#### map   
 - 배열 안에 자료들 전부 변형
 - 변수에 저장해야 됨   

<pre><code>
  var 어레이 = [7,3,5,2,40];

  var 새어레이 = 어레이.filter(function(a){
    return a * 4
  }); 
</code></pre>  
- 예를 들어 array 안의 숫자들을 전부 4를 곱해주고 싶으면 이렇게 코드짜면 됩니다.
새어레이 출력해보면 [28, 12, 20, 8, 160] 이게 들어있겠군요. 
이런거 응용하면 쇼핑몰에서 "달러 -> 원화로 변환하기" 이런 기능도 만들 수 있겠군요.
array 안에 있는 숫자들을 달러가격이라고 생각해봅시다. 이걸 전부 원화가격으로 변경하고 싶으면 어떻게하죠?
아마 map 써서 1000얼마 곱해주면 끝일듯요.   

---








