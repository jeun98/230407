# 230407

﻿
230407 31일차


요소가 높이를 읽지 못하는 경우

1) float 해제를 안했을때

2) position: absolute;가 적용된 요소는 부모가 자식의 높이를 읽을 수 없음


** 지금 있는 공간에서 랜덤으로 이동을 해야할때에 position; absolute; 사용하고 아닐때에는 최대한 사용 자제


집에서 >> header 부분 position으로 위치 잡기 // 헤더 삼각형 배경이미지로 넣어보기


display : none; 요소를 없애는것뿐만 아니라 공간까지 없는 취급을 함


형제요소 선택자 : <태그> ~ <태그> { }


section .content .box-wrap .box ~ .box /*(여기서 .box ~ .box 가 형제요소 선택자)*/{
    margin-left: 26.66px;
}
내용을 입력하세요.

가로 나열
- flout / display:inline-block; 의 차이점 : flout은 여백이 없음

------------------------------------------------------------------------------------------------

가상요소로 구분선 만드는 방법


footer ul li {
    /*float: left;*/
    display: inline-block;
    margin-right: 12px;
    position: relative; /* ::before 요소의 기준 */
    padding-right: 10px;
}

footer ul li:last-child {
    margin-right: 0;
}

footer ul li::before {
    content: "";
    display: block;
    width: 2px;
    height: 14px;
    background-color: silver;
    position: absolute;
    left: 100%;
    top: 3px;
}

footer ul li:last-child::before {
    display: none;
    padding-right: 0;
}

---------------------------------------------------------------------

# 05_menu1.html


<!DOCTYPE html>
<html lang="ko">

<head>
    <meta charset="utf-8">
    <title>05_menu1</title>

    <link rel="stylesheet" href="css/05_menu1_2.css">
</head>

<body>

    <header>
        <h1><a href="#">LOGO</a></h1>

        <nav>
            <ul>
                <li><a href="#">메인메뉴1</a></li>
                <li><a href="#">메인메뉴2</a></li>
                <li><a href="#">메인메뉴3</a></li>
                <li><a href="#">메인메뉴4</a></li>
            </ul>
        </nav>
    </header>

    <section>
        <article class="main">
            <p>메인이미지 슬라이드</p>
        </article>

        <article class="product">
            <div class="item1">Product1</div>
            <div class="item2">Product2</div>
            <div class="item1">Product3</div>
            <div class="item2">Product4</div>
        </article>

        <article class="banner">
            <div class="banner1">Banner1</div>
            <div class="banner2">Banner2</div>
        </article>
    </section>

    <footer>
        <div class="footer-top">
            <ul>
                <li><a href="#">회사소개</a></li>
                <li><a href="#">사이트맵</a></li>
                <li><a href="#">이용약관</a></li>
                <li><a href="#">개인정보처리방침</a></li>
            </ul>

            <div class="sns"><a href="#">SNS연결</a></div>
        </div>

        <div class="footer-bottom">
            <p>&copy;Copyright2023</p>
        </div>
    </footer>

</body>

</html>

--------------------------------------------------------------------------------------------------------

# 05_menu1.css


@charset "utf-8";

* {
    margin: 0;
    padding: 0;
}

ul,
ol {
    list-style: none;
}

ul::after,
ol::after {
    content: "";
    display: block;
    clear: both;
}

li {
    float: left;
    list-style: none;
}

a {
    text-decoration: none;
}

body {
    text-align: center;
    line-height: 30px;
}


header {
    /*background-color: antiquewhite;*/
}

header h1 {
    height: 60px;
    /*background-color: yellow;*/
    line-height: 60px;
}

header nav {
    width: 600px;
    height: 40px;
    /*background-color: lightpink;*/
    margin: 0 auto;
}

header nav ul {}

header nav ul li {
    width: 25%;
    line-height: 40px;
    /*outline: 1px solid red;*/
}

header nav ul li a {
    color: #333;
    display: block;
}

header nav ul li a:hover {
    background-color: lightskyblue;
}


section {
    width: 90%;
    max-width: 1200px;
    margin: 0 auto 50px;
    /*outline: 2px solid blue;*/
}

