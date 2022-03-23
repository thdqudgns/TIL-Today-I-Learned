# :pushpin: CSS

### CSS, Cascading Style Sheets
- HTML, XML, XHTML 등의 마크업 언어(Markup Language)가 화면에서 표현되는 방법(스타일, 모양, style)을 기술하는 언어이다
- HTML에 작성된 태그들이 화면에 보여지는 모양을 지정한다
- 부모태그(상위태그)에 스타일 시트를 적용하면 자식태그(하위태그)에도 해당 스타일이 적용된다 (스타일 상속, Cascading)

### CSS를 HTML에 적용하는 방법 3가지
1. 인라인(inline) 방식
	- HTML태그의 style속성을 이용하여 스타일을 적용한다
	- 장점 : 태그를 보면서 스타일 지정이 가능하다
	- 단점 : 각각 태그에 스타일을 일일히 적용해야하기 때문에 관리가 힘들다
2. 임베디드(embedded) 방식
	- head 태그 내에 style 태그를 생성하고 그 안에 스타일을 작성한다
	- CSS선택자(selector)를 이용한다
	- 장점 : 모든 스타일 시트를 한번에 확인할 수 있다
	- 단점 : 태그와 스타일시트가 서로 떨어져 있어서 곧바로 스타일 적용결과를 예측하기 힘들다
3. 별도의 CSS파일을 로드하는 방식
	- @import방식과 link 방식이 있다
	- 스타일 시트를 별도의 외부파일로 작성하여 관리한다
	- HTML파일에서 외부 CSS파일을 로드해서 사용한다
	- CSS파일의 확장자는 주로 .css로 사용한다
	- 장점 : 스타일을 부여하는 목적(기능)에 따라서 파일을 분리할 수 있다
	> ex) main.css, common.css, board.css, login.css, ...
	
    - 단점 : 관리해야하는 파일이 많아진다
    - ** @import보다 link 방식을 사용하는 것이 좋다
	- ** link 태그 하나에 하나의 CSS파일을 로드하도록 작성한다

### CSS 색상 단위
- 색상 이름, Color Name
	- black, white, red, blue, gray, green, ...
- RGB
	- Red, Green, Blue 색상의 조합을 이용하여 색상을 표현한다
	- R, G, B 에 해당하는 값을 각 자리에 0-255 또는 0%-100%로 표현한다
	- rgb(R, G, B) 형식으로 표현한다
	> ex)	rgb(255, 0, 0) -> RED
- RGBA
	- RGB표현법 + Alpha(투명도)
	- 투명도는 0.0(투명) ~ 1.0(불투명) 수치로 표현한다
	- rgb(R, G, B, A) 형식으로 표현한다
	> ex)	rgb(0, 255, 255, 0.5) -> 반투명 CYAN
- 16진수 표현법, Haxadecimal, HEX
	- RGB에 해당하는 각 수치를 16진수로 변환하여 붙여서 한번에 표현한 것
	- #RRGGBB 형식으로 표현된다
	    - ( 10진수 0 -> 16진수 00 )
	    - ( 10진수 255 -> 16진수 FF )
	- #RRGGBB -> #RGB 형식으로 축약해서 표현 가능하다
	    - RR -> R
	    - GG -> G
	    - BB -> B
	    - 같은 숫자 두개를 한 개로 줄여서 표현한다
	> ex) rgb(255,255,0)	-> #FFFF00	-> yellow   
				            -> #FF0

	> ex)	#6622EE -> #62E
- HSL
	- Hue, Satulation, Lightness (색조, 채도, 명도)
	- hsl(H, S, L) 형식으로 표현한다
	- 색조, hue : 0 ~ 360, 색 각도
		- 0 또는 360 : RED
		- 120 : GREEN
		- 240 : BLUE
    - 채도, satulation : 0% ~ 100%
		- 0% : 무채색, 회색 빛
		- 100% : 유채색, 본연의 빛
	- 명도, lightness : 0% ~ 100%
		- 0% : 어두운, black
		- 100% : 밝은, white
	    - 50% : 적당한 명도
- HSLA
	- HSL표현법 + Alpha(투명도)

### 색 조합 추천 사이트
- https://color.adobe.com/ko/explore/?filter=most-popular&time=month
- https://www.webdesignrankings.com/resources/lolcolors/
- https://www.palettable.io/

