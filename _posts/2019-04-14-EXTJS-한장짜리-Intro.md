기본 문법 이해 
Ext로 시작, Ext.JS가 정의된 기능을 이용하기 위해서는.
탭/패널/차트 등을 구현한다.  tml 스크립트를 직접 편집하지 않고.  


위젯: 화면을 구성하는 요소들
컨테이너: 추가되는 위젯을 받을 상위 위젯. 도화지. 
컴포넌트 : 화면에 나타나는 모든 위젯 - 다른 위젯을 받을 수 없음. 


1 컨테이너 생성.  (패널, 뷰포트, 탭 등) 
생성 방식 1 Ext.Create ex) Ext.Create('Ext.panel.Panel') -> 괄호 안 클래스 이름 입력
* alert, confirm 등 create를 거치지 않고 생성되는 컴포넌트도 있다. 
Ext.Define
'OnReady' - 화면이 로딩 되는 순간 발동 


2 Item에 콤포넌트 추가.
2-1 items: 배열 안에 xtype(약칭)으로 추가
    ex)  Ext.Create('Ext.panel.Panel', { items : { xtype: 'button', text: '확인'}})
2-2 add 메소드   
    ex) tab.add( Ext.create('' , ));  
  
3 config (속성) 지정 
key / value 형식을 지님.  (JSON 구조 따름) 
특히 중요한 친구들 아래 모음
3-1 store - 데이터를 저장하는 역할
fields - key를 나타내주는 값. (DB에서 칼럼명이라고 생각하자. coulmn은 supr_nm, key는 애경식품) 
3-2 style - css 적용
3-3 renderTo - 원하는 위치에 표출시키기. 


4 event - rstener, handler
4-1 listener - component에 이벤트를 적용할 때 씀. 특정 이벤트가 발생할 경우, listner 발동 - 안에 있는 함수 동작
ex) 클릭 시 '다음 펑션을 수행' - click: function()
jsonAraay 형태로 선언. [{event 1: function()}, {event 2: function()},{event 3: function()}]
핸들러와 같으나, 콤포
4-2 handler -  listener의 shotcut. 콤포넌트에 별도로 제공될 시 사용 가능. 
리스너와 달리 다대일 대응이 안 된다. (핸들러는 한 이벤트 : 한 행동)(리스너는 한 이벤트: 여러 행동, 혹은 배열로 여러 이벤트: 각각의 행동) 


* 툴바에서 '[]' 와 {}로 감싸는 것 차이 - 전자는 영역을 주고, 후자 (오브젝트) 는 가능한 영역 전체를 가져간다. - 그리드에서도 이게 마찬가지로 적용되겠구나!!!
* define을 통해 


5.  renderer - 출력될 데이터를 받아와서 -> 추가적 스크립트로 가공한 다음 -> 스토어에 있는 값은 유지한 채로, 화면에 출력되는 값만 변경
사용례: 천 단위마다 콤마 찍기 
리턴을 줘야 한다. 출력 안 된다 없을 시. 
docs 들어가서 - (콤포넌트).renderer 검색 -> 패러미터에 대한 설명 나옴


6. 쿼리 - 안 씀. 있다는 것만 알아두면 된다