section .main {
    width: 100%;
    height: 500px;
    background-color: #fed136;
}

section .product {
    width: 100%;
}

section .product > div {
    width: 25%;
    height: 250px;
    float: left;
    /*display: inline-block;*/
}

/* 짝수홀수 이용해서 배경 넣기 */
section .product > div:nth-child(2n) {
    background-color: lightgreen;
}
section .product > div:nth-child(2n+1) {
    background-color: lightcoral;
}

/*section .product .item1 {
    background-color: lightcoral
}
section .product .item2 {
    background-color: lightgreen;
}*/

section .banner {
    clear: both;
    width: 100%;
    height: 120px; /* 부모가 높이값을 가지고 있어서 float 해제됨 */
    /*outline: 2px solid red;*/
}

section .banner > div {
    width: 50%;
    height: 100%;
    float: left;
}

section .banner .banner1 {
    background-color: olive;
}

section .banner .banner2 {
    background-color: yellow;
}

footer {
    width: 100%;
    background-color: lightgray;
    font-size: 14px;
    border-top: 1px solid #888;
}

footer a {
    color: #333;
}

footer .footer-top {
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
    border-bottom: thin solid #888;
    overflow: hidden;
    line-height: 40px;
}

footer .footer-top ul {
    float: left;
}
footer .footer-top ul li {
    margin-right: 20px;
}

footer .footer-top .sns {
    float: right;
}

footer .footer-bottom {
    clear: both;
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
    text-align: left;
    padding: 20px 0 30px;
}

--------------------------------------------------------------------------------------

★ 메뉴는 목록태그를 사용 (99.9%) ★

footer-top은 2덩어리로 나누기 >> 왼쪽 하나, sns연결 하나


li의 부모(ul, ol)는 정해져있기때문에 reset에서 float을 적용 할 수 있음

(오직 li만 reset에서 float 적용 가능 그 외의 태그들은 불가능)


/* RESET */
ul,ol {
    list-style: none;
}

ul::after, ol::after {
    content: "";
    display: block;
    clear: both;
}

li {
    float: left;
    list-style: none;
}
내용을 입력하세요.
header의 높이(100px) = h1의 높이(60px) + nav의 높이(40px)


header {
    background-color: antiquewhite;
}

header h1 {
    height: 60px;
    background-color: yellow;
    line-height: 60px;
}

header nav {
    width: 600px;
    height: 40px;
    background-color: lightpink;
    margin: 0 auto;
}

--------------------------------------------------------------

◆ 부모의 너비가 변동 될 수 있기 때문에 자식의 너비는 %로 적용



header nav {
    width: 600px;
    height: 40px;
    /*background-color: lightpink;*/
    margin: 0 auto;
}

header nav ul {}

header nav ul li {
    width: 25%;
    line-height: 40px;
    outline: 1px solid red;
}

header nav ul li a {
    color: #333;
}

header nav ul li a:hover {
    background-color: lightskyblue;
}
내용을 입력하세요.
>>> 이 상태에서 hover 했을때 이런식으로 나옴
<img src="1.png">

<a>에 display:block; 을 넣어주면 (a태그는 inline요소이기때문에 텍스트 만큼만 배경색이 나와서 block요소로 변경해줌)


header nav ul li a {
    color: #333;
    display: block;
}

▼▼▼▼ 이런식으로 나옴

<img src="2.png">



▼▼▼▼ display: inline-block; 적용시
<img src="3.png">



높이는 모든 높이값이 상속되지 않음 (필요할경우에는 높이를 줘야함)

높이값을 %로 주고싶으면 >> 부모로부터 50%를 받게 해야함 (부모요소의 높이 값이 없는 경우에는 높이 값이 적용되지 않음)


border 가늘게 : thin


float : 부모가 자식의 높이를 읽을 수 없음 / 다음 요소에 영향을 줌



▼▼ 이거 두개는 세트라 같이 작성해줘야함 ▼▼


.clear {overflow:hidden;}
.clear::after {} >> 얘만 작성해도 괜춘
내용을 입력하세요.

﻿
