<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>용달 김사장</title>

<style>
body{font-family:Arial;margin:0;background:#f5f5f5}
header{background:#198754;color:white;text-align:center;padding:20px}
nav{text-align:center;background:white;padding:12px}
nav a{margin:8px;color:#198754;text-decoration:none}
section{background:white;margin:15px auto;padding:15px;max-width:900px;border-radius:8px}
.box{display:flex;gap:15px;max-width:930px;margin:auto}
.box section{width:50%}
input{padding:9px;width:100%;box-sizing:border-box}
button{padding:9px;background:#198754;color:white;border:0;margin-top:5px}
.post,.product{padding:10px;border-bottom:1px solid #ddd}
#postList,#productList{max-height:300px;overflow-y:auto}
table{width:100%;border-collapse:collapse}
th,td{border:1px solid #ddd;padding:8px;text-align:center}
footer{text-align:center;padding:20px}
@media(max-width:600px){
.box{display:block}
.box section{width:auto}
}
</style>
</head>

<body>

<header>
<h1>용달 김사장</h1>
<p>신속하고 믿을 수 있는 용달 서비스</p>
</header>

<nav>
<a href="#posts">게시글</a>
<a href="#products">상품</a>
<a href="#donation">기부금</a>
<a href="#contact">문의</a>
</nav>

<div class="box">

<section id="posts">
<h2>게시글</h2>
<input id="postSearch" placeholder="게시글 검색">
<button onclick="searchPosts()">검색</button>
<div id="postList"></div>
</section>

<section id="products">
<h2>상품</h2>
<input id="productSearch" placeholder="상품 검색">
<button onclick="searchProducts()">검색</button>
<div id="productList"></div>
</section>

</div>

<section id="donation">
<h2>기부금 사용내역</h2>

<table>
<tr>
<th>날짜</th>
<th>내용</th>
<th>금액</th>
</tr>

<tr>
<td>2026-01-01</td>
<td>천사무료급식소 기부</td>
<td>100,000원</td>
</tr>

<tr>
<td>2026-02-01</td>
<td>환경운동연합 기부</td>
<td>200,000원</td>
</tr>
</table>

<p><b>잔액 0원</b></p>
</section>

<section id="contact">
<h2>문의</h2>

<p>
전화:
<a href="tel:01026946608">010-2694-6608</a>
</p>

<p>
<a href="https://forms.gle/G9Bxju48dDDFhyMBA" target="_blank">
문의하기
</a>
</p>
</section>

<footer>
© 2026 용달 김사장. All rights reserved.
</footer>

<script>

const posts=[
{
title:"용달 김사장 오픈",
content:"용달 김사장 홈페이지가 오픈했습니다.",
date:"2026-09-23"
},
{
title:"용달 김사장 1분기 수입 보고",
content:"수입<br>3600만원<br><br>지출<br>세금: 600만원<br>수송원가: 300만원<br><br>순수익: 2700만원(매출의 50%)",
date:"2026-09-28"
}
];

const products=[
"🚚 일반배송 — 600원/km, 본부 반경 10km 이내 픽업/배송(예약제)",
"🚚 급행배송 — 900원/km, 본부 반경 10km 이내 픽업/배송(예약제)",
"🚚 장거리 배송 — 120원/km, 본부 반경 10km 외 픽업/배송(예약제)"
];

const postList=document.getElementById("postList");
const productList=document.getElementById("productList");

function showPosts(list){
postList.innerHTML="";
[...list].reverse().forEach(p=>{
postList.innerHTML+=`
<div class="post">
<b>${p.title}</b>
<p>${p.content}</p>
<small>${p.date}</small>
</div>`;
});
}

function searchPosts(){
let w=document.getElementById("postSearch").value.toLowerCase();
showPosts(posts.filter(p=>
p.title.toLowerCase().includes(w)||
p.content.toLowerCase().includes(w)
));
}

function showProducts(list){
productList.innerHTML="";
list.forEach(p=>{
productList.innerHTML+=`<div class="product">${p}</div>`;
});
}

function searchProducts(){
let w=document.getElementById("productSearch").value.toLowerCase();
showProducts(products.filter(p=>p.toLowerCase().includes(w)));
}

showPosts(posts);
showProducts(products);

</script>

</body>
</html>
