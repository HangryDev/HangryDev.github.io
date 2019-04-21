EXTJS: 

EXTJS가 하는 일:? 웹 사이트에 쓰이는 UI 요소들을 구현합니다 (ex, 버튼/팝업/그래프). 

html 스크립트를 직접 편집하는 것보다 간단한다는 장점이 있습니다. 

Ext. 로 시작하는 코드가 보이면  Ext.JS 프레임워크의 기능을 사용한다는 뜻입니다. 



'위젯': 

EXTJS를 이용해 구현된 UI 요소들을 위젯이라고 부릅니다. (ex, 버튼/팝업/그래프). 

위젯의 종류는 크게 두가지로 나뉩니다.  

컨테이너 위젯 : 다른 위젯을 추가할 수 있는 위젯 

컴포넌트 위젯:  다른 위젯을 추가할 수 없는 위젯




EXT.JS 코드는 '컨테이너' 안에 '컴퍼넌트'가 들어가 있는 형태로 구현됩니다. 



(그림 1. 회원가입 창) 

컨테이너 위젯 안에 컴퍼넌트가 구현 된 예시 화면입니다. 

그림 1에서 User info가 쓰여 있는 회색 상자는 패널(Panel)이라는 컨테이너 위젯이고, User ID가 쓰여 있는 흰색 상자는 텍스트박스(textbox)라는 컴퍼넌트 위젯입니다. 

컨테이너 안에 컨테이너가 들어가는 것도 물론 가능합니다. 예시에서 User Info 회색 패널은 흰색 panel 안에 구현되어 있습니다. 


EXTJS 코드 리딩: 


0 어떤 위젯들이 생성되는지를 찾아냅니다.  

웹사이트가 로딩될 때, 가장 기본이 되는 컨테이너가 있습니다. 그 컨테이너의 뒤에는 .OnReady가 붙어 있습니다. 

.OnReady - 화면이 불러오지는 순간에 괄호 안의 코드를 실행하라는 뜻입니다.

.OnReady 안에 다른 패널들이 붙습니다. 

아래의 세 키워드를 주목해서, 어떤 위젯들이 생성되는지와 포함 관계를 파악하시면서 코드를 읽습니다

1 Ext.Create -

 Ext.Create('Ext.panel.Panel') 

* alert, confirm 등 create를 거치지 않고 생성되는 컴포넌트도 있습니다. 

2 Ext.Define

Ext.define('KitchenSink.view.form.RegisterForm', {

extend: 'Ext.form.Panel',

xtype: 'form-register',

)}

3 컨테이너 위젯의  Item : 을 살펴보면, 거기에 다른 위젯이 추가되어 있는지를 알 수 있습니다. 

2-1 items: 배열 안에 xtype(약칭)으로 추가

ex)  Ext.Create('Ext.panel.Panel', { items : { xtype: 'button', text: '확인'}})

2-2 add 메소드   

ex) tab.add( Ext.create('' , ));  


2 위젯들의 속성 (config) 지정 

위젯의 속성은 key / value 형식으로 쓰여 있습니다.  (JSON 구조 따름) 

특히 중요한 속성들 몇 가지를 예시로 들어 보았습니다. 

2-1 store - 어떤 스토어를 사용할 것인가 

2-2 style - css 적용

2-3 renderTo - 페이지의 어느 위치에 표기시킬지 정해줍니다. 코드 하단의 HTML 스크립트에 대응합니다. 


3 confing 중 listener, handler는 특히 중요합니다. 이 두 속성은 특정 event가 발생 시 동작시킬 코드를 담고 있습니다.  

3-1 listener - component에 이벤트를 적용할 때 씀. 특정 이벤트가 발생할 경우, listner 발동 - 안에 있는 함수 동작

ex) 클릭 시 '다음 펑션을 수행' - click: function()

jsonAraay 형태로 선언. [{event 1: function()}, {event 2: function()},{event 3: function()}]

3-2 handler -  listener의 shotcut. 콤포넌트에 별도로 제공될 시 사용 가능. 

리스너와 달리 다대일 대응이 안 된다. (핸들러는 한 이벤트 : 한 행동)(리스너는 한 이벤트: 여러 행동, 혹은 배열로 여러 이벤트: 각각의 행동) 
	* 


4.  renderer config 또한 중요합니다.  출력될 데이터를 받아와서 -> 추가적인 스크립트로 데이터를 가공한 다음 -> 스토어에 있는 값은 유지한 채로, 화면에 출력되는 값만 변경해주는 역할을 합니다. 

사용 예시: 숫자 데이터를 그리드에 출력할 때, 화면에 보이는 숫자 천 단위마다 ,를 찍어주고 싶을 때 renderer를 사용하면 좋습니다. 

주의) 반드시 리턴을 줘야 합니다.