### 웹 안전 색상, Web Safe Color
- RGB 기준으로 표현 가능한 색상의 조합은 ‭16,777,216‬ 가지이다
    - R : 0~255, 256가지
	- G : 0~255, 256가지
	- B : 0~255, 256가지
	- RGB조합 : 256 * 256 * 256 = 16777216
- RGB조합의 모든 색상을 웹에서 나타내기에는 현실적인 어려움이 있다
- 색상을 간소화하여 웹 표준 안전 색상을 정한 것
- 시스템 환경(운영체제, 브라우저, 디바이스 장치 등)에 구애받지 않고 표현 가능한 색상들을 정해놓은 것
- 0~255 수치 중에서 00, 33, 66, 99, cc, ff 만 사용해서 색상을 표현한다
- 간소화하면 0, 3, 6, 9, c, f로 사용할 수 있다
	- 256가지를 6가지로 바꾼 것
	- 6 * 6 * 6 = 216가지 색상이 된다
	> ex)	#ccc, #f39, #930

### 크기 단위
- 고정 크기 단위
	- 부모요소의 크기에 영향받지않고 일정한 크기를 유지하는 단위
	- px, 픽셀 : 화소 단위, 정확한 크기나 위치를 설정할 때 사용
	- in, 인치 : 미리 설정되어있는 화소 개수를 기준으로 인치를 표현한다 (보통 96px)
    - pc, 파이카 : 1/6 in == 16px
	- pt, 포인트 : 1/12 pc == 1/72in == 1.3px
	- cm, 센티미터 : 약 2.54cm == 1in
	- mm, 밀리미터 : 1/10 cm
    - 현실의 크기와는 다르다
- 가변 크기 단위
	- 부모요소의 크기에 비례한 상대적인 크기를 지정하는 단위
    - %, 퍼센트 : 부모요소의 크기에 대한 비율로 지정한다
	- em, 이엠 : EleMent, 부모요소의 크기에 대한 배율로 지정한다 (1em == 100%, 1.5em == 150%)
	- rem, 루트 이엠 : Root EleMent, 최상위 부모요소(HTML태그)에 대한 배율
	- ex, 이엑스 : Element X-height, 현재 폰트의 소문자 'x' 크기에 대한 배율

### 태그의 id, class 속성
- 두 속성 모두 Global Attribute(공용 속성)이다
- 모든 태그들이 다 사용할 수 있는 속성이다
- id속성
	- HTML문서에서 요소들을 서로 구분하기 위해 사용하는 속성
	- 문서 내에서 고유한 값으로 부여해야 한다
	- Javascript 이벤트(event) 처리코드를 작성할 때 많이 사용한다
	- CSS를 적용할 때에도 많이 사용한다
	- #기호와 연계해서 사용한다
- class속성
	- 태그들을 같은 그룹으로 편성할 때 사용한다
	- 여러 태그들을 같은 클래스값을 적용하여 같은 그룹으로 표현한다
	- 클래스값이 같은 그룹끼리 같은 스타일을 적용할 수 있다
	- Javascript코드로 그룹에게 적용할 수 있다
	- .기호와 연계해서 사용한다
	- 클래스값은 여러 개를 부여할 수 있다
	- 각각의 값을 띄어쓰기로 구분하여 하나의 문자열로 작성한다
    ```html
	ex)	<p class="colorRed blue menu">테스트</p>
    ```

### CSS 선택자, Selector
- HTML문서에서 특정 요소를 선택하는 CSS문법
- 선택자를 이용하여 선택된 요소들에게 일괄적으로 스타일을 적용할 수 있다

### 선택자의 종류
- 전체 선택자 : * { }
- 태그 선택자 : tagName { }
- 아이디 선택자 : #idName { }
- 클래스 선택자 : .className { }
- 복합 선택자
	- 둘 이상의 선택자를 조합하여 복합적으로 사용하는 방법
	- 선택자에 포함된 요소들의 관계를 따져서 태그들을 선택한다
    1. 하위(자손) 선택자 - Descendent
	    - E F
	    - E요소의 하위 요소인 F들을 선택한다
    ```html
	ex)	div p { }
		div태그의 자손들 중에서 모든 p태그를 선택한다

		#board .title { }
		id가 board인 요소의 자손들 중에서 class가 title인 태그들을 선택
    ```
	2. 자식 선택자 - Child
	    - E > F
	    - E요소의 자식 요소인 F들을 선택한다
	3. 형제 선택자 - Sibling
	    - E + F
            - E의 인접한 형제 F (E요소의 바로 뒤에 오는 F요소 한 개를 선택)
	    - E ~ F
	        - E의 일반적인 형제 F (E요소를 뒤따르는 모든 F요소 전부를 선택)
