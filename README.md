<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ReelPro - Pro Instagram Reel Editor</title>
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css"/>
<style>
body{margin:0;font-family:Arial,sans-serif;background:#0d0f1a;color:#fff;scroll-behavior:smooth;overflow-x:hidden;}
header{position:sticky;top:0;background:#111528;display:flex;justify-content:space-between;align-items:center;padding:20px 60px;z-index:1000;box-shadow:0 2px 10px rgba(0,0,0,0.5);}
header h1{color:#ff4d79;cursor:pointer;font-size:28px;font-weight:bold;} 
nav a{color:#fff;margin:0 12px;text-decoration:none;font-weight:600;cursor:pointer;transition:0.3s;}
nav a:hover{color:#ff4d79;}
section{padding:80px 60px;}
.hero{display:grid;grid-template-columns:1fr 1fr;gap:40px;align-items:center;background:url('https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=1200') center/cover no-repeat;border-radius:20px;padding:60px;position:relative;overflow:hidden;animation:fadeIn 1s ease-in;}
.hero::after{content:'';position:absolute;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.5);border-radius:20px;}
.hero div{position:relative;z-index:1;}
.hero h2{font-size:48px;margin-bottom:20px;color:#fff;text-shadow:2px 2px 8px rgba(0,0,0,0.6);animation:slideDown 1s ease-in;}
.hero p{font-size:20px;line-height:1.6;color:#ddd;}
.btn{display:inline-block;padding:14px 26px;background:#ff4d79;color:#fff;border-radius:30px;text-decoration:none;font-weight:bold;margin-top:20px;cursor:pointer;transition:0.3s,transform 0.3s;}
.btn:hover{background:#ff3377;transform:scale(1.05);}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:30px;}
.card{background:#1a1f3d;padding:30px;border-radius:16px;transition:transform 0.3s,box-shadow 0.3s;cursor:pointer;position:relative;overflow:hidden;animation:fadeIn 0.8s ease-in;}
.card:hover{transform:translateY(-10px);box-shadow:0 10px 25px rgba(255,77,121,0.3);}
.card h3{color:#ff4d79;margin-bottom:12px;}
.portfolio img{width:100%;border-radius:16px;transition:transform 0.3s,filter 0.3s;cursor:pointer;}
.portfolio img:hover{transform:scale(1.05);filter:brightness(1.1);}
.modal, .order-modal{display:none;position:fixed;z-index:2000;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.9);justify-content:center;align-items:center;}
.modal img, .order-modal img.preview{max-width:90%;max-height:80%;border-radius:16px;transition:0.5s;}
.modal span, .order-modal span.close{position:absolute;top:20px;right:40px;font-size:40px;color:#fff;cursor:pointer;}
.order-modal form{background:#1a1f3d;padding:40px;border-radius:16px;width:90%;max-width:500px;display:flex;flex-direction:column;gap:15px;animation:fadeIn 0.5s ease-in;}
.order-modal form h2{color:#ff4d79;margin-bottom:15px;text-align:center;}
footer{background:#111528;padding:40px 60px;text-align:center;font-size:16px;}
input,textarea,select{width:100%;padding:12px;border-radius:8px;border:none;margin:5px 0;background:#0d0f1a;color:#fff;}
input::placeholder,textarea::placeholder,select{color:#aaa;}
button{padding:12px 20px;border:none;border-radius:20px;background:#ff4d79;font-weight:bold;cursor:pointer;transition:0.3s,transform 0.3s;}
button:hover{background:#ff3377;transform:scale(1.05);}
.social-icons a{color:#fff;margin:0 10px;font-size:28px;transition:0.3s;}
.social-icons a:hover{color:#ff4d79;transform:scale(1.2);}
.floating-order{position:fixed;bottom:20px;right:20px;background:#ff4d79;color:#fff;padding:16px 22px;border-radius:50px;font-weight:bold;cursor:pointer;box-shadow:0 5px 15px rgba(255,77,121,0.4);transition:0.3s,transform 0.3s;z-index:3000;}
.floating-order:hover{transform:scale(1.1);}

/* WhatsApp Group Button */
.whatsapp-group-btn{
  position:fixed;
  top:50%;
  left:10px;
  transform:translateY(-50%);
  background:#25D366;
  color:#fff;
  padding:16px 20px;
  border-radius:50px;
  font-weight:bold;
  text-decoration:none;
  z-index:5000;
  box-shadow:0 5px 15px rgba(0,0,0,0.3);
  transition:0.3s, transform 0.3s;
}
.whatsapp-group-btn:hover{background:#1ebe57;transform:scale(1.05);}

/* Description / Disclaimer section */
.description{background:#1a1f3d;padding:30px;border-radius:20px;margin:40px 0;text-align:center;}
.description h3{color:#ff4d79;margin-bottom:12px;font-size:28px;}
.description p{color:#ddd;font-size:18px;line-height:1.6;}

/* Notification style */
#notification{position:fixed;bottom:100px;right:20px;background:#ff4d79;padding:15px 20px;border-radius:12px;box-shadow:0 5px 15px rgba(255,77,121,0.5);z-index:4000;display:none;animation:slideUp 0.5s ease;}
@keyframes slideUp{from{opacity:0;transform:translateY(50px);}to{opacity:1;transform:translateY(0);}}
@keyframes fadeIn{from{opacity:0}to{opacity:1}}
@keyframes slideDown{from{opacity:0;transform:translateY(-50px)}to{opacity:1;transform:translateY(0)}}
@media(max-width:800px){.hero{grid-template-columns:1fr;padding:40px}.hero h2{font-size:36px}.hero p{font-size:18px}}
</style>
</head>
<body>

<header>
<h1 onclick="scrollToSection('home')">ReelPro</h1>
<nav>
<a onclick="scrollToSection('home')">Home</a>
<a onclick="scrollToSection('services')">Services</a>
<a onclick="scrollToSection('portfolio')">Portfolio</a>
<a onclick="scrollToSection('pricing')">Pricing</a>
<a onclick="scrollToSection('contact')">Contact</a>
</nav>
</header>

<section id="home" class="hero">
<div>
<h2>Professional Instagram Reel Editing</h2>
<p>High-quality, trendy, viral-ready Reels for Instagram. Make your content stand out.</p>
<a href="https://chat.whatsapp.com/CoxRybIdkqVKieHBXPHxvc" target="_blank" class="btn">Order Your Reel</a>
<div class="social-icons" style="margin-top:20px">
<a href="https://instagram.com/yourhandle" target="_blank"><i class="fab fa-instagram"></i></a>
</div>
</div>
<div>
<img src="https://images.pexels.com/photos/774909/pexels-photo-774909.jpeg?auto=compress&cs=tinysrgb&w=800" style="width:100%;border-radius:20px"/>
</div>
</section>

<!-- Description / Disclaimer -->
<section class="description">
<h3>About Our Services</h3>
<p>At ReelPro, we provide professional Instagram Reel editing services including trendy effects, smooth transitions, music synchronization, color grading, and text animations.  
Please note: All content must comply with Instagram guidelines and should not include any copyrighted material without permission. By using our services, you agree that the content you submit is your own or you have rights to use it. We aim to deliver high-quality, engaging, and viral-ready Reels to boost your social media presence.</p>
</section>

<section id="services">
<h2>Our Services</h2>
<div class="cards">
<div class="card"><h3>Reels Editing</h3><p>Trending and viral Reels with professional edits.</p></div>
<div class="card"><h3>Short Form Videos</h3><p>High-quality shorts optimized for Instagram.</p></div>
<div class="card"><h3>Effects & Transitions</h3><p>Trendy effects and smooth transitions.</p></div>
</div>
</section>

<section id="portfolio" class="portfolio">
<h2>Portfolio</h2>
<div class="cards">
<div class="card"><img src="https://images.pexels.com/photos/414612/pexels-photo-414612.jpeg?auto=compress&cs=tinysrgb&w=800" onclick="openModal(this)"/><h3>Reel 1</h3></div>
<div class="card"><img src="https://images.pexels.com/photos/3244513/pexels-photo-3244513.jpeg?auto=compress&cs=tinysrgb&w=800" onclick="openModal(this)"/><h3>Reel 2</h3></div>
<div class="card"><img src="https://images.pexels.com/photos/3182786/pexels-photo-3182786.jpeg?auto=compress&cs=tinysrgb&w=800" onclick="openModal(this)"/><h3>Reel 3</h3></div>
</div>
</section>

<div id="modal" class="modal" onclick="closeModal()">
<span>&times;</span>
<img id="modalImg" src=""/>
</div>

<footer>
<p>© 2026 ReelPro. All Rights Reserved.</p>
</footer>

<!-- Floating Order Button -->
<div class="floating-order" onclick="window.open('https://chat.whatsapp.com/CoxRybIdkqVKieHBXPHxvc','_blank')">Order Your Reel</div>

<!-- WhatsApp Group Button -->
<a href="https://chat.whatsapp.com/CoxRybIdkqVKieHBXPHxvc" target="_blank" class="whatsapp-group-btn">Join WhatsApp Group</a>

<script>
function scrollToSection(id){document.getElementById(id).scrollIntoView({behavior:'smooth'});}
function openModal(img){document.getElementById('modal').style.display='flex';document.getElementById('modalImg').src=img.src;}
function closeModal(){document.getElementById('modal').style.display='none';}
</script>

</body>
</html>
