HTML 에서 Javascript 로드하기
==========================

**JavaScript로 웹페이지를 제어하기 위해서는 JavaScript를 로드해야 한다.**  
_JavaScript로 웹페이지를 제어하기 위해서는 JavaScript를 로드해야 한다._  
JavaScript로 웹페이지를 제어하기 위해서는 **JavaScript를 로드**해야 한다.  
_JavaScript로 웹페이지를 제어하기 위해서는 **JavaScript를 로드해야** 한다._    
JavaScript로 웹페이지를 제어하기 위해서는 JavaScript를 로드해야 한다.  
 
방법 1) inline: 태그에 직접 자바스크립트를 기술하는 방식
---------------------------

    <input type="button" onclick="alert('Hello world')" value="Hello world" />

(onclick 안에 JS 코드가 기입되어 있다) 

>장점: 태그와 연관되는 스크립트가 무엇인지 분명하게 알 수 있다.  
>단점: 정보와 제어가 섞여 있기 때문에 정보로서의 가치가 떨어진다.   
>>검색엔진이 찾아본다던지, 다른 외부 소프트웨어가 정리한다던지 할 때 그렇다.   
>>JS는 JS끼리, html는 htrl끼리 모아두는게 코드 읽을때 편하다.   

방법 2) Script: <script></script>태그를 만들어서 여기에 자바스크립트 코드를 삽입하는 방식.   
---------------------------

    <script type="text/javascript">  
        var hw = document.getElementById('hw');  
        hw.addEventListener('click', function(){  
            alert('Hello world');  
        })  
    </script>  

>장점: html 태그와 js 코드를 분리할 수 있다는 점


방법 3) 외부 파일로 분리
---------------------------
 >보다 엄격하게 정보와 제어를 분리할 수 있다.  
 >하나의 js 파일을 여러 웹페이지에서 로드함으로서 js의 재활용성을 높일 수 있다.  
 >캐쉬를 통해서 속도의 향상, 전송량의 경량화를 도모할 수 있다.  
 
    <script type="text/javascript" src="script2.js"></script>  


# <script> 태그 위치에 대한 댓글 논의
------------------------------ 
 
 일반적으로 이렇게 한다고 합니다: 
>1. Place library script such as the jQuery library in the head section.
>라이브러리 스크립트는 헤더에
>2. Place normal script in the head unless it becomes a performance/page load issue.
>성능/페이지 로딩문제가 없는 스크립트는 헤더에
>3. Place script that impacts the render of the page at the end of the body
>페이지 렌더링에 직결되는 스크립트는 바디 마지막에

+Js 는 맨하단에, css는 상단에 두는게 좋다고 합니다.
>일반적으로 브라우저가 **js파일을 읽을때는 html을 읽지 않습니다**.
>js내부에서 style을 제어하는 경우가 있기에 js를 읽는 동안에는 다른 작업을 하지 않죠.style을 제어할 경우 다시 그려야하기 때문에
>즉, html 중간이나 처음에 둘 경우 작업이 밀릴 수 있습니다.
>css를 앞에두는 이유는 아마(?) 브라우저가 css를 읽기 전까진 painting을 하지 않앗던걸로 기억해요

결론: JS script 태그는 바디 하단에 외부 파일로 넣는 것이 좋은 것 맞습니다. 로딩부하, 자원 관리, 코드 가독성, 코드 재사용 등등 잇점이 많으니까요.