- 속성 선택자
	- 요소의 속성(Attribute)을 이용하여 선택한다
    ```html
	[attr]		attr속성을 가지고 있는 모든 태그를 선택

	[attr="val"]	attr속성의 값이 val과 같은 태그를 선택
			(속성의 값이 띄어쓰기까지 전부 완전 일치해야함)

	[attr~="val"]	attr속성의 값으로 val단어를 완전 포함하는 태그를 선택
	(띄어쓰기로 구분되어있는 단어가 같은 값을 가지고 있으면 선택된다)

	[attr^="val"]	attr속성의 값이 val로 시작하는 태그를 선택

	[attr$="val"]	attr속성의 값이 val로 끝나는 태그를 선택

	[attr*="val"]	attr속성의 값이 val을 부분 포함하는 태그를 선택

	[attr|="val"]	attr속성의 값이 "val"과 같거나 "val-"로 시작하는 태그
    ```
- 가상 선택자, Pseudo Selector, 의사 선택자
	- HTML문서에는 실제 요소로 존재하지 않은 대상을 선택한다
	- 이벤트 기반, 순서 기반 가상 선택자가 있다
	1. 가상 클래스 선택자(이벤트 기반)
	    - :hover - onmouseover, onmouseout 이벤트에 반응하여 요소 선택
		    - (mouseover - 마우스 올림)
		    - (mouseout - 마우스 내림)

	    - :active - onmousedown에 반응 (마우스 눌림)
	    - :link	- a 태그의 방문 전 상태
	    - :visited - a 태그의 방문 후 상태
	    - :checked - checked상태인 요소 선택 (checkbox, radio)
	    - :focus - onfocus상태인 요소 선택 (사용자의 입력이 가능한 상태)
	    - :empty - 컨텐츠가 비어있는 요소 선택, 자식요소가 없는 요소를 선택
	2. 가상 클래스 선택자(순서 기반)
	    - :root		- 최상위 태그 선택, html 태그
	    - :nth-child(n)		- 앞에서부터 n번째 요소 선택
	    - :nth-last-child(n)	- 뒤에서부터 n번째 요소 선택
	    - :first-child	- 첫번째 요소 선택
	    - :last-child	- 마지막 요소 선택
	    - :only-child	- 유일한 자식 요소(형제요소가 없을 때 선택)
	    - :only-of-type	- 유일한 태그 타입(형제요소가 있어도 단독 타입일 때)
	3. 가상 요소 선택자
	    - ::before	- 태그의 앞에 가상 요소를 추가한다
	    - ::after	- 태그의 뒤에 가상 요소를 추가한다
	    - ::first-line		- 요소의 첫번째 줄을 선택
	    - ::first-letter	- 요소의 첫번째 문자를 선택
- 부정 선택자
    - :not(S) - 선택자조건 S를 만족하지 않는 요소를 선택 (S는 선택자(selector)를 이용하여 작성한다)
	> ex)	:not(ul) - ul태그 선택자로 선택되지 않는 요소를 선택   
	ex)	p:not(.new)	- 클래스속성값이 new가 아닌 p태그 선택

### CSS스타일 적용 우선 순위
- 선택자 우선순위
    1. 아이디 선택자
	2. 클래스/속성/가상 선택자
	3. 태그 선택자
	4. 전체 선택자
- 스타일 적용 방법에 따른 우선순위
	1. !important
	2. 인라인
	3. 임베디드
	4. @import
	5. link 태그
	6. link 태그 안에 적용된 @import
	7. 브라우저의 기본 스타일

### CSS 레이아웃, Layout
- 화면에 표현될 요소(태그)를 배치하는 작업
- 어떤 요소를 어디에 어떻게 배치할 것인가에 대한 전략
	> 태그의 모양, 배치될 위치, 다른 요소들과의 관계

### 태그의 기본적인 영역 속성
- width : 컨텐츠 영역의 너비
- height : 컨텐츠 영역의 높이
- padding : 내부 여백
- border : 테두리
- margin : 외부 여백

