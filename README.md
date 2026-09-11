<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>The Daily Kitchen — today’s menu, tomorrow’s list, full recipes</title>
<meta name="description" content="Rotating North Indian vegetarian menu with South Indian breakfasts, next-day shopping list, and step-by-step recipes.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@500;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,400;0,9..40,500;0,9..40,700;1,9..40,400&display=swap" rel="stylesheet">
<style>
:root{
  --ink:#2A1A12;
  --ghee:#FFF4DC;
  --paper:#FFFBF0;
  --haldi:#F4A400;
  --mirchi:#D9322A;
  --dhania:#17794A;
  --neel:#2C3C99;
  --imli:#8A4B1E;
  --line:rgba(42,26,18,.14);
  --shadow:0 10px 0 -4px rgba(42,26,18,.10);
  --r:18px;
}
*{box-sizing:border-box}
html,body{margin:0;padding:0}
body{
  background:var(--ghee);
  background-image:
    radial-gradient(circle at 12% 8%, rgba(244,164,0,.20), transparent 42%),
    radial-gradient(circle at 88% 4%, rgba(217,50,42,.16), transparent 40%),
    radial-gradient(circle at 50% 100%, rgba(23,121,74,.14), transparent 48%);
  color:var(--ink);
  font-family:"DM Sans",system-ui,sans-serif;
  font-size:17px;line-height:1.6;
  -webkit-font-smoothing:antialiased;
}
h1,h2,h3,h4,.disp{font-family:"Baloo 2",system-ui,sans-serif;line-height:1.12;margin:0}
.wrap{max-width:1080px;margin:0 auto;padding:0 20px}
a{color:var(--neel)}

/* ---------- masthead ---------- */
header.top{padding:26px 0 6px}
.brandrow{display:flex;align-items:center;gap:14px;flex-wrap:wrap}
.mark{
  width:52px;height:52px;border-radius:50%;flex:none;
  background:conic-gradient(var(--haldi) 0 25%,var(--mirchi) 0 50%,var(--dhania) 0 75%,var(--neel) 0);
  box-shadow:inset 0 0 0 5px var(--ghee),inset 0 0 0 7px rgba(42,26,18,.5);
}
.brand{font-size:30px;font-weight:800;letter-spacing:-.02em}
.brand small{display:block;font-family:"DM Sans";font-size:14px;font-weight:400;opacity:.7;letter-spacing:0}
.datepill{margin-left:auto;background:var(--ink);color:var(--ghee);border-radius:999px;padding:8px 16px;font-size:14px;font-weight:500}

