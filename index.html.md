<!DOCTYPE html>  
<html>  
<head>  
<meta charset="UTF-8">  
<title>ねこタップゲーム（10匹バージョン）</title>  
<style>  
  body {  
    text-align: center;  
    background: linear-gradient(#ffeef5, #fff7fc);  
    font-family: "Arial";  
    overflow: hidden;  
  }  
  #cat {  
    width: 220px;  
    transition: transform 0.15s, filter 0.2s;  
    border-radius: 20px;  
  }  
  #count {  
    font-size: 26px;  
    margin-top: 20px;  
    color: #ff7fa8;  
  }  
  .heart {  
    position: absolute;  
    font-size: 28px;  
    color: #ff9ecb;  
    animation: float 1.2s ease-out;  
  }  
  @keyframes float {  
    from { opacity: 1; transform: translateY(0) scale(1); }  
    to { opacity: 0; transform: translateY(-60px) scale(1.4); }  
  }  
</style>  
</head>  
<body>  
  
<h2>🐾 ねこタップゲーム（10匹バージョン）🐾</h2>  
  
<img id="cat">  
  
<div id="count">タップ数：0</div>  
  
<script>  
let count = 0;  
const cat = document.getElementById("cat");  
const countText = document.getElementById("count");  
  
// 10匹のねこキャラ  
const cats = [  
  { src: "https://placekitten.com/300/300", hearts: ["💗","💕"], sound: "ぽふっ" },  
  { src: "https://placekitten.com/301/300", hearts: ["❤️","💖","💘"], sound: "にゃっ！" },  
  { src: "https://placekitten.com/300/301", hearts: ["💞","💓"], sound: "すり…" },  
  { src: "https://placekitten.com/302/300", hearts: ["💗","💘"], sound: "みゃっ" },  
  { src: "https://placekitten.com/300/302", hearts: ["💖","💕"], sound: "ふにゃ" },  
  { src: "https://placekitten.com/303/300", hearts: ["💗","💞"], sound: "くるっ" },  
  { src: "https://placekitten.com/300/303", hearts: ["❤️","💓"], sound: "すん…" },  
  { src: "https://placekitten.com/304/300", hearts: ["💘","💕"], sound: "とてっ" },  
  { src: "https://placekitten.com/300/304", hearts: ["💞","💖"], sound: "ぷるっ" },  
  { src: "https://placekitten.com/305/300", hearts: ["💗","💓","💘"], sound: "にゃふ" }  
];  
  
// ランダムで1匹選ぶ  
let currentCat = cats[Math.floor(Math.random() * cats.length)];  
cat.src = currentCat.src;  
  
cat.addEventListener("click", () => {  
  count++;  
  countText.textContent = "タップ数：" + count;  
  
  // ねこが喜ぶ演出  
  cat.style.transform = "scale(1.15)";  
  cat.style.filter = "brightness(1.2)";  
  setTimeout(() => {  
    cat.style.transform = "scale(1)";  
    cat.style.filter = "brightness(1)";  
  }, 150);  
  
  // ハート演出  
  const heart = document.createElement("div");  
  heart.className = "heart";  
  heart.textContent = currentCat.hearts[Math.floor(Math.random()*currentCat.hearts.length)];  
  heart.style.left = (Math.random() * window.innerWidth) + "px";  
  heart.style.top = (Math.random() * window.innerHeight) + "px";  
  document.body.appendChild(heart);  
  
  setTimeout(() => heart.remove(), 1200);  
});  
</script>  
  
</body>  
</html>  
