# game-sense
یک سایت برای عاشقان گیم❤️
<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>گیم سنتز | GAME SENSE</title>
<style>
*{box-sizing:border-box}
body{
 margin:0;
 font-family:Tahoma,Arial;
 background:#fff
 <script>
const games = [
["Red Dead Redemption 2","ماجراجویی در غرب وحشی با داستان آرتور مورگان، دنیای عظیم و شخصیت‌های فراموش‌نشدنی.","اکشن، جهان‌باز",97,"۹۹ گیگابایت"],
["The Last of Us Part II","داستان احساسی الی در دنیایی پساآخرالزمانی، با مخفی‌کاری و مبارزات هیجان‌انگیز.","اکشن، بقا",93,"۷۸ گیگابایت"],
["God of War (2018)","سفر کریتوس و آترئوس در سرزمین اساطیر نورس، همراه با مبارزات و باس‌فایت‌های جذاب.","اکشن، ماجراجویی",94,"۴۵ گیگابایت"],
["Ghost of Tsushima","در نقش یک سامورایی برای محافظت از جزیره تسوشیما در برابر مغول‌ها بجنگ.","اکشن، جهان‌باز",83,"۵۰ گیگابایت"],
["Marvel's Spider-Man","در نقش مرد عنکبوتی در نیویورک تاب بخور و با دشمنان مبارزه کن.","اکشن، ابرقهرمانی",87,"۴۵ گیگابایت"],
["Uncharted 4","نیتن دریک برای پیدا کردن گنجی افسانه‌ای وارد ماجراجویی خطرناکی می‌شود.","اکشن، ماجراجویی",93,"۶۳ گیگابایت"],
["Horizon Zero Dawn","در دنیایی پر از ماشین‌های غول‌پیکر، راز گذشته را کشف کن.","اکشن، نقش‌آفرینی",89,"۴۸ گیگابایت"],
["GTA V","در شهر لس‌سانتوس با سه شخصیت متفاوت زندگی کن.","اکشن، جهان‌باز",97,"۹۰ گیگابایت"],
["Resident Evil 2 Remake","برای زنده ماندن در شهر راکون و مقابله با خطرهای آن تلاش کن.","ترسناک، بقا",91,"۲۳ گیگابایت"],
["The Witcher 3","در نقش گرالت، شکارچی هیولاها، در دنیایی فانتزی سفر کن.","نقش‌آفرینی",92,"۵۰ گیگابایت"],
["Days Gone","در جهانی آلوده با موتور خود سفر کن و برای بقا بجنگ.","اکشن، بقا",71,"۶۰ گیگابایت"],
["Detroit Become Human","انتخاب‌های تو داستان سه اندروید را تغییر می‌دهند.","داستانی",78,"۴۳ گیگابایت"],
["Shadow of the Tomb Raider","لارا کرافت در جنگل‌های مرموز به کاوش و حل معما می‌پردازد.","ماجراجویی",75,"۴۰ گیگابایت"],
["Bloodborne","در شهر تاریک یارنام با هیولاهای ترسناک روبه‌رو شو.","اکشن",92,"۳۰ گیگابایت"],
["Sekiro","در نقش یک شینوبی در ژاپن فئودال مبارزه کن.","اکشن",90,"۱۳ گیگابایت"],
["Resident Evil 4 Remake","لئون برای نجات دختر رئیس‌جمهور به روستایی مرموز می‌رود.","ترسناک",81,"۵۸ گیگابایت"],
["Until Dawn","انتخاب‌های تو سرنوشت گروهی از دوستان را تغییر می‌دهد.","ترسناک",79,"۴۶ گیگابایت"],
["Batman Arkham Knight","در نقش بتمن از شهر گاتهام دفاع کن.","اکشن",87,"۴۵ گیگابایت"],
["A Plague Tale Innocence","آم
<script>
const grid=document.getElementById("grid");

games.forEach((g,i)=>{
 const card=document.createElement("div");
 card.className="card";

 const key="game_"+i;
 let likes=Number(localStorage.getItem(key+"_likes")||0);
 let liked=localStorage.getItem(key+"_liked")==="1";
 let comments=JSON.parse(localStorage.getItem(key+"_comments")||"[]");

 card.innerHTML=`
 <div class="poster">
 <div style="color:white;text-align:center;padding:55px 5px">
 ${g[0]}
 </div>
 </div>

 <div class="info">
 <h3>${g[0]}</h3>

 <span class="score">
 ${g[3]} / 100
 </span>

 <p class="desc">${g[1]}</p>

 <p class="detail">🎮 ژانر: ${g[2]}</p>
 <p class="detail">💾 حجم: ${g[4]}</p>

 <button class="like">
 ${liked?"❤️":"♡"} لایک
 (${likes})
 </button>

 <button class="comment">💬 نظرات</button>

 <div class="comments" style="display:none">
 <textarea placeholder="نظر خود را بنویسید"></textarea>
 <button class="send">ثبت نظر</button>
 <div class="list"></div>
 </div>
 </div>
 `;

 const likeBtn=card.querySelector(".like");

 likeBtn.onclick=()=>{
 liked=!liked;
 likes=Math.max(0,likes+(liked?1:-1));

 localStorage.setItem(key+"_likes",likes);
 localStorage.setItem(key+"_liked",liked?"1":"0");

 likeBtn.innerHTML=`${liked?"❤️":"♡"} لایک (${likes})`;
 };

 const box=card.querySelector(".comments");

 card.querySelector(".comment").onclick=()=>{
 box.style.display=box.style.display==="none"?"block":"none";
 };

 const list=card.querySelector(".list");

 function showComments(){
 list.innerHTML="";
 comments.forEach(c=>{
 const p=document.createElement("p");
 p.textContent=c;
 list.appendChild(p);
 });
 }

 showComments();

 card.querySelector(".send").onclick=()=>{
 const input=card.querySelector("