/* ---------- thali hero ---------- */
.hero{padding:18px 0 10px}
.thali{
  position:relative;display:grid;grid-template-columns:repeat(3,1fr);gap:16px;
  background:var(--paper);border:3px solid var(--ink);border-radius:28px;padding:18px;
  box-shadow:8px 8px 0 rgba(42,26,18,.85);
}
.katori{
  border-radius:22px;padding:16px 16px 18px;border:2px solid var(--ink);
  position:relative;overflow:hidden;min-height:186px;display:flex;flex-direction:column;
}
.katori.b{background:linear-gradient(175deg,#FFD262,#F4A400)}
.katori.l{background:linear-gradient(175deg,#63C795,#17794A);color:#FFF9EC}
.katori.d{background:linear-gradient(175deg,#7C8BE8,#2C3C99);color:#FFF9EC}
.katori h3{font-size:15px;font-weight:700;letter-spacing:.02em;opacity:.85;margin-bottom:6px}
.katori .clock{font-size:13px;opacity:.75;margin-bottom:10px}
.dishlist{list-style:none;margin:0;padding:0;display:flex;flex-direction:column;gap:6px}
.dishlist button{
  all:unset;cursor:pointer;font-family:"Baloo 2";font-size:20px;font-weight:700;line-height:1.15;
  border-bottom:2px dotted currentColor;padding-bottom:1px;
}
.dishlist button:hover{opacity:.72}
.dishlist button:focus-visible{outline:3px solid var(--ink);outline-offset:3px;border-radius:4px}
.katori .side{font-size:14px;opacity:.85;margin-top:auto;padding-top:10px}

/* ---------- tomorrow ---------- */
.tom{
  margin:34px 0;background:var(--ink);color:var(--ghee);border-radius:26px;padding:24px;
  box-shadow:8px 8px 0 rgba(217,50,42,.9);
}
.tom h2{font-size:27px;margin-bottom:2px}
.tom .sub{opacity:.72;font-size:15px;margin-bottom:18px}
.tommenu{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:20px}
.chip{background:rgba(255,244,220,.12);border:1px solid rgba(255,244,220,.28);border-radius:999px;padding:5px 12px;font-size:14px}
.cats{display:grid;grid-template-columns:repeat(auto-fit,minmax(215px,1fr));gap:18px}
.cat h4{font-size:17px;color:var(--haldi);margin-bottom:8px;border-bottom:1px solid rgba(255,244,220,.2);padding-bottom:5px}
.cat ul{list-style:none;margin:0;padding:0;font-size:15px}
.cat li{padding:3px 0;display:flex;gap:9px;align-items:flex-start}
.cat input{margin-top:5px;accent-color:var(--haldi);flex:none}
.cat label{cursor:pointer}
.cat input:checked + label{opacity:.42;text-decoration:line-through}
.tools{display:flex;gap:10px;flex-wrap:wrap;margin-top:22px}
.btn{
  font:inherit;font-weight:700;cursor:pointer;border-radius:999px;padding:10px 20px;
  border:2px solid var(--ghee);background:transparent;color:var(--ghee);
}
.btn.solid{background:var(--haldi);border-color:var(--haldi);color:var(--ink)}
.btn:hover{transform:translateY(-1px)}
.btn:focus-visible{outline:3px solid var(--haldi);outline-offset:3px}

/* ---------- rotation strip ---------- */
.sec{margin:44px 0}
.sechead{display:flex;align-items:baseline;gap:14px;flex-wrap:wrap;margin-bottom:16px}
.sechead h2{font-size:29px}
.sechead p{margin:0;opacity:.7;font-size:15px}
.strip{display:grid;grid-template-columns:repeat(auto-fill,minmax(176px,1fr));gap:12px}
.day{
  background:var(--paper);border:2px solid var(--ink);border-radius:16px;padding:12px 14px;font-size:14px;
  box-shadow:var(--shadow);
}
.day.today{background:var(--haldi)}
.day .dh{font-family:"Baloo 2";font-weight:700;font-size:17px;margin-bottom:6px;display:flex;justify-content:space-between;gap:8px}
.day .dh span{font-family:"DM Sans";font-size:12px;font-weight:500;opacity:.65}
.day p{margin:3px 0}
.day b{font-weight:700;color:var(--imli)}
.day.today b{color:var(--ink)}

/* ---------- recipe library ---------- */
.filters{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:16px;align-items:center}
.fchip{
  font:inherit;font-size:14px;font-weight:500;cursor:pointer;border:2px solid var(--ink);
  background:var(--paper);border-radius:999px;padding:6px 14px;
}
.fchip[aria-pressed="true"]{background:var(--ink);color:var(--ghee)}
#q{
  font:inherit;border:2px solid var(--ink);border-radius:999px;padding:9px 16px;background:var(--paper);
  min-width:210px;flex:1;color:var(--ink);
}
#q:focus{outline:3px solid var(--haldi);outline-offset:2px}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(224px,1fr));gap:14px}
.card{
  text-align:left;font:inherit;cursor:pointer;background:var(--paper);color:var(--ink);
  border:2px solid var(--ink);border-radius:var(--r);padding:16px;box-shadow:var(--shadow);
  display:flex;flex-direction:column;gap:6px;
}
.card:hover{box-shadow:0 4px 0 -1px rgba(42,26,18,.18);transform:translateY(2px)}
.card:focus-visible{outline:3px solid var(--mirchi);outline-offset:3px}
.card .rn{font-family:"Baloo 2";font-size:21px;font-weight:700;line-height:1.12}
.card .meta{font-size:13px;opacity:.7}
.tagdot{width:9px;height:9px;border-radius:50%;display:inline-block;margin-right:6px}
.t-north{background:var(--mirchi)} .t-south{background:var(--dhania)} .t-basic{background:var(--neel)}
.empty{grid-column:1/-1;padding:28px;text-align:center;opacity:.7;border:2px dashed var(--line);border-radius:var(--r)}

/* ---------- modal ---------- */
dialog#rec{
  border:none;padding:0;max-width:720px;width:calc(100% - 28px);border-radius:24px;
  background:var(--paper);color:var(--ink);box-shadow:0 24px 60px rgba(42,26,18,.4);
}
dialog#rec::backdrop{background:rgba(42,26,18,.62)}
dialog[open]{animation:pop .22s cubic-bezier(.2,.9,.3,1.4)}
@keyframes pop{from{transform:scale(.94) translateY(12px);opacity:0}}
.rhead{padding:24px 26px 20px;border-bottom:3px solid var(--ink)}
.rhead.north{background:linear-gradient(160deg,#FFD262,#F4A400)}
.rhead.south{background:linear-gradient(160deg,#63C795,#17794A);color:#FFF9EC}
.rhead.basic{background:linear-gradient(160deg,#7C8BE8,#2C3C99);color:#FFF9EC}
.rhead h3{font-size:34px;letter-spacing:-.01em}
.rhead .rmeta{font-size:14px;margin-top:6px;opacity:.9}
.rbody{padding:24px 26px 30px;max-height:62vh;overflow:auto}
.rbody h4{font-size:20px;margin:24px 0 10px}
.rbody h4:first-child{margin-top:0}
.ingtable{width:100%;border-collapse:collapse;font-size:15px}
.ingtable td{padding:6px 0;border-bottom:1px dashed var(--line);vertical-align:top}
.ingtable td:last-child{text-align:right;white-space:nowrap;font-weight:500;padding-left:14px}
ol.steps{margin:0;padding:0;list-style:none;counter-reset:s}
ol.steps li{counter-increment:s;position:relative;padding:0 0 16px 46px;font-size:16px}
ol.steps li::before{
  content:counter(s);position:absolute;left:0;top:0;width:32px;height:32px;border-radius:50%;
  background:var(--mirchi);color:#FFF9EC;font-family:"Baloo 2";font-weight:700;
  display:grid;place-items:center;font-size:17px;
}
ol.steps li b{color:var(--imli)}
.tipbox{background:rgba(244,164,0,.18);border-left:5px solid var(--haldi);border-radius:0 12px 12px 0;padding:14px 16px;font-size:15px}
.tipbox ul{margin:0;padding-left:18px}
.tipbox li{margin:4px 0}
.reflinks{font-size:14px;opacity:.8;margin-top:20px;border-top:1px dashed var(--line);padding-top:14px}
.closebar{position:sticky;bottom:0;background:var(--paper);border-top:2px solid var(--ink);padding:12px 26px;display:flex;gap:10px;justify-content:flex-end}
.btn.dark{border-color:var(--ink);color:var(--ink)}
.btn.dark.solid{background:var(--ink);color:var(--ghee)}

footer{margin:60px 0 40px;font-size:14px;opacity:.72;border-top:2px solid var(--line);padding-top:18px}

@media(max-width:760px){
  .thali{grid-template-columns:1fr;box-shadow:5px 5px 0 rgba(42,26,18,.85)}
  .katori{min-height:auto}
  .brand{font-size:25px}
  .datepill{margin-left:0}
}
@media(prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
@media print{
  body{background:#fff}
  header.top,.hero,.sec,footer,.tools{display:none}
  .tom{background:#fff;color:#000;box-shadow:none;border:1px solid #000}
  .cat h4{color:#000}
}
</style>
</head>
<body>

<header class="top"><div class="wrap brandrow">
  <div class="mark" aria-hidden="true"></div>
  <div class="brand">The Daily Kitchen<small>Today’s menu, tomorrow’s shopping list, full recipes</small></div>
  <div class="datepill" id="today"></div>
</div></header>

<main class="wrap">

  <section class="hero" aria-label="Today's menu">
    <div class="thali">
      <div class="katori b"><h3>Nashta</h3><div class="clock">7:30 – 9:00</div><ul class="dishlist" id="m-b"></ul><div class="side" id="s-b"></div></div>
      <div class="katori l"><h3>Dopahar ka khana</h3><div class="clock">1:00 – 2:00</div><ul class="dishlist" id="m-l"></ul><div class="side" id="s-l"></div></div>
      <div class="katori d"><h3>Raat ka khana</h3><div class="clock">8:00 – 9:30</div><ul class="dishlist" id="m-d"></ul><div class="side" id="s-d"></div></div>
    </div>
  </section>

  <section class="tom" id="tomorrow">
    <h2>Kal ke liye kharidna hai</h2>
    <p class="sub" id="tomdate"></p>
    <div class="tommenu" id="tommenu"></div>
    <div class="cats" id="shop"></div>
    <div class="tools">
      <button class="btn solid" id="copy">Copy list</button>
      <button class="btn" id="print">Print list</button>
      <button class="btn" id="reset">Clear ticks</button>
    </div>
  </section>

  <section class="sec">
    <div class="sechead"><h2>Agle 14 din</h2><p>Menu apne aap rotate hota hai — har roz page kholo, aaj ka plan sabse upar.</p></div>
    <div class="strip" id="strip"></div>
  </section>

  <section class="sec">
    <div class="sechead"><h2>Saari recipes</h2><p>Kisi bhi dish par click karo, poori vidhi khul jayegi.</p></div>
    <div class="filters">
      <input id="q" type="search" placeholder="Dhoondo — paneer, dal, dosa…" aria-label="Search recipes">
      <button class="fchip" data-f="all" aria-pressed="true">Sab</button>
      <button class="fchip" data-f="breakfast" aria-pressed="false">Nashta</button>
      <button class="fchip" data-f="main" aria-pressed="false">Sabzi &amp; Dal</button>
      <button class="fchip" data-f="side" aria-pressed="false">Roti, Chawal, Raita</button>
      <button class="fchip" data-f="south" aria-pressed="false">South Indian</button>
    </div>
    <div class="grid" id="grid"></div>
  </section>

  <footer>
    <p>Ye recipes is site ke liye khaas likhi gayi hain. Inhi dishes ke doosre versions dekhne ke liye <a href="https://www.tarladalal.com" target="_blank" rel="noopener">Tarla Dalal</a>, <a href="https://nishamadhulika.com" target="_blank" rel="noopener">Nisha Madhulika</a> aur <a href="https://www.sanjeevkapoor.com" target="_blank" rel="noopener">Sanjeev Kapoor</a> ki apni websites dekhein.</p>
  </footer>
</main>

<dialog id="rec" aria-labelledby="rtitle">
  <div class="rhead" id="rhead"><h3 id="rtitle"></h3><div class="rmeta" id="rmeta"></div></div>
  <div class="rbody" id="rbody"></div>
  <div class="closebar"><button class="btn dark" id="copyIng">Copy ingredients</button><button class="btn dark solid" id="close">Band karo</button></div>
</dialog>

<script>
/* ===================================================================
   RECIPE DATA
   ing: [item, qty, unit, category]  qty null = "to taste"/"as needed"
   =================================================================== */
const R = {

/* ---------------- BREAKFAST ---------------- */
"aloo-paratha":{n:"Aloo Paratha",type:"breakfast",tag:"north",time:"45 min",serves:4,
ing:[["Gehun ka atta",400,"g","Anaj"],["Aloo (ubla)",500,"g","Sabzi"],["Pyaz (barik)",1,"medium","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Adrak (kisa)",1,"tsp","Sabzi"],["Jeera",1,"tsp","Masale"],["Ajwain",0.5,"tsp","Masale"],["Amchur",1,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",4,"tbsp","Dairy"],["Dahi (side)",200,"g","Dairy"]],
steps:[
"Atta gundho: 400 g atta mein 1 tsp namak aur 1 tbsp ghee mila kar ungliyon se ragdo — 30 second. Phir thoda-thoda paani daal kar (lagbhag 230–250 ml) narm, chipchipa nahi, aisa dough bana lo. 5 minute achhi tarah gundho jab tak surface smooth na ho. Geela kapda dhak kar <b>20 minute rest</b> do — ye step skip kiya to paratha phategaa.",
"Aloo ko cooker mein 3 seeti (ya 20 min ubaal) — <b>bilkul thoda paani</b> mein. Zyada paani wala aloo geela stuffing dega. Ubalne ke baad chhilka utaar kar aloo ko 10 minute thanda hone do, warna bhaap se filling paste ban jaati hai.",
"Aloo ko masher se mash karo — grater use mat karo, chipku ho jaata hai. Koi bhi gaanth na rahe, par mash ko over-mix bhi mat karo.",
"Mash mein pyaz, hari mirch, adrak, dhania, jeera, ajwain (haath par masal kar), amchur, lal mirch, garam masala aur namak daalo. Namak <b>banane se just pehle</b> daalo — pehle daloge to pyaz paani chhodega.",
"Filling ke 8 barabar gole bana lo (lagbhag lemon size). Dough ke bhi 8 gole — filling ka gola dough ke gole se thoda bada hona chahiye. Yahi asli ratio hai.",
"Dough gole ko 4 inch ki katori jaisa bela, beech mein filling rakho, kinare upar utha kar potli band karo, upar ki extra dough choti karke pinch kar do.",
"Sookha atta laga kar halke haath se belo — beech se bahar ki taraf, ek hi jagah baar-baar mat dabao. 7 inch tak jao. Belan par vajan bilkul halka rakho.",
"Tawa madhyam-tez aanch par garam karo. Paratha daalo, 30–40 second jab tak halke chhote bubble dikhein, palto.",
"Doosri side par 0.5 tsp ghee lagao, palto, pehli side par bhi ghee. Ab spatula se halka dabate hue seko jab tak dono taraf sunhare-bhoore chitte na aa jaayein — har side 60–90 second.",
"Garam paratha turant plate mein, upar makkhan. Dahi, achar aur nимbu ke saath serve karo. Dher lagana ho to casserole mein rakho, plate mein dhak kar nahi — warna bhaap se narm pad jaate hain."],
tips:["Aloo ubalte waqt namak mat daalo — chhilka mushkil se utarta hai.","Filling agar geeli lage to 1 tbsp bhuna besan mila do.","Tawa lohe ka ho to crust best aata hai."]},

"poha":{n:"Indori Poha",type:"breakfast",tag:"north",time:"25 min",serves:4,
ing:[["Poha (motа)",3,"cup","Anaj"],["Pyaz",2,"medium","Sabzi"],["Aloo",1,"medium","Sabzi"],["Hari mirch",3,"","Sabzi"],["Kadi patta",12,"","Sabzi"],["Nimbu",1,"","Sabzi"],["Hara dhania",0.3,"cup","Sabzi"],["Rai",1,"tsp","Masale"],["Jeera",0.5,"tsp","Masale"],["Saunf",0.5,"tsp","Masale"],["Haldi",0.75,"tsp","Masale"],["Cheeni",1.5,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",3,"tbsp","Other"],["Moongfali",0.3,"cup","Other"],["Sev (upar)",0.5,"cup","Other"]],
steps:[
"Poha ko chalni mein daal kar nal ke neeche <b>15 second</b> dhoyo, beech mein ungli se halka hilao. Turant paani band. Chalni ko 10 minute aise hi rakha raho — poha apne aap phool jayega. Bowl mein bhigona sabse badi galti hai, ghol ban jaata hai.",
"Phoole poha par 1 tsp namak, 0.75 tsp haldi aur 1.5 tsp cheeni chhidko. Ungliyon se halke haath se mix karo — chamach se mat, dane toot jaayenge. Alag rakho.",
"Kadhai mein 1 tbsp tel garam karke moongfali madhyam aanch par 3 minute bhooно jab tak chhilka chatakne na lage. Nikaal lo.",
"Usi kadhai mein 2 tbsp tel, rai daalo — jab tak chatakna band na ho tab tak haath mat lagao (30 second). Phir jeera aur saunf, 10 second.",
"Kadi patta aur kati hari mirch daalo — 20 second, tez khushboo aane tak.",
"Aloo ke chhote cube daalo, dhak kar madhyam aanch par 6–7 minute, beech mein hilate raho, jab tak kanta aar-paar na ho jaye.",
"Barik kata pyaz daalo. Yahan pyaz ko <b>bhoora mat karo</b> — sirf 3 minute, jab tak paardarshi (translucent) ho jaye. Indori poha mein pyaz narm chahiye, karara nahi.",
"Aanch dheemi karo, poha daalo, moongfali milao aur neeche se upar ki taraf folding style mein mix karo — 1 minute.",
"Dhak kar <b>2 minute steam</b> do. Yahi step poha ko fuluffy karta hai.",
"Gas band, nimbu nichodo, hara dhania. Plate mein sev, barik pyaz aur jeeravan (agar ho) daal kar garam serve karo."],
tips:["Patla poha kabhi mat lo — 15 second dhoyega bhi to bhurji ban jayega.","Cheeni optional nahi hai; Indori swaad wahi deti hai.","Bacha poha dobara garam karte waqt 1 tbsp paani chhidak kar dhak do."]},

"masala-dosa":{n:"Masala Dosa",type:"breakfast",tag:"south",time:"30 min + 14 ghante",serves:4,
ing:[["Dosa chawal",2,"cup","Anaj"],["Urad dal",0.5,"cup","Dal"],["Methi dana",1,"tsp","Masale"],["Poha",2,"tbsp","Anaj"],["Aloo (ubla)",500,"g","Sabzi"],["Pyaz",2,"medium","Sabzi"],["Hari mirch",3,"","Sabzi"],["Kadi patta",15,"","Sabzi"],["Adrak",1,"inch","Sabzi"],["Rai",1,"tsp","Masale"],["Chana dal",1,"tsp","Dal"],["Haldi",0.75,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",5,"tbsp","Other"]],
steps:[
"Chawal ko methi dane ke saath aur urad dal ko alag — dono ko 5 ghante paani mein bhigao. Poha bhigone se 30 minute pehle chawal ke saath daal do.",
"Pehle urad dal peeso, thoda-thoda thanda paani daal kar, jab tak jhaag-daar aur bilkul mulayam (fluffy) na ho jaye. Ungli par ragdo — daana feel nahi hona chahiye. Bade bowl mein nikalo.",
"Ab chawal+methi+poha peeso — <b>halka rava jaisa</b> (bilkul smooth nahi). Urad paste mein milao.",
"Haath se 2 minute mix karo (haath ki garmi fermentation shuru karti hai), 1 tsp namak daalo. Batter dhak kar 8–14 ghante warm jagah par rakho jab tak double na ho jaye aur khatti khushboo na aaye. Sardi mein oven ki light on karke andar rakho.",
"Bhaaji: kadhai mein 2 tbsp tel, rai chatka lo, chana dal 30 second (halka sunhera), kadi patta, hari mirch, adrak.",
"Lamba kata pyaz daal kar 4 minute bhooно — narm ho jaye bas, brown nahi. Haldi aur namak daalo, 20 second.",
"Haath se toda hua ubla aloo daalo, 3 tbsp paani chhidko, dhak kar 4 minute dheemi aanch par pakao. Halka mash karo — aadha chunky, aadha mashed. Dhania mila lo.",
"Tawa (nonstick ya cast iron) madhyam-tez par garam karo. Paani ki boond daalo — <b>chhann se udni chahiye</b>, tabhi sahi temperature hai. Ab aanch madhyam karo, kate pyaz se tel lagao, tawa par thoda paani chhidak kar kapde se poonch lo.",
"Ek karchhi batter beech mein daal kar bahar ki taraf gol ghumate hue patla failao. Kinaron par 1 tsp tel.",
"2 minute seko jab tak neeche sunhera-lal aur kinare apne aap uthne na lagein. <b>Palatne ki zaroorat nahi.</b> Beech mein aloo bhaaji rakho, mod kar nikalo. Sambar aur nariyal chutney ke saath."],
tips:["Batter thick lage to sirf 2 tbsp paani daal kar patla karo.","Har dosa ke beech tawa ka temperature giraana zaroori — paani chhidak kar poonchna isi liye hai.","Fermented batter fridge mein 4 din chalta hai."]},

"idli-sambar":{n:"Idli",type:"breakfast",tag:"south",time:"25 min + 12 ghante",serves:4,
ing:[["Idli rava",2,"cup","Anaj"],["Urad dal",0.75,"cup","Dal"],["Methi dana",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Tel (greasing)",1,"tbsp","Other"]],
steps:[
"Urad dal aur methi dana 4 ghante bhigao. Idli rava alag se 30 minute bhigao, phir daba kar extra paani nichod lo.",
"Urad dal ko bahut kam paani (lagbhag 0.75 cup) ke saath ekdum mulayam, halka aur jhaag-daar peeso. Grinder garam na ho — beech-beech mein rukо.",
"Nichoda hua idli rava urad paste mein milao, 1.25 tsp namak daalo, haath se 2 minute phent kar mix karo. Batter gaadha honа chahiye — dosa se motа.",
"Dhak kar 8–12 ghante rakho jab tak batter ubhar kar hawa-daar na ho jaye.",
"Idli stand ke saanche mein tel lagao. Batter bharte waqt <b>hilao mat</b> — hawa nikal jayegi. Saanche 3/4 hi bharo.",
"Steamer mein 2 inch paani ubalne do. Stand rakho, dhakkan band, <b>12 minute tez bhaap</b>. Whistle mat lagao.",
"Gas band karke 5 minute stand andar hi rehne do — turant nikaloge to idli sikud jayegi.",
"Geele chamach se kinare se idli utaro. Sambar aur nariyal chutney ke saath garam serve karo."],
tips:["Batter fridge mein rakha ho to use se 1 ghanta pehle bahar nikalo.","Idli sakht ho rahi hai — matlab urad dal kam ya batter zyada patla.","Bachi idli ko cube karke rai-kadi patta ke tadke mein bhoон lo, best snack."]},

"upma":{n:"Rava Upma",type:"breakfast",tag:"south",time:"25 min",serves:4,
ing:[["Sooji (mota rava)",1.5,"cup","Anaj"],["Pyaz",1,"medium","Sabzi"],["Adrak",1,"inch","Sabzi"],["Hari mirch",2,"","Sabzi"],["Kadi patta",12,"","Sabzi"],["Gajar/matar",0.5,"cup","Sabzi"],["Nimbu",0.5,"","Sabzi"],["Rai",1,"tsp","Masale"],["Chana dal",1,"tbsp","Dal"],["Urad dal",1,"tsp","Dal"],["Namak",null,"","Masale"],["Ghee",2,"tbsp","Dairy"],["Tel",1,"tbsp","Other"],["Kaju",10,"","Other"]],
steps:[
"Sookhi kadhai mein sooji ko madhyam-dheemi aanch par <b>6–7 minute</b> lagatar chalate hue bhoon lo — rang badalna nahi chahiye, bas khushboo aani chahiye aur daane alag-alag lagne chahiye. Nikaal kar alag rakho. Ye step chhodoge to upma lei ban jayega.",
"3.5 cup paani alag bartan mein ubaalne rakho. Paani hamesha ubalta hua chahiye — thanda paani = lumps.",
"Kadhai mein tel + 1 tbsp ghee. Rai chatkao, phir chana dal aur urad dal 40 second tak sunhera hone tak, phir kaju, phir kadi patta, hari mirch, adrak.",
"Pyaz daal kar 3 minute — paardarshi hone tak. Gajar-matar daal kar 3 minute aur.",
"Ubalta paani daalo (dhyan se, chhitein udengi), namak milao, 2 minute ubaalne do.",
"Aanch dheemi karo. Ek haath se sooji <b>dhaar banate hue</b> daalo aur doosre haath se lagataar chalate raho. Ek saath mat undelo.",
"Sooji daalne ke baad 2 minute chalate raho jab tak saara paani soak na ho jaye aur mixture kadhai chhodne na lage.",
"Gas band, 1 tbsp ghee upar se, dhak kar <b>5 minute</b> chhod do — yahi dum upma ko fluffy banata hai.",
"Kaante se halke haath se fluff karo, nimbu nichod kar dhania ke saath serve karo."],
tips:["Paani:sooji ka ratio 1:2.5 rakho — 1:2 se upma sookha lagta hai.","Nariyal chutney ya bas cheeni ke saath — dono authentic hain."]},

"besan-chilla":{n:"Besan Chilla",type:"breakfast",tag:"north",time:"20 min",serves:3,
ing:[["Besan",1.5,"cup","Anaj"],["Pyaz",1,"medium","Sabzi"],["Tamatar",1,"medium","Sabzi"],["Shimla mirch",0.5,"","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Ajwain",0.5,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Lal mirch powder",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",3,"tbsp","Other"]],
steps:[
"Besan ko bowl mein chhano. Haldi, lal mirch, ajwain (masal kar) aur namak milao.",
"Thoda-thoda paani daal kar <b>pehle gaadha paste</b> banao aur gaanth todo. Gaanth toot jaayein tab baaki paani (kul lagbhag 1.25 cup) daal kar patla karo — consistency dosa batter jaisi, thodi gaadhi.",
"Batter ko 10 minute rest do — besan phool jayega aur chilla narm banega.",
"Ab barik kata pyaz, tamatar, shimla mirch, hari mirch, dhania milao. Sabzi pehle daal doge to batter paani chhodega.",
"Nonstick tawa madhyam aanch par garam karo, 0.5 tsp tel laga kar kapde se failao.",
"Ek karchhi batter beech mein daalo aur karchhi ke peeche se gol ghumate hue failao — patla, par dosa jitna patla nahi.",
"Kinaron par 1 tsp tel. 2–3 minute seko jab tak neeche sunhera aur kinare tawa chhodne na lagein.",
"Palat kar 1.5 minute doosri side. Beech mein cheese ya paneer bhurji bhar sakte ho.",
"Hari chutney aur dahi ke saath garam serve karo."],
tips:["Chilla phat raha hai = batter zyada patla, 2 tbsp besan aur daalo.","1 tbsp sooji milane se karara banta hai."]},

"methi-thepla":{n:"Methi Thepla",type:"breakfast",tag:"north",time:"40 min",serves:4,
ing:[["Gehun ka atta",300,"g","Anaj"],["Besan",3,"tbsp","Anaj"],["Methi patta",2,"cup","Sabzi"],["Dahi",0.5,"cup","Dairy"],["Adrak-mirch paste",1,"tbsp","Sabzi"],["Haldi",0.5,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Dhania powder",1,"tsp","Masale"],["Til",1,"tbsp","Masale"],["Namak",null,"","Masale"],["Tel",4,"tbsp","Other"]],
steps:[
"Methi ke patte tod kar 2 baar paani mein dho lo, chalni mein 10 minute sukhao. Barik kaat lo — dandi zyada na aaye, kadwahat aati hai.",
"Bade bartan mein atta, besan, kati methi, haldi, lal mirch, dhania powder, til, adrak-mirch paste, namak aur 1 tbsp tel — sab sookha mix karo.",
"Dahi daal kar mix karo. Ab <b>bahut kam paani</b> (2–4 tbsp) daal kar sakht-narm dough gundho. Methi khud paani chhodti hai, isliye dheere.",
"Dough dhak kar 15 minute rest.",
"14–16 chhote gole banao. Har gole ko sookhe atte mein lapet kar 6 inch patla belo — roti se patla.",
"Tawa madhyam aanch par. Thepla daalo, 30 second, palto.",
"0.5 tsp tel lagao, palto, doosri side par bhi tel. Spatula se daba-daba kar dono side bhoore chitte aane tak seko — 1 minute per side.",
"Thanda hone par hi dabba mein rakho, warna bhaap se geele ho jaayenge. Dahi ya aam ke achar ke saath — safar ke liye 3 din tak theek rehte hain."],
tips:["Methi kadvi lage to kati methi par 0.5 tsp namak laga kar 10 minute chhod do aur nichod lo.","Dahi khatta ho to aur behtar swaad aata hai."]},

"puri-bhaji":{n:"Puri aur Aloo Rasedar",type:"breakfast",tag:"north",time:"45 min",serves:4,
ing:[["Gehun ka atta",350,"g","Anaj"],["Sooji",2,"tbsp","Anaj"],["Aloo (ubla)",600,"g","Sabzi"],["Tamatar",3,"medium","Sabzi"],["Hari mirch",2,"","Sabzi"],["Adrak",1,"inch","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Haldi",0.75,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Amchur",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Tel (talne ke liye)",500,"ml","Other"]],
steps:[
"Puri ka atta: atta + sooji + 0.75 tsp namak + 2 tsp tel. Paani thoda-thoda daal kar <b>sakht dough</b> gundho — roti se kaafi sakht. Narm dough tel pi jaata hai. Dhak kar 20 minute rest.",
"Bhaji: ubale aloo ko haath se tod lo — cube mat kaato, tootey hue aloo gravy pakadte hain.",
"Kadhai mein 3 tbsp tel garam karo. Jeera chatkao, hing daalo, phir kati hari mirch aur adrak — 30 second.",
"Kadduskas/kata tamatar daalo, haldi, dhania powder, lal mirch aur namak. Dhak kar 8 minute madhyam aanch par pakao jab tak tel kinaron par alag na dikhne lage.",
"Tootey aloo daal kar masale mein 2 minute bhooно — aloo par masala chadh jaye.",
"3 cup garam paani daalo, ubaal aane do, phir aanch dheemi karke <b>12 minute</b> pakao. Karchhi se 4–5 aloo ke tukde dabao — gravy apne aap gaadhi ho jayegi.",
"Amchur aur garam masala daal kar 2 minute, dhania se garnish.",
"Puri: dough ke chhote gole, thodi si tel lagi surface par 4 inch belo. Sookha atta mat lagao — tel mein jal kar kala ho jaata hai.",
"Tel ko tez garam karo — dough ka tukda daalo, <b>turant upar aana chahiye</b>. Puri daalo, karchhi se halka dabao, apne aap phool jayegi. Palat kar 20 second, sunheri hone par nikaalo.",
"Tel ki aanch har puri ke beech madhyam-tez rakho. Rasedar aloo ke saath turant serve karo."],
tips:["Puri phool nahi rahi = dough narm hai ya tel thanda hai.","Bhaji ko 10 minute rakhne se swaad aur khulta hai."]},

"moong-cheela":{n:"Moong Dal Cheela",type:"breakfast",tag:"north",time:"25 min + bhigona",serves:3,
ing:[["Moong dal (chilka)",1,"cup","Dal"],["Adrak",1,"inch","Sabzi"],["Hari mirch",2,"","Sabzi"],["Pyaz",1,"medium","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Paneer (bharne ke liye)",100,"g","Dairy"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",3,"tbsp","Other"]],
steps:[
"Moong dal ko 3 baar dho kar 4 ghante (ya raat bhar) bhigao.",
"Paani nikaal kar dal ko adrak, hari mirch aur sirf 3–4 tbsp taaza paani ke saath peeso. Batter gaadha aur halka daanedar rahe — bilkul paste nahi.",
"Batter ko 2 minute chamach se phento — hawa milegi aur cheela narm banega. Namak, jeera, hing aur dhania milao.",
"Nonstick tawa madhyam aanch par garam karo, halka tel lagao.",
"Karchhi bhar batter daal kar gol failao (5–6 inch). Zyada patla mat karo — moong cheela thoda motа hi achha lagta hai.",
"Upar barik pyaz aur crumbled paneer chhidko, halke haath se daba do.",
"Kinaron par tel daal kar 3 minute seko jab tak neeche sunheri-bhoori parat na ban jaye.",
"Palat kar 2 minute. Hari chutney ke saath garam serve karo."],
tips:["Bina chilke wali dhuli moong dal se rang peela aur texture smooth aata hai.","Batter fridge mein 2 din chalta hai."]},

"suji-halwa":{n:"Sooji Halwa",type:"breakfast",tag:"north",time:"25 min",serves:4,
ing:[["Sooji",1,"cup","Anaj"],["Cheeni",0.75,"cup","Masale"],["Ghee",0.75,"cup","Dairy"],["Elaichi powder",0.5,"tsp","Masale"],["Kaju-badam",0.3,"cup","Other"],["Kishmish",2,"tbsp","Other"]],
steps:[
"3 cup paani mein cheeni daal kar ubaalne rakho. Ubaal aate hi aanch bilkul dheemi kar do — chashni garam rehni chahiye.",
"Kadhai mein ghee garam karo, kaju-badam 1 minute bhoon kar nikaal lo.",
"Usi ghee mein sooji daalo. Ab <b>dheemi-madhyam aanch par 10–12 minute</b> lagataar chalao. Sooji ka rang halka sunhera hoga aur ghee alag hone lagega — jaldi mat karo, yahi halwe ka poora swaad hai.",
"Aanch bilkul dheemi karo. Garam cheeni-paani ko <b>dhyan se, thoda-thoda</b> daalo — bahut bhaap uthegi, chehra door rakho.",
"Lagataar chalate raho — 2 minute mein saara paani soak ho jayega aur halwa gaadha ho jayega.",
"Elaichi powder, kishmish aur bhune mewe milao.",
"Dhak kar 3 minute dum do, phir chamach se fluff karke garam serve karo — kaale chane aur puri ke saath ashtami wala combo."],
tips:["Paani:sooji 3:1 se halwa narm banta hai, 2:1 se daanedar.","Cheeni ka paani hamesha garam hi daalo, warna gaanth banegi."]},

"paneer-bhurji":{n:"Paneer Bhurji",type:"breakfast",tag:"north",time:"20 min",serves:3,
ing:[["Paneer",300,"g","Dairy"],["Pyaz",2,"medium","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Shimla mirch",1,"","Sabzi"],["Hari mirch",2,"","Sabzi"],["Adrak-lehsun paste",1,"tbsp","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Jeera",1,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",1,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Kasuri methi",1,"tsp","Masale"],["Namak",null,"","Masale"],["Makkhan",2,"tbsp","Dairy"]],
steps:[
"Paneer ko haath se motа-motа crumble karo — grater se kiya paneer bhurji mein paste ban jaata hai.",
"Kadhai mein makkhan garam karo, jeera chatkao.",
"Barik kata pyaz daal kar 4 minute madhyam aanch par — kinare sunhere hone tak.",
"Adrak-lehsun paste 1 minute, kacchi khushboo jaane tak. Hari mirch aur shimla mirch daal kar 2 minute — shimla mirch thodi crunchy rehni chahiye.",
"Tamatar, haldi, dhania powder, lal mirch aur namak. Dhak kar 5 minute pakao jab tak tamatar gal kar tel na chhod de.",
"Aanch dheemi karo, crumbled paneer daalo aur sirf <b>2 minute</b> mila kar pakao. Zyada pakaoge to paneer rubber ho jayega.",
"Kasuri methi haath par masal kar daalo, garam masala aur dhania.",
"Pav, paratha ya toast ke saath garam serve karo."],
tips:["Paneer taaza na ho to 10 minute garam paani mein daal kar nikaal lo — narm ho jayega.","Namak paneer daalne ke baad hi adjust karo."]},

"semiya-upma":{n:"Semiya Upma",type:"breakfast",tag:"south",time:"25 min",serves:4,
ing:[["Semiya (vermicelli)",2,"cup","Anaj"],["Pyaz",1,"medium","Sabzi"],["Gajar",1,"medium","Sabzi"],["Matar",0.5,"cup","Sabzi"],["Hari mirch",2,"","Sabzi"],["Kadi patta",12,"","Sabzi"],["Nimbu",0.5,"","Sabzi"],["Rai",1,"tsp","Masale"],["Chana dal",1,"tbsp","Dal"],["Urad dal",1,"tsp","Dal"],["Haldi",0.25,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",1,"tbsp","Dairy"],["Tel",2,"tbsp","Other"],["Moongfali",0.25,"cup","Other"]],
steps:[
"Semiya ko 1 tsp ghee mein madhyam aanch par 4 minute bhooно jab tak halka sunhera na ho jaye (roasted semiya ho to skip karo).",
"Kadhai mein tel garam, rai chatkao, chana-urad dal sunheri hone tak, moongfali, kadi patta, hari mirch.",
"Pyaz 3 minute, phir gajar aur matar 3 minute.",
"2.5 cup paani daalo, haldi aur namak, tez ubaal aane do.",
"Bhuni semiya daal kar ek baar hilao, dhakkan lagao, <b>aanch bilkul dheemi karke 6 minute</b> pakao. Baar-baar mat chalao — semiya chipak jayegi.",
"Dhakkan hata kar dekho — paani soak ho gaya ho to gas band, 1 tsp ghee aur nimbu daalo.",
"Dhak kar 4 minute rest, phir kaante se fluff karke serve karo."],
tips:["Paani:semiya 1:1.25 ka ratio sahi rehta hai.","Nariyal chutney best sathi hai."]},

"medu-vada":{n:"Medu Vada",type:"breakfast",tag:"south",time:"35 min + bhigona",serves:4,
ing:[["Urad dal (dhuli)",1.5,"cup","Dal"],["Hari mirch",3,"","Sabzi"],["Adrak",1,"inch","Sabzi"],["Kadi patta",15,"","Sabzi"],["Kali mirch (khadi)",1,"tsp","Masale"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Namak",null,"","Masale"],["Tel (talne ke liye)",500,"ml","Other"]],
steps:[
"Urad dal ko 4 ghante bhigao. Paani poori tarah nikaal do — geeli dal ka batter kabhi nahi jamta.",
"Grinder mein dal ko <b>bilkul kam paani</b> (2–3 tbsp, ek baar mein 1 tbsp) ke saath peeso. Batter ekdum smooth aur gaadha ho — chamach par tikna chahiye.",
"Batter ko haath se ya chamach se 3–4 minute ek hi disha mein phento jab tak hawa-daar na ho jaye. Test: paani ke katore mein batter ki choti boond daalo, <b>tairni chahiye</b>. Na taire to aur phento.",
"Ab kati hari mirch, adrak, kadi patta, kuti kali mirch, jeera, hing aur namak milao. Namak pehle daaloge to batter paani chhodega.",
"Tel madhyam-tez garam karo (180°C). Batter ki boond daalne par dheere se upar aani chahiye, turant bhoori nahi honi chahiye.",
"Hatheli ya plastic sheet geela karo, thoda batter rakho, thapki se gol karo aur angoothe se beech mein chhed banao.",
"Vada ko dhyan se tel mein sarkao. 3–4 vade ek saath, kadhai bharо mat.",
"Madhyam aanch par 5–6 minute palat-palat kar talo jab tak sunhera-bhoora aur karara na ho jaye. Tez aanch par bahar jal jayega, andar kaccha rahega.",
"Tissue par nikaalo. Sambar aur nariyal chutney ke saath turant serve karo."],
tips:["Batter patla ho gaya to 2 tbsp chawal ka aata mila do.","Geele haath = vada chipkega nahi."]},

/* ---------------- DALS & MAINS ---------------- */
"dal-tadka":{n:"Dal Tadka",type:"main",tag:"north",time:"35 min",serves:4,
ing:[["Arhar dal",1,"cup","Dal"],["Pyaz",1,"medium","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Lehsun",8,"kali","Sabzi"],["Adrak",1,"inch","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Haldi",0.75,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Dhania powder",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Kashmiri mirch (tadka)",1,"tsp","Masale"],["Sookhi lal mirch",2,"","Masale"],["Namak",null,"","Masale"],["Ghee",3,"tbsp","Dairy"],["Nimbu",0.5,"","Sabzi"]],
steps:[
"Dal ko 3 baar dho kar 20 minute bhigao — pakne ka time aadha ho jayega aur dal creamy banegi.",
"Cooker mein dal, 3 cup paani, haldi, 0.5 tsp namak aur 0.5 tsp tel (jhaag nahi banega) daal kar madhyam aanch par <b>3 seeti</b> lagao. Pressure apne aap utarne do.",
"Dhakkan khol kar dal ko karchhi se halka mathhо — thodi mashed, thodi sabut. Agar gaadhi ho to garam paani milao.",
"Tadka: kadhai mein 3 tbsp ghee garam karo. Jeera chatkao, hing daalo.",
"Barik kata lehsun daalo aur <b>halka sunhera</b> hone tak bhooно — 40 second. Zyada bhoora = kadwa.",
"Barik kata pyaz, adrak aur hari mirch daal kar 4 minute, kinare sunhere hone tak.",
"Tamatar, lal mirch powder, dhania powder aur namak. Dhak kar 6 minute madhyam aanch par pakao jab tak masala tel na chhod de — yahi asli test hai.",
"Ye tadka dal mein daalo (ya dal tadke mein), mila kar dheemi aanch par <b>7 minute</b> khadkne do. Is time mein dal masala pi leti hai.",
"Garam masala aur dhania milao, nimbu nichodo.",
"Final tadka (dhaba style): choti kadhai mein 1 tbsp ghee, 2 sookhi lal mirch aur 1 tsp Kashmiri mirch — 10 second, aur seedha dal ke upar undel do. Turant dhak do taki khushboo band rahe. Jeera rice ya roti ke saath."],
tips:["Dal cooker mein hi mathni se mathoge to restaurant jaisi creamy banti hai.","Tamatar khatte na ho to 0.5 tsp amchur daal do."]},

"dal-makhani":{n:"Dal Makhani",type:"main",tag:"north",time:"1 ghanta 15 min",serves:4,
ing:[["Sabut urad dal",1,"cup","Dal"],["Rajma",0.25,"cup","Dal"],["Pyaz",2,"medium","Sabzi"],["Tamatar (puree)",4,"medium","Sabzi"],["Adrak-lehsun paste",2,"tbsp","Sabzi"],["Hari mirch",2,"","Sabzi"],["Lal mirch powder",1.5,"tsp","Masale"],["Dhania powder",1,"tsp","Masale"],["Garam masala",1,"tsp","Masale"],["Kasuri methi",1,"tbsp","Masale"],["Namak",null,"","Masale"],["Makkhan",5,"tbsp","Dairy"],["Cream",0.3,"cup","Dairy"]],
steps:[
"Urad dal aur rajma ko raat bhar (kam se kam 8 ghante) bhigao. Ye shortcut nahi ho sakta.",
"Cooker mein 4 cup paani, 1 tsp namak ke saath madhyam aanch par <b>7–8 seeti</b>. Dal ungli se dabane par bilkul ghul jani chahiye. Kam pakі dal makhani kabhi creamy nahi hogi.",
"Kadhai mein 3 tbsp makkhan, barik kata pyaz daal kar 8 minute madhyam aanch par sunhera-bhoora karo.",
"Adrak-lehsun paste 90 second, kacchi smell jaane tak.",
"Tamatar puree, lal mirch, dhania powder aur namak. <b>10–12 minute</b> pakao jab tak masala gaadha ho kar kinaron se makkhan na chhode.",
"Pakі dal ko apne paani samet masale mein daalo. Karchhi se dal ke 1/3 hisse ko kadhai ki deewar par daba-daba kar mash karo — isse gaadhapan aata hai, cream se nahi.",
"Ab aanch bilkul dheemi karke <b>35–45 minute dheere-dheere pakao</b>, har 5 minute mein chalate raho taki neeche na lage. Rang dheere-dheere gehra bhoora hoga. Yahi dal makhani ka poora raaz hai.",
"Zaroorat ho to garam paani milate raho — dal gaadhi honi chahiye, sookhi nahi.",
"Kasuri methi haath par masal kar daalo, garam masala, 2 tbsp makkhan aur cream milao. 5 minute aur.",
"Upar se cream ki lakeer aur makkhan ki tikiya daal kar naan ya jeera rice ke saath serve karo."],
tips:["Agle din dal makhani aur behtar lagti hai.","Dhungar chaho to koyle ka tukda garam karke katori mein rakho, ghee daal kar 2 minute dhak do."]},

"chana-masala":{n:"Chana Masala",type:"main",tag:"north",time:"50 min + bhigona",serves:4,
ing:[["Kabuli chana",1.5,"cup","Dal"],["Pyaz",3,"medium","Sabzi"],["Tamatar",4,"medium","Sabzi"],["Adrak-lehsun paste",2,"tbsp","Sabzi"],["Hari mirch",2,"","Sabzi"],["Chai patti (potli)",1,"tsp","Other"],["Tej patta",2,"","Masale"],["Jeera",1,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1.5,"tsp","Masale"],["Chana masala",2,"tsp","Masale"],["Amchur",1,"tsp","Masale"],["Anardana powder",1,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",4,"tbsp","Other"]],
steps:[
"Chane ko 1 tsp namak wale paani mein <b>8–10 ghante</b> bhigao. Paani chane se 3 inch upar rahe.",
"Cooker mein bhige chane, 4 cup taaza paani, 1 tsp namak, tej patta aur chai patti ki potli (muslin/tea bag) daalo. Chai patti hi chane ko wo gehra rang deti hai, bina kisi rang ke.",
"Madhyam aanch par <b>5–6 seeti</b>, phir 10 minute dheemi aanch par. Chana do ungli ke beech aasani se dabna chahiye. Potli nikaal do. Ubla paani <b>fenkna mat</b> — gravy usi se banegi.",
"Kadhai mein 4 tbsp tel garam karo, jeera chatkao.",
"Barik kata pyaz daalo aur 10 minute madhyam aanch par asli sunhera-bhoora karo. Jaldi ki to gravy ka rang aur meethapan dono nahi aayega.",
"Adrak-lehsun paste 90 second. Hari mirch daalo.",
"Pisa tamatar, haldi, dhania powder, lal mirch aur namak. Dhak kar 10 minute pakao jab tak masala gaadha ho kar tel alag na ho jaye.",
"Pake chane daal kar masale mein 3 minute bhooно — har chane par masala chadhe.",
"2 cup bacha hua chane ka paani daalo. Chane ke 1/4 hisse ko karchhi se daba do — gravy apne aap gaadhi hogi.",
"Dhak kar dheemi aanch par <b>15 minute</b> pakao. Chana masala, amchur aur anardana powder daal kar 5 minute aur. Kate pyaz, nimbu aur bhature/chawal ke saath."],
tips:["Chana jaldi galane ke liye bhigote waqt 0.5 tsp meetha soda daalo.","Anardana asli khattapan deta hai — amchur se behtar."]},

"rajma":{n:"Rajma Masala",type:"main",tag:"north",time:"1 ghanta + bhigona",serves:4,
ing:[["Rajma",1.5,"cup","Dal"],["Pyaz",3,"medium","Sabzi"],["Tamatar",4,"medium","Sabzi"],["Adrak-lehsun paste",2,"tbsp","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Tej patta",2,"","Masale"],["Badi elaichi",1,"","Masale"],["Jeera",1,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1.5,"tsp","Masale"],["Garam masala",1,"tsp","Masale"],["Kasuri methi",1,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",3,"tbsp","Dairy"]],
steps:[
"Rajma ko 8–10 ghante bhigao. Bhigoya hua paani fenk do (isi se gas banti hai), taaza paani lo.",
"Cooker mein rajma, 4 cup paani, tej patta, badi elaichi aur 1 tsp namak. <b>6–7 seeti</b> madhyam aanch par, phir 10 minute dheemi. Rajma ungli se dabane par poora mash hona chahiye — ye zaroori hai.",
"Kadhai mein ghee garam karo, jeera chatkao.",
"Pisa ya bahut barik kata pyaz daal kar <b>10–12 minute</b> gehra sunhera karo. Rajma ki poori gravy isi par tiki hai.",
"Adrak-lehsun paste 2 minute, jab tak kacchapan na chala jaye.",
"Pisa tamatar, haldi, dhania powder, lal mirch aur namak. Dhak kar 10–12 minute pakao jab tak kinaron par ghee alag na dikhne lage.",
"Pake rajma ko paani samet daalo. 1/2 cup rajma alag katori mein nikaal kar mash karo aur wapas daal do — gravy gaadhi aur malaidaar ho jayegi.",
"Dhak kar dheemi aanch par <b>20 minute</b> pakao, beech-beech mein chalao. Gravy tel chhodne lage tab samjho ban gayi.",
"Kasuri methi masal kar, garam masala aur hara dhania. 3 minute aur.",
"Sade chawal ke saath, upar se thoda ghee — classic rajma chawal."],
tips:["Purana rajma 12 ghante bhi bhigoya jaye to kam galta hai — taaza stock lo.","Kashmiri rajma chhota hota hai, jaldi galta hai."]},

"kadhi-pakora":{n:"Kadhi Pakora",type:"main",tag:"north",time:"50 min",serves:4,
ing:[["Besan (kadhi)",0.75,"cup","Anaj"],["Besan (pakore)",1,"cup","Anaj"],["Khatta dahi",1.5,"cup","Dairy"],["Pyaz",2,"medium","Sabzi"],["Hari mirch",2,"","Sabzi"],["Adrak",1,"inch","Sabzi"],["Kadi patta",12,"","Sabzi"],["Methi dana",0.5,"tsp","Masale"],["Rai",1,"tsp","Masale"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Haldi",1,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Sookhi lal mirch",3,"","Masale"],["Dhaniya powder",1,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",300,"ml","Other"],["Ghee",2,"tbsp","Dairy"]],
steps:[
"Bade bartan mein 0.75 cup besan aur dahi ko <b>bina paani ke</b> pehle phento — ekdum smooth hone tak. Yahi gaanth-free kadhi ka tareeka hai.",
"Ab 5 cup paani, haldi, lal mirch aur namak daal kar dobara phento. Chalni se chhan lo — extra safety.",
"Bade bhagone mein 2 tbsp tel garam karo. Methi dana daalo (10 second, bhoora na ho), phir rai, jeera, hing, kadi patta.",
"Ghol daalo aur tez aanch par <b>lagataar chalate hue</b> ubaal laao — ubaal aane tak chalana band mat karo, warna dahi phat jayega.",
"Ubaal aate hi aanch bilkul dheemi karo aur <b>35–40 minute</b> bina dhakke pakao, har 4–5 minute chalate raho. Kadhi gaadhi hogi aur besan ka kacchapan khatam hoga.",
"Pakore: 1 cup besan, kata pyaz, hari mirch, 0.5 tsp ajwain, namak aur bahut kam paani (3–4 tbsp) se gaadha ghol banao. 2 minute phento.",
"Tel madhyam garam karo, chamach se choti pakodiyaan daalo, 4 minute sunhera hone tak talo. Tissue par nikaalo.",
"Pakore ko kadhi mein <b>serve karne se 10 minute pehle</b> daalo — pehle daaloge to ghul jaayenge.",
"Tadka: ghee mein sookhi lal mirch aur 1 tsp Kashmiri mirch 10 second, kadhi ke upar undelo.",
"Sade chawal ke saath garam serve karo."],
tips:["Dahi jitna khatta, kadhi utni achhi.","Kadhi patli lage to 10 minute aur pakao, besan mat daalo."]},

"paneer-butter-masala":{n:"Paneer Butter Masala",type:"main",tag:"north",time:"45 min",serves:4,
ing:[["Paneer",400,"g","Dairy"],["Tamatar",6,"medium","Sabzi"],["Pyaz",2,"medium","Sabzi"],["Kaju",20,"","Other"],["Adrak",1,"inch","Sabzi"],["Lehsun",6,"kali","Sabzi"],["Sookhi Kashmiri mirch",4,"","Masale"],["Tej patta",1,"","Masale"],["Dalchini",1,"inch","Masale"],["Laung",3,"","Masale"],["Elaichi",3,"","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Garam masala",0.75,"tsp","Masale"],["Kasuri methi",1,"tbsp","Masale"],["Cheeni",1,"tsp","Masale"],["Namak",null,"","Masale"],["Makkhan",5,"tbsp","Dairy"],["Cream",0.3,"cup","Dairy"]],
steps:[
"Paneer ko 1 inch cube kaat kar garam (ubalte nahi) paani mein 10 minute daal do. Narm aur ras-bhara rahega.",
"Bhagone mein 2 tbsp makkhan, tej patta, dalchini, laung, elaichi — 30 second.",
"Motа kata pyaz, adrak, lehsun aur kaju daal kar 5 minute bhooно. Pyaz ko brown mat karo — gravy ka rang laal chahiye, bhoora nahi.",
"Char-char tukdon mein kate tamatar aur bhigoyi Kashmiri mirch daalo, 1 cup paani, dhak kar <b>15 minute</b> pakao jab tak tamatar bilkul gal na jaayein.",
"Thanda karo, khade masale (tej patta, dalchini, laung) nikaal do, aur mixer mein <b>bilkul silky</b> peeso — 2 minute chalao, jaldi mat karo.",
"Paste ko chalni se chhano aur karchhi se daba-daba kar poora nikalo. Ye chhanna hi restaurant-jaisa texture deta hai. Chhilka fenk do.",
"Kadhai mein 3 tbsp makkhan garam karo, chhani gravy daalo — chhitein udengi, dhakkan aadha rakho. Dheemi aanch par <b>12 minute</b> pakao jab tak gravy gaadhi ho kar makkhan alag na dikhe.",
"Lal mirch powder, namak, 1 tsp cheeni (tamatar ka khattapan balance karne ke liye) aur zaroorat ho to 0.5 cup garam paani.",
"Paneer cube daal kar dheemi aanch par sirf <b>5 minute</b>. Kasuri methi haath par masal kar, garam masala aur cream milao.",
"Gas band karke 5 minute dhak do, phir naan ya laccha paratha ke saath serve karo."],
tips:["Kaju na ho to 2 tbsp malai use karo.","Gravy zyada khatti lage to 1 tbsp makkhan aur daalo — cheeni nahi."]},

"palak-paneer":{n:"Palak Paneer",type:"main",tag:"north",time:"40 min",serves:4,
ing:[["Palak",500,"g","Sabzi"],["Paneer",300,"g","Dairy"],["Pyaz",2,"medium","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Hari mirch",2,"","Sabzi"],["Adrak-lehsun paste",1.5,"tbsp","Sabzi"],["Jeera",1,"tsp","Masale"],["Haldi",0.25,"tsp","Masale"],["Dhania powder",1,"tsp","Masale"],["Lal mirch powder",0.75,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Kasuri methi",1,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",3,"tbsp","Dairy"],["Cream",2,"tbsp","Dairy"]],
steps:[
"Palak ke patte tod kar 3 baar paani mein dho lo — mitti poori nikalni chahiye.",
"Bade bartan mein paani ubaalo, palak daal kar <b>sirf 2 minute</b> blanch karo.",
"Turant chhan kar barf ke thande paani mein daalo — 1 minute. Ye shock hi palak ka gehra hara rang bachata hai. Zyada ubaalne se rang kaala pad jaata hai.",
"Nichoda hua palak, 1 hari mirch aur 2 tbsp paani ke saath peeso — <b>thoda daanedar</b> rakho, bilkul paste nahi.",
"Kadhai mein 2 tbsp ghee, jeera chatkao, barik kata pyaz 5 minute halka sunhera.",
"Adrak-lehsun paste 90 second, phir kata tamatar, haldi, dhania powder, lal mirch aur namak. 7 minute pakao jab tak ghee alag na ho.",
"Palak puree daalo. Ab <b>sirf 6–7 minute</b> dheemi aanch par pakao — zyada pakaoge to rang chala jayega.",
"Paneer cube daalo (chaho to pehle 1 tbsp ghee mein halka sunhera kar lo), 3 minute.",
"Kasuri methi masal kar, garam masala aur cream. Gas band.",
"Roti ya jeera rice ke saath, upar se cream aur thoda makkhan."],
tips:["Palak puree ko thanda hone ke baad hi peeso, warna rang badalta hai.","Dhakkan mat lagao palak pakate waqt — bhaap rang kharab karti hai."]},

"aloo-gobhi":{n:"Aloo Gobhi",type:"main",tag:"north",time:"35 min",serves:4,
ing:[["Gobhi",1,"medium","Sabzi"],["Aloo",3,"medium","Sabzi"],["Pyaz",1,"medium","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Adrak",1,"inch","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Haldi",0.75,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Amchur",0.75,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",4,"tbsp","Other"]],
steps:[
"Gobhi ko madhyam phool (florets) mein kaat kar garam namak-paani mein 10 minute daal do, phir chhan kar <b>poori tarah sukhao</b>. Geeli gobhi bhaap mein gal jaati hai, bhunegi nahi.",
"Aloo ko chhilke ke saath ya bina, 1 inch cube kaato.",
"Kadhai mein 2 tbsp tel tez garam karo. Gobhi daal kar tez aanch par 5 minute bhooно jab tak kinaron par sunhere-bhoore dhabbe na aa jaayein. Nikaal lo. Ye bhunai hi swaad ka fark hai.",
"Usi kadhai mein aloo 5 minute isi tarah bhooно, nikaal lo.",
"Bache tel mein jeera chatkao, hing, kata pyaz 3 minute, phir adrak aur hari mirch.",
"Tamatar, haldi, dhania powder, lal mirch aur namak. 6 minute jab tak tel alag na ho.",
"Bhuni gobhi aur aloo wapas daalo, masale mein halke haath se mix karo — tod mat do.",
"Dhak kar <b>dheemi aanch par 10–12 minute</b>, har 3 minute mein halka hilao. Paani bilkul mat daalo — bhaap kaafi hai.",
"Kanta aloo mein aar-paar ho jaye to amchur aur garam masala daalo, 2 minute khula pakao.",
"Hara dhania daal kar phulke ke saath serve karo."],
tips:["Sookhi sabzi chahiye to dhakkan aakhri 4 minute hata do.","Gobhi ke kaante wale dandi wale hisse bhi kaam aate hain — fenko mat."]},

"bhindi-masala":{n:"Bhindi Masala",type:"main",tag:"north",time:"30 min",serves:4,
ing:[["Bhindi",500,"g","Sabzi"],["Pyaz",2,"medium","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Hari mirch",2,"","Sabzi"],["Adrak-lehsun paste",1,"tbsp","Sabzi"],["Jeera",1,"tsp","Masale"],["Saunf",0.5,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Amchur",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",4,"tbsp","Other"]],
steps:[
"Bhindi ko dho kar <b>kapde se ek-ek karke poori tarah pochho</b> aur 20 minute hawa mein sukhao. Ek bhi boond paani = lasleса bhindi.",
"Sookhi bhindi ke sir-poonch kaat kar 1 inch tukde karo. Chaku bhi sookha hona chahiye.",
"Kadhai mein 3 tbsp tel tez garam karo. Bhindi daal kar <b>tez aanch par 8–10 minute</b> bhooно. Shuru ke 4 minute bilkul mat chalao — bas kadhai hilao. Lasleсapan jal kar khatam ho jayega.",
"Bhindi ke kinare sunhere hone par nikaal kar alag rakho.",
"Bache tel mein jeera aur saunf chatkao, lamba kata pyaz 4 minute tak halka sunhera.",
"Adrak-lehsun paste 1 minute, hari mirch daalo.",
"Kata tamatar, haldi, dhania powder, lal mirch, namak — 5 minute khuli aanch par, tamatar gal jaye par bilkul paste na bane.",
"Bhindi wapas daalo, halke haath se mix karo, <b>bina dhake</b> 4 minute pakao. Dhakoge to bhaap se bhindi phir lasleси ho jayegi.",
"Amchur aur garam masala daal kar 1 minute. Roti ke saath serve karo."],
tips:["Bhindi kharidte waqt poonch todo — chatak jaye to taaza hai.","Nimbu ki 2 boond bhi lasleсapan katti hai."]},

"baingan-bharta":{n:"Baingan Bharta",type:"main",tag:"north",time:"45 min",serves:4,
ing:[["Bada baingan",1,"","Sabzi"],["Pyaz",3,"medium","Sabzi"],["Tamatar",3,"medium","Sabzi"],["Hari mirch",3,"","Sabzi"],["Adrak-lehsun paste",1.5,"tbsp","Sabzi"],["Hara dhania",0.3,"cup","Sabzi"],["Jeera",1,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Sarson tel",4,"tbsp","Other"]],
steps:[
"Baingan par chaku se 5–6 chhed karo, poore par tel malo aur 2 lehsun ki kaliyan cheeron mein ghusa do.",
"Seedha gas ki flame par rakho. <b>15–18 minute</b> palat-palat kar bhoonо jab tak chhilka jal kar kaala na ho jaye aur baingan pichak kar narm na pad jaye. Chaku andar aasani se jaana chahiye. Yahi smoky swaad bharte ki jaan hai.",
"Thanda hone do, phir haath se jala chhilka utaro. Paani mein mat dhoyo — poora smoke dhul jayega. Kaale tukde thode reh jaayein to theek hai.",
"Gudde ko kaante se mash karo — thoda chunky rakho.",
"Kadhai mein sarson tel dhuan uthne tak garam karo, phir aanch dheemi karke 30 second — kacchapan chala jayega.",
"Jeera chatkao, barik kata pyaz daal kar <b>8 minute</b> sunhera-bhoora karo.",
"Adrak-lehsun paste 90 second, kati hari mirch daalo.",
"Tamatar, haldi, dhania powder, lal mirch aur namak. 8 minute pakao jab tak tel alag na dikhe.",
"Mashed baingan daal kar <b>khuli aanch par 10 minute</b> bhooно, chalate raho — extra paani udega aur masala baingan mein utar jayega.",
"Garam masala aur mutthi bhar hara dhania. Bajre ki roti ya phulke ke saath, upar se kacchа sarson tel ki chhota chhidkav."],
tips:["Gas na ho to oven mein 230°C par 40 minute, par smoky flavour kam aayega.","Baingan halka ho aur chamakdar ho — beej kam honge."]},

"matar-paneer":{n:"Matar Paneer",type:"main",tag:"north",time:"35 min",serves:4,
ing:[["Paneer",300,"g","Dairy"],["Hari matar",1.5,"cup","Sabzi"],["Pyaz",2,"medium","Sabzi"],["Tamatar",3,"medium","Sabzi"],["Kaju",12,"","Other"],["Adrak-lehsun paste",1.5,"tbsp","Sabzi"],["Hari mirch",2,"","Sabzi"],["Jeera",1,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Garam masala",0.75,"tsp","Masale"],["Kasuri methi",1,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",3,"tbsp","Other"],["Cream",2,"tbsp","Dairy"]],
steps:[
"Kaju ko 15 minute garam paani mein bhigao, phir pyaz ke saath peeso (motа kata pyaz + kaju + 3 tbsp paani).",
"Tamatar alag se peeso — dono paste alag rakhne se rang aur texture behtar aata hai.",
"Kadhai mein tel garam karo, jeera chatkao.",
"Pyaz-kaju paste daalo. <b>Chhitein bahut udengi</b>, dhakkan aadha rakho. 8 minute madhyam aanch par pakao jab tak paste gaadha ho kar kinare chhodne na lage.",
"Adrak-lehsun paste 90 second.",
"Tamatar paste, haldi, dhania powder, lal mirch aur namak. Dhak kar 8 minute — tel kinaron par alag dikhna chahiye.",
"Matar aur 1.5 cup garam paani daalo. Dhak kar 8 minute (taaza matar) ya 5 minute (frozen) pakao jab tak matar narm na ho.",
"Paneer cube daal kar dheemi aanch par sirf 4 minute. Zyada nahi.",
"Kasuri methi masal kar, garam masala aur cream. 2 minute rest.",
"Roti ya pulao ke saath serve karo."],
tips:["Frozen matar ho to seedha daalo, pehle na ubaalo.","Paneer fry karna hai to halka golden — zyada karne se sakht ho jaata hai."]},

"lauki-chana-dal":{n:"Lauki Chana Dal",type:"main",tag:"north",time:"35 min",serves:4,
ing:[["Chana dal",0.75,"cup","Dal"],["Lauki",500,"g","Sabzi"],["Pyaz",1,"medium","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Adrak",1,"inch","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Haldi",0.75,"tsp","Masale"],["Dhania powder",1.5,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",3,"tbsp","Dairy"]],
steps:[
"Chana dal ko dho kar 1 ghanta bhigao — nahi bhigoge to lauki gal jayegi aur dal kacchi rahegi.",
"Lauki chheel kar 1 inch cube kaato, beej wala narm hissa nikaal do agar zyada pakа ho.",
"Cooker mein ghee garam karo, jeera chatkao, hing daalo.",
"Kata pyaz 4 minute, phir adrak aur hari mirch 30 second.",
"Tamatar, haldi, dhania powder, lal mirch aur namak. 5 minute jab tak tel alag na ho.",
"Bhigi chana dal daal kar 2 minute bhooно — masala dal par chadh jaye.",
"Lauki daalo, 1 minute mix karo, phir 1.5 cup paani. Lauki khud paani chhodti hai isliye kam paani.",
"Dhakkan band, madhyam aanch par <b>3 seeti</b>. Pressure apne aap utarne do.",
"Kholo, garam masala aur dhania milao. Agar patli lage to 3 minute khuli aanch par sukhao.",
"Roti ya chawal ke saath — halka aur ghar jaisa khana."],
tips:["Lauki kadwi lage to phenk do, chakh kar hi use karo.","Ghee ka tadka ghar wali dal ko restaurant jaisa banata hai."]},

"kadai-paneer":{n:"Kadai Paneer",type:"main",tag:"north",time:"35 min",serves:4,
ing:[["Paneer",400,"g","Dairy"],["Shimla mirch",2,"","Sabzi"],["Pyaz",2,"medium","Sabzi"],["Tamatar",4,"medium","Sabzi"],["Adrak",1,"inch","Sabzi"],["Lehsun",6,"kali","Sabzi"],["Sabut dhania",2,"tbsp","Masale"],["Sookhi Kashmiri mirch",4,"","Masale"],["Kali mirch",0.5,"tsp","Masale"],["Saunf",0.5,"tsp","Masale"],["Haldi",0.25,"tsp","Masale"],["Kasuri methi",1,"tbsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",4,"tbsp","Dairy"],["Cream",2,"tbsp","Dairy"]],
steps:[
"Kadai masala: sookhi kadhai mein sabut dhania, sookhi lal mirch, kali mirch aur saunf ko dheemi aanch par <b>3 minute</b> bhooно jab tak khushboo na uthe. Thanda karke motа-motа kuto — powder nahi, dardara. Yahi dish ki asli pehchaan hai.",
"Paneer aur shimla mirch ko 1 inch chaukor kaato. Pyaz ki ek petal-style kaat lo (layers alag).",
"Kadhai mein 1 tbsp ghee garam karo, shimla mirch aur petal pyaz ko tez aanch par <b>2 minute</b> bhooно — crunchy rehni chahiye. Nikaal lo.",
"Usi kadhai mein 3 tbsp ghee, kuta adrak-lehsun 1 minute.",
"Barik kata tamatar (ya dardara pisa), haldi aur namak daal kar dhak kar 10 minute pakao jab tak gravy gaadhi ho kar ghee na chhode.",
"Adha kadai masala daal kar 2 minute bhooно.",
"Paneer cube daal kar halke haath se mix karo, 0.5 cup garam paani, dheemi aanch par 4 minute.",
"Bhuni shimla mirch aur pyaz wapas daalo, bacha kadai masala chhidko.",
"Kasuri methi masal kar, garam masala aur cream. 2 minute dhak do.",
"Tandoori roti ya laccha paratha ke saath."],
tips:["Kadai masala ek baar bana kar 1 mahine ka rakh sakte ho.","Shimla mirch ko zyada mat pakao — crunch hi dish banati hai."]},

"chole":{n:"Pindi Chole (sookhe)",type:"main",tag:"north",time:"45 min + bhigona",serves:4,
ing:[["Kabuli chana",1.5,"cup","Dal"],["Pyaz",2,"medium","Sabzi"],["Adrak",2,"inch","Sabzi"],["Hari mirch",3,"","Sabzi"],["Chai patti (potli)",1,"tsp","Other"],["Tej patta",2,"","Masale"],["Jeera",1,"tsp","Masale"],["Ajwain",0.5,"tsp","Masale"],["Anardana powder",2,"tsp","Masale"],["Amchur",1,"tsp","Masale"],["Chana masala",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Kali mirch",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",4,"tbsp","Other"]],
steps:[
"Chane raat bhar bhigao. Cooker mein 4 cup paani, namak, tej patta aur chai patti potli ke saath 5–6 seeti. Chana narm par sabut rehna chahiye.",
"Potli nikaalo, chane chhan lo par <b>1 cup paani bacha kar rakho</b>.",
"Kadhai mein tel garam karo, jeera aur ajwain chatkao.",
"Barik kata pyaz 8 minute gehra sunhera karo.",
"Kata adrak aur hari mirch 1 minute.",
"Aanch dheemi karo, anardana powder, chana masala, lal mirch, kali mirch aur amchur daal kar sirf <b>30 second</b> bhooно — powder masale jaldi jalte hain.",
"Chane daal kar 4 minute achhi tarah mix karo, chamach se thode chane dabao.",
"Bacha paani daal kar khuli aanch par 10 minute pakao jab tak masala chane par chipak na jaye aur plate mein gravy na bahe. Pindi chole sookhe hote hain.",
"Upar se adrak ki barik lambi katran, hari mirch aur nimbu.",
"Bhature, kulche ya sade chawal ke saath serve karo."],
tips:["Anardana powder ke bina asli Pindi swaad nahi aayega.","Chai patti ki jagah 1 tea bag bhi chalega."]},

"mix-veg":{n:"Mix Veg",type:"main",tag:"north",time:"35 min",serves:4,
ing:[["Gajar",2,"medium","Sabzi"],["French beans",100,"g","Sabzi"],["Gobhi",0.5,"","Sabzi"],["Matar",0.75,"cup","Sabzi"],["Aloo",2,"medium","Sabzi"],["Shimla mirch",1,"","Sabzi"],["Pyaz",2,"medium","Sabzi"],["Tamatar",3,"medium","Sabzi"],["Adrak-lehsun paste",1.5,"tbsp","Sabzi"],["Jeera",1,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Kasuri methi",1,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",4,"tbsp","Other"],["Cream",2,"tbsp","Dairy"]],
steps:[
"Sabhi sabziyon ko <b>ek jaise size</b> mein kaato — barabar pakengi. Gajar aur beans thode patle, gobhi aur aloo thode bade.",
"Aloo, gajar, beans aur gobhi ko namak wale ubalte paani mein 4 minute blanch karo, phir thande paani mein daal do. Rang aur crunch dono bache rahenge.",
"Kadhai mein 2 tbsp tel garam karo, blanched sabziyan tez aanch par 4 minute bhooно, nikaal lo.",
"Bache tel mein jeera chatkao, barik kata pyaz 6 minute sunhera.",
"Adrak-lehsun paste 90 second.",
"Pisa tamatar, haldi, dhania powder, lal mirch aur namak. Dhak kar 8 minute jab tak tel alag na ho.",
"Bhuni sabziyan, matar aur shimla mirch daalo. 0.5 cup garam paani.",
"Dhak kar dheemi aanch par <b>8 minute</b> — sabzi narm par toot-phoot na ho.",
"Kasuri methi masal kar, garam masala aur cream. 2 minute.",
"Roti ya pulao ke saath."],
tips:["Blanching skip karoge to gobhi gal jayegi aur gajar kacchi rahegi.","Paneer ya kaju bhi 5 minute pehle daal sakte ho."]},

"jeera-aloo":{n:"Jeera Aloo",type:"main",tag:"north",time:"20 min",serves:4,
ing:[["Aloo (ubla)",600,"g","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Jeera",2,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Dhania powder",1,"tsp","Masale"],["Amchur",1,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",3,"tbsp","Dairy"]],
steps:[
"Aloo ko cooker mein 2 seeti (bilkul gala nahi chahiye), thanda karke chhilka utaar kar 1 inch cube kaato. Thande aloo hi cube rehte hain.",
"Kadhai mein ghee garam karo. Jeera daalo aur <b>chatakne ke baad 10 second aur</b> bhoon lo — gehra rang aur khushboo aayegi.",
"Hing aur cheeri hui hari mirch, 20 second.",
"Aanch dheemi karo, haldi, lal mirch aur dhania powder daal kar 15 second — ghee mein masale khil jaayenge.",
"Aloo cube aur namak daalo. Halke haath se mix karo taki har cube par masala lage.",
"Aanch madhyam-tez karo aur <b>8 minute bina dhake</b> pakao, har 2 minute mein palto. Kuch kinare karare-sunhere hone chahiye.",
"Amchur chhidko, 1 minute.",
"Hara dhania daal kar poori, paratha ya dal-chawal ke saath serve karo."],
tips:["Dhakkan lagaoge to aloo bhaap mein narm ho jaayega, karara nahi.","Nonstick ki jagah lohe ki kadhai behtar crust deti hai."]},

"aloo-matar":{n:"Aloo Matar",type:"main",tag:"north",time:"30 min",serves:4,
ing:[["Aloo",4,"medium","Sabzi"],["Hari matar",1.5,"cup","Sabzi"],["Pyaz",2,"medium","Sabzi"],["Tamatar",3,"medium","Sabzi"],["Adrak-lehsun paste",1,"tbsp","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",3,"tbsp","Other"]],
steps:[
"Aloo ko chheel kar 1 inch cube kaato aur 5 minute paani mein daal do (starch nikal jayega), phir sukha lo.",
"Kadhai mein tel garam karo, aloo cube 5 minute tez aanch par bhooно jab tak kinare sunhere na hon. Nikaal lo.",
"Usi tel mein jeera chatkao, hing.",
"Barik kata pyaz 5 minute sunhera, phir adrak-lehsun paste 1 minute.",
"Pisa tamatar, haldi, dhania powder, lal mirch aur namak. Dhak kar 7 minute jab tak tel kinaron par na dikhe.",
"Bhune aloo aur matar daal kar 2 minute masale mein lapetо.",
"2 cup garam paani daalo, ubaal aane do.",
"Dhak kar dheemi aanch par <b>12 minute</b> — aloo mein kanta aar-paar jaye. 3–4 aloo cube dabao, gravy gaadhi hogi.",
"Garam masala aur hara dhania. 2 minute rest.",
"Poori, roti ya chawal ke saath."],
tips:["Sardi mein taaza matar mile to frozen se kahin behtar.","Gravy zyada chahiye to 0.5 cup paani aur, par 5 minute extra pakao."]},

"sambar":{n:"Sambar",type:"main",tag:"south",time:"45 min",serves:4,
ing:[["Arhar dal",1,"cup","Dal"],["Imli",1,"nimbu-size","Other"],["Sahjan (drumstick)",1,"","Sabzi"],["Lauki/kaddu",1,"cup","Sabzi"],["Gajar",1,"medium","Sabzi"],["Pyaz (chhota/sambar)",10,"","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Kadi patta",15,"","Sabzi"],["Sambar powder",2.5,"tbsp","Masale"],["Haldi",0.75,"tsp","Masale"],["Rai",1,"tsp","Masale"],["Methi dana",0.25,"tsp","Masale"],["Hing",0.5,"tsp","Masale"],["Sookhi lal mirch",2,"","Masale"],["Gur",1,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",3,"tbsp","Other"]],
steps:[
"Arhar dal ko dho kar haldi aur 3 cup paani ke saath cooker mein 4 seeti. Mathni ya karchhi se poori tarah mathо — sambar ki dal smooth honi chahiye.",
"Imli ko garam paani mein 20 minute bhigao, haath se masal kar gaadha ras nikaalo, chhan lo.",
"Bhagone mein 1 tbsp tel garam karo, chhote pyaz 3 minute bhooно, phir gajar, lauki aur sahjan daalo.",
"Imli ka paani, tamatar, haldi aur namak daalo. Dhak kar <b>12 minute</b> pakao jab tak sabziyan narm aur imli ka kacchapan khatam na ho jaye — kaccha imli ka swaad poora sambar kharab karta hai.",
"Sambar powder daal kar 5 minute aur pakao.",
"Mathi hui dal daalo, zaroorat ke hisaab se 1–2 cup garam paani, gur daalo.",
"Dheemi aanch par <b>10 minute</b> khadakne do — bas halke bulbule, tez ubaal nahi.",
"Tadka: choti kadhai mein 2 tbsp tel, rai chatkao, methi dana (10 second, bhoora na ho), sookhi lal mirch, hing aur kadi patta.",
"Tadka sambar mein undel kar turant dhak do — 5 minute.",
"Idli, dosa ya sade chawal ke saath serve karo."],
tips:["Sahjan asli sambar ka swaad deta hai, mil jaye to zaroor daalo.","Gur optional lagta hai par imli ko balance karta hai."]},

"sarson-saag":{n:"Sarson ka Saag",type:"main",tag:"north",time:"1 ghanta 15 min",serves:4,
ing:[["Sarson ke patte",750,"g","Sabzi"],["Palak",250,"g","Sabzi"],["Bathua",100,"g","Sabzi"],["Makkai ka aata",4,"tbsp","Anaj"],["Pyaz",2,"medium","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Adrak",2,"inch","Sabzi"],["Lehsun",10,"kali","Sabzi"],["Hari mirch",3,"","Sabzi"],["Sookhi lal mirch",2,"","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",5,"tbsp","Dairy"]],
steps:[
"Saare patte 3–4 baar dho kar motа-motа kaat lo. Moti dandi hata do.",
"Cooker mein saag, 1 inch adrak, 5 lehsun kali, hari mirch, namak aur sirf <b>1 cup paani</b> daalo — patte khud bahut paani chhodte hain. 5 seeti madhyam aanch par.",
"Pressure utarne ke baad khol kar dekho, agar paani zyada ho to 5 minute khuli aanch par sukhao.",
"Mathni (ya hand blender ka pulse) se saag ko mathо — <b>bilkul smooth mat karo</b>, halka daanedar rehna chahiye.",
"Makkai ka aata 0.5 cup paani mein ghol kar (bina gaanth ke) saag mein daalo, lagataar chalate hue 5 minute.",
"Ab dheemi aanch par <b>30–40 minute</b> pakao, har 5 minute mein chalao. Saag gaadha hoga aur rang gehra hoga. Ye lambi pakai hi asli saag banati hai.",
"Tadka: kadhai mein ghee garam karo, kuta lehsun 40 second sunhera, barik kata pyaz 6 minute.",
"Kata adrak, sookhi lal mirch aur tamatar daal kar 6 minute jab tak ghee alag na ho. Lal mirch powder daalo.",
"Ye tadka saag mein daal kar 10 minute aur pakao.",
"Makke ki roti, gud aur safed makkhan ke saath — upar se 1 tbsp ghee."],
tips:["Bathua na mile to sirf sarson-palak bhi chalega, ratio 3:1.","Agle din ka saag hamesha behtar lagta hai."]},

"veg-pulao":{n:"Veg Pulao",type:"main",tag:"north",time:"35 min",serves:4,
ing:[["Basmati chawal",2,"cup","Anaj"],["Gajar",1,"medium","Sabzi"],["Matar",0.75,"cup","Sabzi"],["French beans",75,"g","Sabzi"],["Pyaz",2,"medium","Sabzi"],["Hari mirch",2,"","Sabzi"],["Adrak-lehsun paste",1,"tbsp","Sabzi"],["Pudina",0.25,"cup","Sabzi"],["Tej patta",2,"","Masale"],["Dalchini",1,"inch","Masale"],["Laung",4,"","Masale"],["Elaichi",3,"","Masale"],["Jeera",1,"tsp","Masale"],["Shahi jeera",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",3,"tbsp","Dairy"]],
steps:[
"Chawal ko 3 baar dho kar 25 minute bhigao. Phir paani nikaal kar 10 minute chalni mein sukhao — daane alag-alag rahenge.",
"Bhagone mein ghee garam karo, tej patta, dalchini, laung, elaichi, jeera aur shahi jeera daal kar 30 second.",
"Lamba kata pyaz daal kar <b>6 minute</b> sunhera karo. 2 tbsp bhuna pyaz garnish ke liye nikaal lo.",
"Adrak-lehsun paste 1 minute, hari mirch.",
"Gajar, beans aur matar daal kar 3 minute bhooно.",
"Chawal daalo aur <b>bahut halke haath se</b> 2 minute bhooно — har daana ghee mein lipat jaye, tootna nahi chahiye.",
"3.5 cup garam paani, namak aur pudina daalo. Chakh kar namak theek karo — paani thoda namkeen lagna chahiye.",
"Tez ubaal aane do, phir aanch bilkul dheemi, dhakkan band, <b>12 minute</b>. Beech mein dhakkan mat kholo.",
"Gas band karke <b>10 minute dum</b> — ye step chhodoge to chawal chipke hue milenge.",
"Kaante se fluff karo, bhune pyaz daal kar raita aur achar ke saath serve karo."],
tips:["Paani:chawal 1:1.75 se daane khile-khile rehte hain.","Bhagone ka dhakkan bhaari ho to dum achha lagta hai."]},

"dahi-aloo":{n:"Dahi Wale Aloo",type:"main",tag:"north",time:"25 min",serves:4,
ing:[["Aloo (chhote, uble)",600,"g","Sabzi"],["Dahi",1,"cup","Dairy"],["Besan",1,"tbsp","Anaj"],["Adrak",1,"inch","Sabzi"],["Hari mirch",2,"","Sabzi"],["Hara dhania",0.25,"cup","Sabzi"],["Jeera",1,"tsp","Masale"],["Hing",0.25,"tsp","Masale"],["Haldi",0.5,"tsp","Masale"],["Dhania powder",2,"tsp","Masale"],["Lal mirch powder",1,"tsp","Masale"],["Saunf powder",1,"tsp","Masale"],["Garam masala",0.5,"tsp","Masale"],["Namak",null,"","Masale"],["Ghee",3,"tbsp","Dairy"]],
steps:[
"Dahi ko besan ke saath phent kar bilkul smooth karo — gaanth bilkul nahi. Isi besan se dahi phategaa nahi.",
"Uble aloo chhil kar haath se do tukdon mein todo.",
"Kadhai mein ghee garam karo, jeera chatkao, hing, kata adrak aur hari mirch.",
"Aanch <b>bilkul dheemi</b> karo. Ab phenta dahi daalo aur lagataar 4–5 minute chalate raho jab tak halke bulbule na aane lagein. Beech mein chalana band mat karo — yahi ek jagah dahi phatta hai.",
"Haldi, dhania powder, lal mirch aur saunf powder daalo, 2 minute.",
"Tootey aloo aur namak daalo, mix karo.",
"1.5 cup garam paani daal kar madhyam aanch par 10 minute pakao jab tak gravy halki gaadhi na ho.",
"Garam masala aur hara dhania. 5 minute dhak kar rakho.",
"Poori, kachori ya sade chawal ke saath — vrat-friendly bhi ban sakta hai (hing hata kar, sendha namak se)."],
tips:["Dahi taaza aur kam khatta lo.","Namak dahi pakne ke baad hi daalo."]},

/* ---------------- SIDES, BREADS, RICE ---------------- */
"phulka":{n:"Phulka Roti",type:"side",tag:"basic",time:"25 min",serves:4,
ing:[["Gehun ka atta",400,"g","Anaj"],["Namak",0.5,"tsp","Masale"],["Ghee",2,"tbsp","Dairy"]],
steps:[
"Atte mein namak mila kar thoda-thoda paani daalte hue (lagbhag 240 ml) narm dough gundho. 6–7 minute gundhna zaroori hai — gluten banega aur roti phoolegi.",
"Upar se 0.5 tsp ghee laga kar geele kapde se dhak kar <b>20–30 minute</b> rest do.",
"8–10 gole banao. Har gole ko haath se chapta karke sookhe atte mein lapetо.",
"Belan se halke haath se 6 inch gol belo — beech mein zyada dabav mat do, warna beech motа reh jayega aur roti nahi phoolegi.",
"Tawa tez garam karo (paani ki boond turant udni chahiye).",
"Roti daalo. <b>20 second</b> baad, jab rang halka badal jaye aur chhote bubble dikhein, palto.",
"Doosri side par 30–40 second, jab tak safed daag bhoore na hone lagein.",
"Chimte se utha kar seedha flame par rakho — 5–8 second mein roti gubbare ki tarah phool jayegi. Turant palat kar 3 second.",
"Ghee laga kar casserole mein rakho, ek dusre ke upar nahi — warna bhaap se geeli hongi.",
"Har sabzi, dal ke saath garam serve karo."],
tips:["Roti nahi phool rahi = ya tawa thanda hai ya rolling unequal hai.","Dough jitna narm, roti utni mulayam."]},

"jeera-rice":{n:"Jeera Rice",type:"side",tag:"basic",time:"25 min",serves:4,
ing:[["Basmati chawal",1.5,"cup","Anaj"],["Jeera",2,"tsp","Masale"],["Tej patta",1,"","Masale"],["Dalchini",1,"inch","Masale"],["Laung",3,"","Masale"],["Hari mirch",1,"","Sabzi"],["Namak",null,"","Masale"],["Ghee",2,"tbsp","Dairy"]],
steps:[
"Chawal ko 3 baar dho kar 20 minute bhigao, phir chhan kar 10 minute sukhao.",
"Bhagone mein ghee garam karo, tej patta, dalchini, laung.",
"Jeera daalo aur <b>10 second</b> chatkne do — gehri khushboo aani chahiye.",
"Cheeri hari mirch daalo.",
"Chawal daal kar halke haath se 2 minute bhooно.",
"2.5 cup garam paani aur namak daalo, tez ubaal.",
"Ubaal aate hi aanch bilkul dheemi, dhakkan band, <b>11 minute</b>.",
"Gas band karke 8 minute dum, phir kaante se fluff karo. Dal tadka ya rajma ke saath."],
tips:["Paani:chawal 1:1.66 sahi hai.","Chalane se chawal toot-te hain — sirf fluff karo."]},

"steamed-rice":{n:"Sade Chawal",type:"side",tag:"basic",time:"20 min",serves:4,
ing:[["Chawal",1.5,"cup","Anaj"],["Namak",0.5,"tsp","Masale"]],
steps:[
"Chawal ko 3 baar dho lo jab tak paani saaf na aaye. 15 minute bhigao.",
"Bade bhagone mein 6 cup paani ubaalo, namak daalo.",
"Chhane hue chawal daalo, ek baar hilao.",
"Khuli aanch par 8–10 minute pakao. 8 minute par ek daana nikaal kar dabao — beech mein bilkul halka sa kadapan ho to ho gaya.",
"Chalni mein palat kar paani nikaal do, 2 minute drain hone do.",
"Dhak kar 5 minute rakho, phir kaante se fluff karo."],
tips:["Cooker mein karna ho to 1:1.5 paani, 2 seeti.","Zyada ubaal = chipka chawal."]},

"boondi-raita":{n:"Boondi Raita",type:"side",tag:"basic",time:"10 min",serves:4,
ing:[["Dahi",2,"cup","Dairy"],["Boondi",1,"cup","Other"],["Bhuna jeera powder",1,"tsp","Masale"],["Kala namak",0.5,"tsp","Masale"],["Lal mirch powder",0.25,"tsp","Masale"],["Hara dhania",2,"tbsp","Sabzi"],["Namak",null,"","Masale"]],
steps:[
"Boondi ko garam paani mein <b>3 minute</b> bhigao, phir halke haath se daba kar paani nichod lo. Isse boondi narm hogi aur extra tel nikal jayega.",
"Dahi ko 1 minute phento jab tak smooth na ho, zaroorat ho to 3 tbsp paani.",
"Bhuna jeera, kala namak, saada namak aur lal mirch milao.",
"Nichodi boondi daal kar halka mix karo.",
"Thanda karke serve karo, upar se jeera aur dhania. Serve se 10 minute pehle hi boondi milao, warna gal jayegi."],
tips:["Jeera khud bhoon kar peeso — khushboo alag hi hoti hai."]},

"kachumber":{n:"Kachumber Salad",type:"side",tag:"basic",time:"10 min",serves:4,
ing:[["Kheera",2,"","Sabzi"],["Tamatar",2,"medium","Sabzi"],["Pyaz",1,"medium","Sabzi"],["Hari mirch",1,"","Sabzi"],["Nimbu",1,"","Sabzi"],["Hara dhania",2,"tbsp","Sabzi"],["Bhuna jeera powder",0.5,"tsp","Masale"],["Kala namak",0.5,"tsp","Masale"]],
steps:[
"Kheera, tamatar aur pyaz ko ek jaise chhote cube mein kaato — barabar kaatna hi salad ka texture banata hai.",
"Tamatar ke beej wala geela hissa nikaal do, salad paani nahi chhodega.",
"Barik kati hari mirch aur dhania milao.",
"Nimbu, kala namak aur bhuna jeera <b>serve karne se just pehle</b> daalo — pehle daloge to sabzi paani chhod degi.",
"Thanda serve karo."],
tips:["Kaali mirch aur chaat masala bhi achha lagta hai."]},

"nariyal-chutney":{n:"Nariyal Chutney",type:"side",tag:"south",time:"15 min",serves:4,
ing:[["Taaza nariyal",1,"cup","Sabzi"],["Bhuni chana dal",3,"tbsp","Dal"],["Hari mirch",3,"","Sabzi"],["Adrak",0.5,"inch","Sabzi"],["Imli",0.5,"tsp","Other"],["Rai",1,"tsp","Masale"],["Urad dal",1,"tsp","Dal"],["Sookhi lal mirch",2,"","Masale"],["Kadi patta",10,"","Sabzi"],["Hing",0.25,"tsp","Masale"],["Namak",null,"","Masale"],["Tel",2,"tbsp","Other"]],
steps:[
"Mixer mein kisa nariyal, bhuni chana dal, hari mirch, adrak, imli aur namak daalo.",
"<b>Thanda paani</b> (0.5 cup) thoda-thoda daal kar peeso jab tak mulayam na ho. Garam paani se nariyal ka tel alag ho jaata hai aur chutney kadvi lagti hai.",
"Consistency dahi jaisi rakho — dosa ke liye thodi patli, idli ke liye gaadhi.",
"Tadka: choti kadhai mein tel garam karo, rai chatkao, urad dal 20 second sunhera, sookhi lal mirch, hing aur kadi patta.",
"Tadka chutney par undel do, halka mix karo.",
"Fridge mein 2 din chalti hai, par taaza best hai."],
tips:["Nariyal ka bhoora hissa hata do — rang safed rahega.","Dahi 2 tbsp milane se khattapan aur shelf life dono badhte hain."]},

"hari-chutney":{n:"Hari Chutney",type:"side",tag:"basic",time:"10 min",serves:6,
ing:[["Hara dhania",2,"cup","Sabzi"],["Pudina",0.75,"cup","Sabzi"],["Hari mirch",3,"","Sabzi"],["Adrak",1,"inch","Sabzi"],["Lehsun",3,"kali","Sabzi"],["Nimbu",1,"","Sabzi"],["Bhuna jeera powder",1,"tsp","Masale"],["Kala namak",0.5,"tsp","Masale"],["Cheeni",0.5,"tsp","Masale"],["Namak",null,"","Masale"]],
steps:[
"Dhania aur pudina ko achhi tarah dho kar motа kaat lo. Pudina ki moti dandi hata do — kadwahat wahin hoti hai.",
"Mixer mein sab kuch daal kar, <b>bahut kam paani</b> (2–3 tbsp) ke saath peeso.",
"Beech mein ruk kar kinare se chutney neeche karo, phir dobara peeso — smooth chutney yahi trick hai.",
"Nimbu aakhir mein daalo — pehle daaloge to garmi se rang kaala pad jaayega.",
"Chakh kar namak-cheeni balance karo. Airtight dabbe mein fridge mein 5 din."],
tips:["Ice cube daal kar peesoge to rang bilkul hara rahega.","2 tbsp dahi milao to dip ban jaati hai."]}

};

/* ===================================================================
   14-DAY ROTATION — North Indian veg majority, South Indian breakfasts
   =================================================================== */
const SCHED = [
 {b:["poha"],                   l:["dal-tadka","jeera-aloo","phulka","steamed-rice","kachumber"],      d:["matar-paneer","phulka","boondi-raita"]},
 {b:["idli-sambar","nariyal-chutney"], l:["rajma","steamed-rice","kachumber"],                          d:["aloo-gobhi","phulka","dal-tadka"]},
 {b:["besan-chilla","hari-chutney"], l:["chana-masala","phulka","boondi-raita"],                        d:["lauki-chana-dal","steamed-rice","phulka"]},
 {b:["aloo-paratha"],           l:["kadhi-pakora","steamed-rice","kachumber"],                          d:["bhindi-masala","phulka","dal-tadka"]},
 {b:["upma","nariyal-chutney"], l:["palak-paneer","phulka","jeera-rice"],                               d:["dahi-aloo","phulka","kachumber"]},
 {b:["methi-thepla"],           l:["dal-makhani","jeera-rice","kachumber"],                             d:["mix-veg","phulka","boondi-raita"]},
 {b:["puri-bhaji"],             l:["paneer-butter-masala","phulka","veg-pulao"],                        d:["dal-tadka","jeera-aloo","phulka"]},
 {b:["masala-dosa","nariyal-chutney"], l:["baingan-bharta","phulka","dal-tadka"],                       d:["aloo-matar","steamed-rice","kachumber"]},
 {b:["moong-cheela","hari-chutney"], l:["chole","steamed-rice","kachumber"],                            d:["lauki-chana-dal","phulka","boondi-raita"]},
 {b:["semiya-upma"],            l:["kadai-paneer","phulka","jeera-rice"],                               d:["dal-tadka","bhindi-masala","phulka"]},
 {b:["paneer-bhurji"],          l:["sarson-saag","phulka","kachumber"],                                 d:["mix-veg","steamed-rice","dal-tadka"]},
 {b:["medu-vada","sambar","nariyal-chutney"], l:["rajma","jeera-rice","boondi-raita"],                  d:["aloo-gobhi","phulka","dal-tadka"]},
 {b:["poha"],                   l:["sambar","steamed-rice","jeera-aloo"],                               d:["palak-paneer","phulka","kachumber"]},
 {b:["suji-halwa","puri-bhaji"],l:["paneer-butter-masala","veg-pulao","boondi-raita"],                  d:["dal-tadka","phulka","kachumber"]}
];

/* ===================================================================
   APP
   =================================================================== */
const DAYS=["Ravivar","Somvar","Mangalvar","Budhvar","Guruvar","Shukravar","Shanivar"];
const MON=["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];
const fmt=d=>`${DAYS[d.getDay()]}, ${d.getDate()} ${MON[d.getMonth()]}`;
const idx=d=>{const e=new Date(2026,0,1);const n=Math.floor((d-e)/864e5);return ((n%14)+14)%14;};
const todayD=new Date(); todayD.setHours(0,0,0,0);
const tomD=new Date(todayD.getTime()+864e5);

document.getElementById("today").textContent=fmt(todayD);
document.getElementById("tomdate").textContent=fmt(tomD)+" ka menu is list par tika hai";

/* ---- today's thali ---- */
function paintMeal(slot,keys){
  const main=keys.filter(k=>R[k]&&R[k].type!=="side");
  const sides=keys.filter(k=>R[k]&&R[k].type==="side");
  const show=main.length?main:keys.slice(0,1);
  const rest=main.length?sides:keys.slice(1);
  const ul=document.getElementById("m-"+slot); ul.innerHTML="";
  show.forEach(k=>{
    const li=document.createElement("li");
    const b=document.createElement("button");
    b.textContent=R[k].n; b.onclick=()=>openRec(k);
    li.appendChild(b); ul.appendChild(li);
  });
  document.getElementById("s-"+slot).textContent = rest.length ? "Saath mein: "+rest.map(k=>R[k].n).join(", ") : "";
}
const tdy=SCHED[idx(todayD)];
paintMeal("b",tdy.b); paintMeal("l",tdy.l); paintMeal("d",tdy.d);

/* ---- tomorrow's shopping list ---- */
const tmr=SCHED[idx(tomD)];
const tmrAll=[...tmr.b,...tmr.l,...tmr.d];
document.getElementById("tommenu").innerHTML=tmrAll.map(k=>`<span class="chip">${R[k].n}</span>`).join("");

const ORDER=["Sabzi","Dal","Anaj","Dairy","Masale","Other"];
const LABEL={Sabzi:"Sabzi & taaza",Dal:"Dal & pulses",Anaj:"Aata & anaj",Dairy:"Dairy",Masale:"Masale",Other:"Baaki"};
function buildList(keys){
  const map={};
  keys.forEach(k=>R[k].ing.forEach(([item,q,u,c])=>{
    const id=item+"|"+u;
    if(!map[id])map[id]={item,u,c,q:0,any:false};
    if(q===null)map[id].any=true; else map[id].q+=q;
  }));
  const out={}; ORDER.forEach(c=>out[c]=[]);
  Object.values(map).forEach(v=>{
    const q=v.any&&!v.q?"zaroorat ke hisaab se":`${+v.q.toFixed(2)} ${v.u}`.trim();
    (out[v.c]||out.Other).push({t:v.item,q});
  });
  ORDER.forEach(c=>out[c].sort((a,b)=>a.t.localeCompare(b.t)));
  return out;
}
const LIST=buildList(tmrAll);
document.getElementById("shop").innerHTML=ORDER.filter(c=>LIST[c].length).map((c,ci)=>`
  <div class="cat"><h4>${LABEL[c]}</h4><ul>${LIST[c].map((r,i)=>`
    <li><input type="checkbox" id="c${ci}-${i}"><label for="c${ci}-${i}">${r.t} — ${r.q}</label></li>`).join("")}</ul></div>`).join("");

document.getElementById("copy").onclick=async e=>{
  const txt=`Kal (${fmt(tomD)}) ka saaman\n\n`+ORDER.filter(c=>LIST[c].length)
    .map(c=>LABEL[c]+"\n"+LIST[c].map(r=>`- ${r.t} — ${r.q}`).join("\n")).join("\n\n");
  try{await navigator.clipboard.writeText(txt);e.target.textContent="Copy ho gaya";}
  catch{e.target.textContent="Copy nahi hua";}
  setTimeout(()=>e.target.textContent="Copy list",1800);
};
document.getElementById("print").onclick=()=>window.print();
document.getElementById("reset").onclick=()=>document.querySelectorAll('#shop input').forEach(i=>i.checked=false);

/* ---- 14 day strip ---- */
document.getElementById("strip").innerHTML=Array.from({length:14},(_,i)=>{
  const d=new Date(todayD.getTime()+i*864e5), s=SCHED[idx(d)];
  const nm=ks=>ks.filter(k=>R[k].type!=="side").map(k=>R[k].n).join(", ")||R[ks[0]].n;
  return `<div class="day${i?"":" today"}">
    <div class="dh">${i?fmt(d).split(",")[0]:"Aaj"}<span>${d.getDate()} ${MON[d.getMonth()]}</span></div>
    <p><b>N:</b> ${nm(s.b)}</p><p><b>D:</b> ${nm(s.l)}</p><p><b>R:</b> ${nm(s.d)}</p></div>`;
}).join("");

/* ---- recipe library ---- */
const grid=document.getElementById("grid");
let filt="all", term="";
const TT={breakfast:"Nashta",main:"Sabzi / Dal",side:"Saath mein"};
function render(){
  const keys=Object.keys(R).filter(k=>{
    const r=R[k];
    const okF = filt==="all" || (filt==="south"? r.tag==="south" : r.type===filt);
    const okT = !term || (r.n+" "+r.ing.map(i=>i[0]).join(" ")).toLowerCase().includes(term);
    return okF&&okT;
  });
  grid.innerHTML = keys.length ? keys.map(k=>{
    const r=R[k];
    return `<button class="card" data-k="${k}">
      <span class="rn">${r.n}</span>
      <span class="meta"><i class="tagdot t-${r.tag}"></i>${TT[r.type]} · ${r.time} · ${r.serves} log</span></button>`;
  }).join("") : `<p class="empty">Is naam se kuch nahi mila. Doosra shabd try karo — "dal", "paneer", "dosa".</p>`;
  grid.querySelectorAll(".card").forEach(b=>b.onclick=()=>openRec(b.dataset.k));
}
document.getElementById("q").oninput=e=>{term=e.target.value.trim().toLowerCase();render();};
document.querySelectorAll(".fchip").forEach(b=>b.onclick=()=>{
  filt=b.dataset.f;
  document.querySelectorAll(".fchip").forEach(x=>x.setAttribute("aria-pressed",x===b));
  render();
});
render();

/* ---- modal ---- */
const dlg=document.getElementById("rec");
let cur=null;
function openRec(k){
  const r=R[k]; cur=r;
  document.getElementById("rhead").className="rhead "+r.tag;
  document.getElementById("rtitle").textContent=r.n;
  document.getElementById("rmeta").textContent=`${r.time} · ${r.serves} logon ke liye · ${r.tag==="south"?"South Indian":r.tag==="north"?"North Indian":"Roz ka"}`;
  document.getElementById("rbody").innerHTML=`
    <h4>Saamagri</h4>
    <table class="ingtable"><tbody>${r.ing.map(([i,q,u])=>
      `<tr><td>${i}</td><td>${q===null?"swaad anusaar":(+q+" "+u).trim()}</td></tr>`).join("")}</tbody></table>
    <h4>Vidhi</h4>
    <ol class="steps">${r.steps.map(s=>`<li>${s}</li>`).join("")}</ol>
    ${r.tips?`<h4>Dhyan rakho</h4><div class="tipbox"><ul>${r.tips.map(t=>`<li>${t}</li>`).join("")}</ul></div>`:""}
    <p class="reflinks">Isi dish ke doosre versions:
      <a href="https://www.tarladalal.com/search?q=${encodeURIComponent(r.n)}" target="_blank" rel="noopener">Tarla Dalal</a> ·
      <a href="https://nishamadhulika.com/?s=${encodeURIComponent(r.n)}" target="_blank" rel="noopener">Nisha Madhulika</a> ·
      <a href="https://www.sanjeevkapoor.com/Search?q=${encodeURIComponent(r.n)}" target="_blank" rel="noopener">Sanjeev Kapoor</a></p>`;
  document.getElementById("rbody").scrollTop=0;
  dlg.showModal();
}
document.getElementById("close").onclick=()=>dlg.close();
document.getElementById("copyIng").onclick=async e=>{
  if(!cur)return;
  const t=cur.n+"\n"+cur.ing.map(([i,q,u])=>`- ${i}: ${q===null?"swaad anusaar":(+q+" "+u).trim()}`).join("\n");
  try{await navigator.clipboard.writeText(t);e.target.textContent="Copy ho gaya";}catch{e.target.textContent="Copy nahi hua";}
  setTimeout(()=>e.target.textContent="Copy ingredients",1800);
};
dlg.addEventListener("click",e=>{if(e.target===dlg)dlg.close();});
</script>
</body>
</html>