### CSS 여백
- 태그 요소를 감싸고 있는 투명한 공간
- padding(내부여백), margin(외부여백)으로 구성된다
- padding은 테두리 안쪽으로 컨텐츠영역을 감싸고 있다
- margin은 테두리 바깥쪽으로 태그 요소영역을 감싸고 있다
- padding, margin 둘 다 top, right, bottom, left로 구성된다

### 여백 설정 방법
- margin, padding 둘 다 설정방법이 똑같다
- 크기 단위로 설정한다
- margin-top, margin-right, margin-bottom, margin-left로 각각 방향에 맞는 여백 설정 가능
- padding도 똑같다

### 축약 설정 방법
- margin: all; /* 상하좌우 똑같이 적용한다 */
- margin: top&bottom left&right; /* 각각 상하, 좌우에 적용한다 */
- margin: top left&right bottom; /* 각각 상, 좌우, 하에 적용한다 */
- margin: top right bottom left; /* 각각 상, 우, 하, 좌에 적용한다 */

### CSS 테두리
- 태그의 컨텐츠 영역과 내부 여백을 감싸는 영역
- 테두리까지 요소의 내부로 취급된다
- 설정 방식
	- border: border-width border-style border-color;
    > ex)	border: 1px solid black;
- border-width
	- 테두리 두께
	- 주로 px단위를 이용하여 설정한다
	- thin(1px), thick(5px), medium(3px, 기본값)
- border-style
	- 테두리 선의 모양(스타일)
	- solid: 실선
	- dotted: 점
	- dashed: 점선
	- double: 두 줄
    - groove: 안쪽 마루
	- ridge: 바깥쪽 마루
	- inset: 오목, 안쪽 그림자
	- outset: 볼록, 바깥쪽 그림자
	- hidden: 숨김, 없애기
- border-color
	- 테두리 색상
	- 색상 단위를 이용한 테두리 색상 지정

### 레이아웃의 흐름 속성
- 요소가 배치되는 방향(흐름)을 설정하는 속성
- float속성
    - 요소를 배치하는 방향을 지정하는 속성
    ```html
	속성값
	left	- 왼쪽을 기준으로 배치
	right	- 오른쪽을 기준으로 배치 
	none	- float하지 않음

	** float == 뜨다, 떠돌다 의미를 가지고 있음. 요소를 이동시킬 수 있는 상태(유동성이 있는 상태)로 설정하고, 여백공간에 다른 텍스트 또는 다른 요소가 배치될 수 있도록 만들어진 속성

	이미지와 텍스트(주로 p태그)를 한 줄에 같이 배치하기 위해 사용되는 속성
     -> float속성을 부여받은 요소는 다음에 오는 요소들에게 영향을 준다
	 -> 요소가 배치되는 흐름이 변경된다
    ```    
- clear속성
	- float속성을 부여하면 그 다음에 오는 요소들은 float요소 옆으로 배치되려는 성질을 가진다
	- clear속성을 이용하여 float의 영향에서 벗어나도록 설정한다
    ```html
	속성값
	left	- float:left;속성 무시(제거)
	right	- float:right;속성 무시(제거)
	both	- left, right 플롯 속성 둘 다 무시(제거)
	none	- float의 영향을 허용한다
    ```

### block 모델
- display: block; 속성을 부여받은 블록 요소의 레이아웃 모델
- 내용물(컨텐츠, 주로 inline요소)들이 들어갈 영역을 지정할 때 사용하는 모델

### 블록요소의 자체 레이아웃 특성
- width, height 속성 적용할 수 있다
	- width	- 기본값으로 부모요소의 너비만큼으로 설정된다(100%)
	- height	- 기본값으로 내부 요소의 최대 높이로 자동 설정된다(auto)
- margin 속성
	- 외부의 다른 요소와의 간견을 설정하는 속성
	- margin영역이 서로 만나는 부분은 밀어내지 않고 겹쳐진다
	- 요소는 밀어내지만 margin영역이 겹쳐진다
- block요소의 내부 정렬 (컨텐츠 정렬)
    - text-align속성을 이용한다
- block요소의 외부 정렬
	- margin: 0 auto;를 이용한다
	- 단, 외부정렬하려면 width가 설정되어 있어야만 가능하다

### 종결 블록요소
- 자식태그로 다른 블록요소를 가질 수 없는 태그
- 인라인 요소만 컨텐츠(자식 요소)로 가질 수 있다
- h1~h6, p, caption, dt, address, blockquote 등등

