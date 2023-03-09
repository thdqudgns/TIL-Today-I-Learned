1. [HTML](https://github.com/thdqudgns/TIL-Today-I-Learned/tree/main/AgainTIL/FrontEnd#-html-%ED%95%99%EC%8A%B5-%EB%B0%A9%EB%B2%95)
2. [CSS](https://github.com/thdqudgns/TIL-Today-I-Learned/tree/main/AgainTIL/FrontEnd#-css-%ED%95%99%EC%8A%B5-%EB%B0%A9%EB%B2%95)

# ⚓ HTML 학습 방법

## 1. [w3schools](https://www.w3schools.com/html/exercise.asp?filename=exercise_html_attributes1) 
에서 퀴즈를 풀면서 HTML 기본 태그에 대한 학습을 진행한다.   
![image](https://user-images.githubusercontent.com/92148521/223776247-e52139b2-14d8-43d3-94c7-3ae3f0af79b4.png)   
   
설명서도 있는데, 예시코드와 그 코드가 브라우저에 어떻게 보이는지까지 확인할 수 있어서 좋다.
![image](https://user-images.githubusercontent.com/92148521/223776142-02c19dc9-8334-4a00-a3a6-dbb416bd68da.png)


## 2. [MDN](https://developer.mozilla.org/ko/docs/Web/HTML)
학습 방법은 w3schools와 비슷하다. 간단한 설명을 하고, 예시 코드를 보여준다.
![image](https://user-images.githubusercontent.com/92148521/223776861-8c0d35dd-7a6c-4bdc-9273-e3e85d0408f7.png)



## 평가
> 둘 다 비슷한 방법으로 HTML을 학습할 수 있다.   
개인적으로는 w3schoos가 밝고 깔끔해서 w3school를 이용했다.
   
   
---

   
# 🧮 CSS 학습 방법

## 1. 선택자 공부하기 [CSS Diner](https://flukeout.github.io/)
CSS Editor 부분에 어떻게 선택자를 작성할 것인지 적으면 된다. 이를 통해 CSS 에서 어려운 부분 중 하나인 선택자에 대해 학습할 수 있다.   
오른쪽에는 어떻게 푸는지 **Hint** 까지 주어진다.
![image](https://user-images.githubusercontent.com/92148521/223777811-4374ad00-e6e5-4e7f-8bc0-efb8a8a29387.png)

## 2. [선택자 이미지](https://specifishity.com/)
한 장의 이미지다.    
선택자의 작성에 따라 무엇이 선택되는지 이미지로 재밌게 보여준다.

## 3. [w3schools - CSS](https://www.w3schools.com/css/default.asp), [MDN - CSS](https://developer.mozilla.org/ko/docs/Web/CSS)
HTML 파트에서 소개한 사이트들이다. HTML뿐만 아니라, CSS, JS 등 여러 가지 학습할 수 있다.

## 23/03/09 학습 내용 : 
- HTML 파일 안에 CSS를 적용하는 방법과 우선순위 :
  1. 인라인
   ```css
   <li style="color: violet;">111</li>
   ```
  2. 내부 style 태그, link 태그를 이용한 외부 호출
   ```css
   <style>
        li {
            color: red;
            background-color: antiquewhite;
        }
    </style>
    
    <link rel="stylesheet" href="./exam01.css" />
   ```

- 선택자 우선순위 : 직접적인 선택일수록 올라감   
id > class > 태그명

- 글자 관련 속성 : 
   - font-family : 글꼴
   - font-size : 글자 크기
   - font-weight : 글자 굵기
   - text-decoration : 글자 꾸미기
   
- 정렬 관련 속성 :
   - text-align
   - text-indent
   - line-height
   - vertical-align
   
- 공간 관련 속성 :
   - margin / padding : 외부 여백 / 내부 여백
   - width / height : 폭 / 높이
   - display
   - float
   - clear
   - overflow
   - text-overflow
   - white-space
   - min-height
   - position, top / bottom / left / right
   
- 테두리 속성 : 
   - border : 테두리 굵기, 모양, 색상
   - border-collapse : 테두리 합치기
   - border-radius : 테두리 둥글게

- 그 외 속성 : 
   - color : 글자색
   - background-color : 배경색
   - cursor : 마우스 포인터 변경
   - list-style : li 태그의 모양
   