### overflow 속성
- 블록 요소의 컨텐츠 크기(너비, 높이)가 존재할 때 내용물이 컨텐츠 영역보다 커서 넘친 부분에 대한 표현 방법을 설정한다
- overflow 설정값
	- visible	넘쳐나온 부분 보여주기(기본값)
	- hidden	넘쳐나온 부분 감추기(잘라내기)
	- scroll	상하, 좌우 스크롤바 생성하기
		- (상하 스크롤 == 수직 스크롤 == vertical scroll == vscroll)
		- (좌우 스크롤 == 수평 스크롤 == horizontal scroll == hscroll)
	- auto      내용물이 넘칭 방향으로만 스크롤 생성하기

### inline 모델
- block모델 요소의 내부에 표현되는 요소의 속성
- inline 요소끼리는 같은 줄에 여러 개를 배치할 수 있다
- 컨텐츠(내용물)가 부모 요소의 너비를 초과하면 새 행으로 줄바꿈한다
- border도 같이 줄바꿈 처리된다

### 인라인요소의 자체 레이아웃 특성
- width, height
	- 적용되지 않는다
	- 컨텐츠영역의 크기는 내용물에 맞춰서 자동 결정된다
- margin
	- left, right만 적용된다
	- top, bottom이 없다
- line-height
	- 줄 간격 속성
	- 텍스트가 들어갈 수 있는 공간의 높이를 설정한다
	- inline요소의 높이(height)를 결정하는 속성으로 사용된다
	- 또한, margin-top, margin-bottom 대신 사용할 수 있다

### inline-block 모델
- block모델과 inline모델의 표현방식이 혼합된 것
- 내부 동작은 block모델
	- 요소의 자체 레이아웃 설정이 block모델처럼 동작
	- width, height, padding, border, margin 모두 적용 가능하다
- 외부 동작은 inline모델
	- 외부 요소와의 관계에 대한 설정이 inline모델처럼 동작
	- 블록처럼 한 줄을 다 차지하지 않는다
	- 인라인처럼 한 줄에 여러 개의 요소를 배치할 수 있다

### 인라인블록모델의 자체 레이아웃 특성
- width, height 속성
	- 설정 가능
	- 내용물의 크기에 맞추려면 auto값으로 설정 (height 기본값)
	- 부모요소에 맞추려면 100%값으로 설정 (width 기본값)
- margin-top, margin-bottom 속성
	- 설정 가능
- margin-left, margin-right 속성
	- 외부 요소와의 간격
	- 인라인모델처럼 동작한다

### table 모델
- table 태그의 레이아웃
- display: table; 을 이용하여 설정 가능하다
- 외부 레이아웃은 블록과 유사하다

### table 태그의 자체 레이아웃
- width
	- 설정 가능
	- 내부 테이블셀(table-cell)의 너비만큼 크기를 가진다(auto)
- height
	- 설정 가능
	- 내부 테이블셀(table-cell)의 높이만큼 크기를 가진다(auto)
- padding
	- 설정 가능
	- table의 테두리와 테이블셀 사이의 공간이 넓어진다
- margin
	- 설정 가능
	- 외부 요소와의 간격이 넓어진다

### tr 태그의 자체 레이아웃
- display: table-row; 속성이 부여되어있음
- width적용 안됨
- height만 적용됨
- padding, margin 적용해도 변화 없음

### th, td 태그의 자체 레이아웃
- display: table-cell; 속성이 부여되어있음
- width,height 둘 다 적용 가능
- padding 적용 가능
- margin 적용 불가

### 테두리, border
- table, td, td 에 각각 테두리가 있다
- tr 에는 테두리가 없음
- border-collapse속성을 이용하여 겹치는 부분을 처리한다
	- separate설정 - 각각 따로 표현 (기본값)
	- collapse설정 - 합쳐서 한 줄로 표현

### position 속성
- 요소 배치 속성
- 요소의 위치를 설정하는 속성
- position속성을 이용하여 요소의 위치를 변경할 수 있고, 위치가 변경되어도 display속성은 유지된다

### position 속성 설정값
- static (기본값)
	- 요소의 기본 위치
	- 요소가 자연스럽게 위치했어야하는 곳에 배치된다
- absolute
	- 절대적인 위치를 지정한다
    - 부모요소에 position속성이 없으면 브라우저의 화면을 기준으로 위치가 지정된다 (스크롤을 따라가지 않는다), (화면의 크기가 달라지면 위치도 바뀐다)
	- 부모요소에 position속성이 있으면 부모요소의 상하좌우를 기준으로 위치가 지정된다
- relative
	- 상대위치를 지정한다
	- static표현되어야하는 위치의 좌측상단지점을 기준으로 이동된다
	- 요소의 기본위치에 있던 공간이 유지된다
	    - 다른 태그 요소가 해당 공간을 차지않고 비워둔다
	    - 상대위치박스는 이동시키지 않고 사용하게된다
	    - 기본 자리를 유지하며 absolute박스의 부모요소로 사용한다
- fixed
	- 고정위치를 지정한다
	- 보고 있는 화면의 상하좌우 벽면을 기준으로 이동된다
	- 스크롤을 따라온다
- **top, bottom, left, right 속성을 이용하여 요소의 위치를 이동시킨다**
- **이동되는 위치의 기준점은 position속성별로 다르다**

### 시맨틱 레이아웃, Semantic Layout
- 웹페이지의 레이아웃 구조를 쉽게 이해할 수 있도록 이름을 붙인 것
- 시맨틱 태그(Semantic Tag)를 활용하여 레이아웃을 구성한다
- 태그의 이름이나, id 또는 class에 설정된 키워드를 확인하면 HTML문서의 대략적인 구조를 파악할 수 있게 된다
- 검색엔진이 페이지의 구성을 파악할 수 있도록 해준다
```html
	<header>
		사이트 소개, 로고 등의 머리글 지정
		주로 위쪽에 삽입된다

	<nav>
		navigation, navigator, 메뉴
		사이트 내에서 다른 문서(페이지)로 연결되는 링크들의 모음

	<aside>
		사이드바
		광고, 배너, 작은 메뉴 등
		본문 이외의 내용이 표시되는 곳

	<section>
		실제 본문 내용
		컨텐츠 영역
		주제별로 카테고리를 나누는 역할로 사용한다

	<article>
		<section>카테고리의 내용물을 채워주는 곳

	<footer>
		바닥글
		사이트의 저작권, 제작자, 사업자등록번호
		주소, 전화번호, 간단한 회사 정보 등

		** 이용약관, 개인정보취급방침 (필수)
```

### CSS 브라우저 벤더 프리픽스(접두어)
- CSS3 스타일 속성 앞에 붙이는 브라우저별 접두어
- 브라우저마다 접두어가 다르다
- 접두어를 적용할 수 있는 속성도 다 다르다
- CSS3 표준문법을 개발하던 도중 브라우저 별로 테스트하거나, 그에 대한 피드백을 제공할 수 있도록 만들어진 것
- 시범 버전으로 CSS3속성을 개발하고 미리 사용해볼 수 있도록 한 것

### 벤더 프리픽스의 종류
    ```html
	-webkit-	크롬, 사파리
	-moz-		파이어폭스
	-o-		    오페라
	-ms-		인터넷 익스플로러
    ```
- **접두어를 적용한 속성을 먼저 작성하고 접두어를 제거한 표준 속성 작성**
- **브라우저에서 버전별로 제일 마지막으로 적용할 수 있는 속성이 화면에 반영된다**

### transition 속성
- CSS속성이 변화하는 과정을 서서히 진행되도록 설정하는 속성
- 설정값 지정하는 방법
    ```html
	transition: property duration delay timing;

	ex)	trainsition: background-color 3s;
    ```
### transition 상세 속성
- transition-property
	- transition속성이 적용될 CSS속성을 지정한다
	- none: 적용안함
	- all: 모든 속성에 반응하도록 설정
	- CSS property: 해당 속성에 반응
- transition-duration
	- 속성의 변화가 진행되는 시간 (지속시간)
	- 시간 단위로 s또는 ms를 사용한다 ( s-초, ms-밀리초 )
- transition-delay
	- 속성의 변화가 시작되는 시점을 지연시키는 시간
	- 시간 단위로 s또는 ms를 사용한다 ( s-초, ms-밀리초 )
  - transition-timing-function
	- 속성의 변화가 진행되는 속도를 조절하는 속성
	- ease (기본값)
		- 천천히 시작해서 빠른 진행 후 천천히 마무리
	- linear
		- 항상 일정한 속도
	- ease-in
		- 천천히 시작 후에 보통속도로 진행
	- ease-out
		- 보통 속도로 진행 후에 천천히 마무리
	- ease-in-out
        - 천천히 시작, 보통 진행, 천천히 마무리
