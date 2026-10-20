
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>BLOCK HUNTER</title>
<style>
:root{--bg:#09080e;--panel:#121019;--border:#292235;--purple:#a875ff;--text:#f5efff;--muted:#958ca6}
*{box-sizing:border-box}
body{margin:0;background:radial-gradient(ellipse at 50% 0%,#211332 0%,var(--bg) 55%);color:var(--text);font-family:Arial,sans-serif}
button{font:inherit;cursor:pointer;color:inherit}
button:disabled{opacity:.4;cursor:not-allowed}
.app{max-width:1000px;margin:auto;padding:18px}
header{display:flex;justify-content:space-between;align-items:center;gap:12px;margin-bottom:20px}
.logo{font-size:23px;font-weight:900;letter-spacing:3px}
.logo span{color:var(--purple)}
.level{color:var(--muted);font-size:12px;margin-top:6px}
.wallet{background:var(--panel);border:1px solid var(--border);border-radius:14px;padding:12px;text-align:right;min-width:115px}
.wallet strong{color:#f5cf76;font-size:18px}
.xpbar,.bar{background:#292332;height:7px;border-radius:20px;overflow:hidden}
.xpfill,.fill{height:100%;background:linear-gradient(90deg,#7444c9,#d4aaff);transition:width .2s}
.xpbar{margin-top:8px}
.layout{display:grid;grid-template-columns:minmax(0,1.2fr) minmax(260px,.8fr);gap:14px}
.panel{background:rgba(18,16,25,.94);border:1px solid var(--border);border-radius:18px;padding:18px;min-width:0}
.eyebrow{color:var(--purple);font-size:10px;font-weight:bold;letter-spacing:3px}
h2{font-size:20px;margin:8px 0}
h3{font-size:14px;margin:0 0 12px}
.muted{color:var(--muted);font-size:12px}
.location{display:flex;gap:8px;overflow-x:auto;margin:16px 0}
.loc{flex:1;min-width:105px;padding:10px 8px;border-radius:11px;background:#17131e;border:1px solid var(--border);font-size:12px}
.loc.active{border-color:var(--purple);background:#241735}
.loc small{display:block;color:var(--muted);margin-top:5px}
.arena{text-align:center;border:1px solid #38254c;border-radius:17px;padding:20px 12px;background:radial-gradient(ellipse at 50% 45%,#2a193c,#100d17 72%)}
.blockname{font-size:12px;color:#c9b2e9;letter-spacing:2px}
.block{width:190px;height:175px;max-width:80%;margin:14px auto;display:grid;place-items:center;border:1px solid #9c68d0;border-radius:23px;background:linear-gradient(145deg,#352048,#15101f);box-shadow:0 0 35px #8b42cb24,inset 0 0 25px #a36bff15;font-size:85px;user-select:none;transition:transform .08s,filter .1s}
.block:active{transform:scale(.93);filter:brightness(1.5)}
.block.hit{animation:hit .16s}
.block.broken{animation:broken .3s}
@keyframes hit{50%{transform:translateX(4px) rotate(2deg);filter:brightness(1.8)}}
@keyframes broken{50%{transform:scale(1.13);opacity:.3}}
.hptext{font-size:12px;color:#c8bed5;margin:8px}
.bar{height:9px;margin:0 auto;max-width:320px}
.damage{min-height:40px;color:#e0baff;font-size:14px;margin:12px;line-height:1.5}
.mainbtn,.btn{background:#241634;border:1px solid #69458e;border-radius:11px;padding:12px}
.mainbtn{width:100%;max-width:320px;background:linear-gradient(100deg,#6033a2,#9a5bd0);font-weight:bold}
.btn{font-size:12px}
button:hover:not(:disabled){filter:brightness(1.2)}
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-top:14px}
.stat{background:#0d0b12;border:1px solid var(--border);border-radius:10px;padding:11px 7px;text-align:center}
.stat b{display:block;font-size:16px;margin-bottom:5px}
.stat small{color:var(--muted);font-size:10px}
.tabs{display:flex;flex-wrap:wrap;gap:7px;margin:14px 0}
.tab{padding:9px 12px;background:#17131e;border:1px solid var(--border);border-radius:9px;font-size:12px}
.tab.active{border-color:var(--purple);color:#d6b9ff}
.section{display:none}
.section.active{display:block}
.item,.upgrade,.achievement{background:#0e0c13;border:1px solid var(--border);border-radius:12px;padding:12px;margin-bottom:8px}
.item{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.itemicon{font-size:30px;width:42px;text-align:center}
.iteminfo{flex:1;min-width:90px}
.iteminfo b{font-size:12px}
.iteminfo small{display:block;margin-top:5px;color:var(--muted);font-size:11px}
.rarity{font-size:10px;font-weight:bold;margin-top:4px}
.Common{color:#c0bbc9}.Uncommon{color:#70dc9c}.Rare{color:#6bc6ff}.Epic{color:#d394ff}.Legendary{color:#ffd16e}.Mythic{color:#ff718d}.Secret{color:#ff55ff;text-shadow:0 0 10px #ff00d4}
.upgrade{display:flex;gap:10px;align-items:center}
.upicon{font-size:25px}
.upinfo{flex:1}
.upinfo b{font-size:13px}
.upinfo small{display:block;color:var(--muted);font-size:11px;margin-top:5px}
.notice{font-size:12px;color:#c7a7ff;min-height:32px;margin-top:12px;line-height:1.5}
.footer{text-align:center;padding:20px;color:#61596c;font-size:10px}
#toast{position:fixed;bottom:20px;left:50%;transform:translateX(-50%);background:#241832;border:1px solid #8154ad;padding:12px 18px;border-radius:12px;z-index:9;font-size:13px;display:none;max-width:90%;text-align:center}
.drop-chances{margin-top:14px;padding:12px;background:#0e0c13;border:1px solid var(--border);border-radius:12px}
.chance-row{display:flex;justify-content:space-between;gap:10px;padding:7px 0;border-bottom:1px solid #292235;font-size:12px}
.chance-row:last-child{border-bottom:0}
.chance-row b{white-space:nowrap}
.chance-note{margin-top:10px;line-height:1.5}
@media(max-width:650px){.app{padding:12px}.layout{grid-template-columns:1fr}.panel{padding:14px}.logo{font-size:19px;letter-spacing:2px}.block{height:155px;width:170px;font-size:75px}.location{margin:12px 0}}
</style>
</head>
<body>
<div class="app">
<header>
<div>
<div class="logo">BLOCK <span>HUNTER</span></div>
<div class="level">УРОВЕНЬ <b id="level">1</b> · <span id="xptext">0 / 100 XP</span></div>
<div class="xpbar"><div id="xpbar" class="xpfill" style="width:0%"></div></div>
</div>
<div class="wallet">🪙 <strong id="coins">0</strong><div class="muted">монеты</div></div>
</header>

<div class="layout">
<section class="panel">
<div class="eyebrow">ЗОНА ДОБЫЧИ</div>
<h2 id="locationTitle">Заброшенное святилище</h2>
<div class="muted" id="locationDesc">Здесь начинаются твои поиски.</div>
<div class="location" id="locations"></div>

<div class="arena">
<div class="blockname" id="blockname">ПРОКЛЯТЫЙ СУНДУК</div>
<button class="block" id="block" aria-label="Ударить по блоку">📦</button>
<div class="hptext">Прочность: <b id="hptext">20 / 20</b></div>
<div class="bar"><div class="fill" id="hpbar" style="width:100%"></div></div>
<div class="damage" id="damageText">Найди что-нибудь ценное...</div>
<button class="mainbtn" id="hit">⛏️ УДАРИТЬ ПО БЛОКУ</button>
<div class="muted" style="margin-top:10px">Критический удар наносит двойной урон</div>
</div>

<div class="stats">
<div class="stat"><b id="powerStat">1</b><small>УРОН</small></div>
<div class="stat"><b id="critStat">5%</b><small>КРИТ. ШАНС</small></div>
<div class="stat"><b id="luckStat">0</b><small>УДАЧА</small></div>
</div>

<div class="drop-chances">
<h3>🎲 Шансы выпадения</h3>
<div class="chance-row"><span>🪨 Ничего не выпало</span><b>30%</b></div>
<div class="chance-row"><span class="Common">Обычный</span><b>45% от дропа</b></div>
<div class="chance-row"><span class="Uncommon">Необычный</span><b>25% от дропа</b></div>
<div class="chance-row"><span class="Rare">Редкий</span><b>15% от дропа</b></div>
<div class="chance-row"><span class="Epic">Эпический</span><b>8% от дропа</b></div>
<div class="chance-row"><span class="Legendary">Легендарный</span><b>5% от дропа</b></div>
<div class="chance-row"><span class="Mythic">Мифический</span><b>1,8% от дропа</b></div>
<div class="chance-row"><span class="Secret">✦ СЕКРЕТНЫЙ</span><b>0,2% от дропа</b></div>
<div class="muted chance-note">30% — блок без предмета. Остальные проценты — веса редкостей среди успешных выпадений. Удача немного повышает шанс получить предмет.</div>
</div>

<div class="notice" id="notice">Разрушай блоки и собирай редкие предметы.</div>
</section>

<section class="panel">
<div class="eyebrow">ТВОЯ КОЛЛЕКЦИЯ</div>
<h2>Инвентарь и развитие</h2>
<div class="muted">Устанавливай найденные предметы, чтобы получать пассивный доход.</div>

<div class="tabs">
<button class="tab active" data-tab="inventory">Инвентарь <span id="itemCount">0</span></button>
<button class="tab" data-tab="upgrades">Прокачка</button>
<button class="tab" data-tab="collection">Коллекция</button>
<button class="tab" data-tab="achievements">Ачивки</button>
<button class="tab" data-tab="stats">Статистика</button>
</div>

<div id="inventory" class="section active">
<div class="muted" style="margin-bottom:12px">Установи предмет, чтобы он приносил деньги каждую секунду.</div>
<div id="items"></div>
</div>
<div id="upgrades" class="section"><div id="upgradeList"></div></div>
<div id="collection" class="section">
<div class="stat" style="margin-bottom:12px"><b id="income">0</b><small>МОНЕТ В СЕКУНДУ</small></div>
<div class="muted" style="margin-bottom:12px">Доход дают только установленные предметы. Максимум дохода за офлайн — 8 часов.</div>
<div id="collectionList"></div>
</div>
<div id="achievements" class="section"><div id="achievementList"></div></div>
<div id="stats" class="section">
<div id="statsList"></div>
<button class="btn" id="sound">🔊 Включить звук</button>
<button class="btn" id="save">💾 Сохранить</button>
<button class="btn" id="reset">♻️ Сбросить игру</button>
</div>
</section>
</div>
<div class="footer">BLOCK HUNTER · добыча принадлежит тем, кто её забрал</div>
</div>
<div id="toast"></div>

<script>
const $=id=>document.getElementById(id);

const rarities=[
{name:"Обычный",key:"Common",weight:45,mult:1,income:.1},
{name:"Необычный",key:"Uncommon",weight:25,mult:2,income:.5},
{name:"Редкий",key:"Rare",weight:15,mult:5,income:2},
{name:"Эпический",key:"Epic",weight:8,mult:15,income:8},
{name:"Легендарный",key:"Legendary",weight:5,mult:50,income:30},
{name:"Мифический",key:"Mythic",weight:1.8,mult:200,income:100},
{name:"Секретный",key:"Secret",weight:.2,mult:1000,income:500}
];

const itemPool=[
["🦴","Старая кость"],["🕯️","Чёрная свеча"],["💀","Череп грешника"],
["🗝️","Ржавая отмычка"],["🪬","Проклятый амулет"],["🕸️","Паучий идол"],
["💜","Аметистовая душа"],["🩸","Кровавый кристалл"],["👁️","Око бездны"],
["🌑","Тёмная луна"],["🔮","Сфера пророка"],["⛓️","Цепь изгнанника"],
["👑","Корона забытого короля"],["💎","Алмаз пустоты"],
["🪽","Крыло падшего ангела"],["🖤","Сердце бездны"],
["☄️","Осколок кометы"],["🌌","Звезда проклятых"]
];

const secretPool=[
["🪬","Печать забытого бога"],
["👁️","Всевидящее око"],
["🩸","Кровь древнего"],
["🌌","Сердце вселенной"],
["👑","Корона последнего"],
["💠","Абсолютный кристалл"]
];

const locations=[
{name:"Заброшенное святилище",short:"Святилище",emoji:"📦",cost:0,hp:20,reward:10,desc:"Здесь начинаются твои поиски."},
{name:"Проклятый лес",short:"Лес",emoji:"🌲",cost:250,hp:65,reward:28,desc:"Между деревьями скрываются древние реликвии."},
{name:"Подземный рудник",short:"Рудник",emoji:"⛏️",cost:1200,hp:180,reward:90,desc:"Камни здесь хранят чужую силу."},
{name:"Забытый собор",short:"Собор",emoji:"⛪",cost:6000,hp:500,reward:350,desc:"Место, где исчезают даже святые."},
{name:"Бездна",short:"Бездна",emoji:"🌌",cost:25000,hp:1500,reward:1500,desc:"Последняя граница известного мира."}
];

const upgradeDefs=[
{id:"power",icon:"⚔️",name:"Сила удара",desc:"Больше урона за каждый тап.",base:25},
{id:"crit",icon:"💥",name:"Критический шанс",desc:"Криты наносят двойной урон.",base:100},
{id:"luck",icon:"🍀",name:"Удача охотника",desc:"Немного повышает шанс получить предмет.",base:150},
{id:"hp",icon:"🧱",name:"Разрушитель",desc:"Увеличивает прочность блоков.",base:200}
];

const defaultState=()=>({
coins:0,xp:0,level:1,damage:1,crit:5,luck:0,hpLevel:0,
blocks:0,clicks:0,critHits:0,items:[],equipped:[],
upgrades:{power:0,crit:0,luck:0,hp:0},
unlocked:[0],location:0,currentHp:20,passive:0,
sound:false,lastTime:Date.now(),achievements:[],
drops:0,emptyDrops:0
});

let s=defaultState(),toastTimer;

function toast(msg){
const el=$("toast");
el.textContent=msg;
el.style.display="block";
clearTimeout(toastTimer);
toastTimer=setTimeout(()=>el.style.display="none",2600);
}

function incomeRate(){
return s.items.filter(it=>s.equipped.includes(it.id))
.reduce((sum,it)=>sum+(Number(it.income)||0),0);
}

function maxHp(){
return Math.round(locations[s.location].hp*(1+s.hpLevel*.4));
}

function save(){
s.lastTime=Date.now();
try{localStorage.setItem("blockHunterSave",JSON.stringify(s))}catch(e){}
}

function load(){
try{
const raw=localStorage.getItem("blockHunterSave");
if(raw)s={...defaultState(),...JSON.parse(raw)};
}catch(e){s=defaultState()}

s.items=Array.isArray(s.items)?s.items:[];
s.equipped=Array.isArray(s.equipped)?s.equipped:[];
s.upgrades={...defaultState().upgrades,...(s.upgrades||{})};
s.unlocked=[...new Set([0,...(s.unlocked||[])])];
s.achievements=Array.isArray(s.achievements)?s.achievements:[];

const incomeByKey={Common:.1,Uncommon:.5,Rare:2,Epic:8,Legendary:30,Mythic:100,Secret:500};
s.items.forEach(it=>{
if(typeof it.income!=="number")it.income=incomeByKey[it.key]||.1;
if(!it.key){
const r=rarities.find(x=>x.name===it.rarity);
if(r)it.key=r.key;
}
});

s.equipped=s.equipped.filter(id=>s.items.some(it=>it.id===id));
s.location=Math.max(0,Math.min(locations.length-1,Number(s.location)||0));
s.currentHp=Math.max(1,Number(s.currentHp)||locations[s.location].hp);

const elapsed=Math.min(28800,Math.max(0,(Date.now()-(s.lastTime||Date.now()))/1000));
const offline=Math.floor(elapsed*incomeRate());

if(offline>0){
s.coins+=offline;
s.passive+=offline;
setTimeout(()=>toast("Пока тебя не было: +"+offline.toLocaleString("ru-RU")+" 🪙"),300);
}
}

function update(){
$("coins").textContent=Math.floor(s.coins).toLocaleString("ru-RU");
$("level").textContent=s.level;
$("xptext").textContent=`${s.xp} / ${s.level*100} XP`;
$("xpbar").style.width=(s.xp/(s.level*100)*100)+"%";
$("powerStat").textContent=s.damage;
$("critStat").textContent=s.crit+"%";
$("luckStat").textContent=s.luck;
$("hptext").textContent=`${Math.ceil(s.currentHp)} / ${maxHp()}`;
$("hpbar").style.width=Math.max(0,s.currentHp/maxHp()*100)+"%";
$("income").textContent=incomeRate().toLocaleString("ru-RU");
$("itemCount").textContent=s.items.length;
$("locationTitle").textContent=locations[s.location].name;
$("locationDesc").textContent=locations[s.location].desc;
$("blockname").textContent="БЛОК УРОВНЯ "+(s.location+1);
$("block").textContent=locations[s.location].emoji;
renderLocations();
renderItems();
renderUpgrades();
renderCollection();
renderAchievements();
renderStats();
}

function renderLocations(){
$("locations").innerHTML=locations.map((l,i)=>{
const unlocked=s.unlocked.includes(i);
return `<button class="loc ${i===s.location?"active":""}" data-loc="${i}" ${!unlocked?"disabled":""}>${l.emoji} ${l.short}<small>${unlocked?(i===s.location?"Текущая локация":"Открыта"):l.cost.toLocaleString("ru-RU")+" 🪙"}</small></button>`;
}).join("");

document.querySelectorAll("[data-loc]").forEach(b=>{
b.onclick=()=>changeLocation(+b.dataset.loc);
});
}

function changeLocation(i){
if(!s.unlocked.includes(i)){
const cost=locations[i].cost;
if(s.coins<cost)return toast("Нужно ещё "+(cost-s.coins)+" монет.");
s.coins-=cost;
s.unlocked.push(i);
toast("Локация открыта!");
}
s.location=i;
s.currentHp=maxHp();
$("damageText").textContent="Новая территория. Начинай добычу!";
update();
save();
}

/*
ДРОП:
30% — предмет не выпадает.
70% — предмет выпадает.
После успешного дропа редкость выбирается по весам:
45 + 25 + 15 + 8 + 5 + 1.8 + 0.2 = 100%.
Удача повышает общий шанс дропа максимум до 90%.
*/
function rollItem(){
const dropChance=Math.min(90,70+s.luck*2);

if(Math.random()*100>=dropChance){
s.emptyDrops++;
return null;
}

s.drops++;

const pick=Math.random()*100;
let total=0;
let rarity=rarities[0];

for(const r of rarities){
total+=r.weight;
if(pick<total){
rarity=r;
break;
}
}

const pool=rarity.key==="Secret"?secretPool:itemPool;
const chosen=pool[Math.floor(Math.random()*pool.length)];
const value=Math.max(2,Math.round(
locations[s.location].reward*rarity.mult*(.7+Math.random()*.6)
));
const income=Math.round(rarity.income*(1+s.location*.5)*10)/10;

return{
id:Date.now()+"-"+Math.random().toString(36).slice(2),
icon:chosen[0],
name:chosen[1],
rarity:rarity.name,
key:rarity.key,
value,income,location:s.location
};
}

function gainXp(n){
s.xp+=n;
while(s.xp>=s.level*100){
s.xp-=s.level*100;
s.level++;
s.coins+=s.level*20;
toast("Уровень повышен! Уровень "+s.level);
}
}

function hitBlock(){
s.clicks++;
const critical=Math.random()*100<s.crit;
const damage=s.damage*(critical?2:1);
s.currentHp-=damage;
if(critical)s.critHits++;

$("damageText").textContent=(critical?"💥 КРИТИЧЕСКИЙ УДАР! ":"⚔️ Урон: ")+damage;
$("block").classList.remove("hit");
void $("block").offsetWidth;
$("block").classList.add("hit");

if(s.currentHp<=0){
const reward=locations[s.location].reward;
s.coins+=reward;
s.blocks++;
gainXp(20+s.location*10);

const item=rollItem();
s.currentHp=maxHp();

if(item){
s.items.unshift(item);
$("damageText").textContent=`💰 +${reward} монет · ${item.icon} ${item.name} · ${item.rarity}`;
$("notice").textContent=`Найдено: ${item.rarity} · +${item.income} монет/сек при установке.`;

if(item.key==="Secret"){
toast("✦ СЕКРЕТНЫЙ ДРОП! "+item.name+" ✦");
}else if(item.key==="Mythic"){
toast("💜 МИФИЧЕСКИЙ ДРОП! "+item.name);
}else if(item.key==="Legendary"){
toast("✨ ЛЕГЕНДАРНЫЙ ДРОП! "+item.name);
}else{
toast("🎁 Найден предмет: "+item.name);
}
}else{
$("damageText").textContent=`💰 +${reward} монет · Ничего не выпало`;
$("notice").textContent="На этот раз без добычи. Разрушай следующий блок!";
}

$("block").classList.remove("broken");
void $("block").offsetWidth;
$("block").classList.add("broken");
checkAchievements();
}
update();
save();
}

$("hit").onclick=hitBlock;
$("block").onclick=hitBlock;

function renderItems(){
if(!s.items.length){
$("items").innerHTML='<div class="muted">Инвентарь пуст. Сломай первый блок, чтобы найти предметы.</div>';
return;
}

$("items").innerHTML=s.items.slice(0,100).map(it=>{
const equipped=s.equipped.includes(it.id);
return `<div class="item">
<div class="itemicon">${it.icon}</div>
<div class="iteminfo">
<b>${it.name}</b>
<div class="rarity ${it.key}">${it.rarity}</div>
<small>Доход: +${Number(it.income)||0}/сек</small>
<small>Продажа: ${Number(it.value)||0} 🪙</small>
</div>
<button class="btn" data-equip="${it.id}">${equipped?"Снять":"Установить"}</button>
<button class="btn" data-sell="${it.id}">Продать</button>
</div>`;
}).join("");

document.querySelectorAll("[data-equip]").forEach(b=>{
b.onclick=()=>{
const id=b.dataset.equip;
if(s.equipped.includes(id)){
s.equipped=s.equipped.filter(x=>x!==id);
toast("Предмет снят с коллекции");
}else{
s.equipped.push(id);
toast("Предмет установлен! Доход увеличен.");
}
update();
save();
};
});

document.querySelectorAll("[data-sell]").forEach(b=>{
b.onclick=()=>{
const id=b.dataset.sell;
const index=s.items.findIndex(it=>it.id===id);
if(index<0)return;
if(s.equipped.includes(id))return toast("Сначала сними предмет из коллекции!");
const [it]=s.items.splice(index,1);
s.coins+=Number(it.value)||0;
toast("Продано: +"+it.value+" монет");
update();
save();
};
});
}

function renderUpgrades(){
$("upgradeList").innerHTML=upgradeDefs.map(u=>{
const lv=s.upgrades[u.id]||0;
const cost=Math.floor(u.base*Math.pow(1.75,lv));
return `<div class="upgrade">
<div class="upicon">${u.icon}</div>
<div class="upinfo">
<b>${u.name} · ур. ${lv}</b>
<small>${u.desc}</small>
<small>Цена: ${cost.toLocaleString("ru-RU")} 🪙</small>
</div>
<button class="btn" data-up="${u.id}">Улучшить</button>
</div>`;
}).join("");

document.querySelectorAll("[data-up]").forEach(b=>{
b.onclick=()=>{
const id=b.dataset.up;
const u=upgradeDefs.find(x=>x.id===id);
const lv=s.upgrades[id]||0;
const cost=Math.floor(u.base*Math.pow(1.75,lv));
if(s.coins<cost)return toast("Недостаточно монет.");

s.coins-=cost;
s.upgrades[id]=lv+1;

if(id==="power")s.damage++;
if(id==="crit")s.crit=Math.min(75,s.crit+3);
if(id==="luck")s.luck++;
if(id==="hp"){
s.hpLevel++;
s.currentHp=maxHp();
}

toast(u.name+" улучшено!");
update();
save();
};
});
}

function renderCollection(){
const equipped=s.items.filter(it=>s.equipped.includes(it.id));

if(!equipped.length){
$("collectionList").innerHTML='<div class="muted">Коллекция пуста. Установи предмет в инвентаре.</div>';
return;
}

$("collectionList").innerHTML=equipped.map(it=>`
<div class="item">
<div class="itemicon">${it.icon}</div>
<div class="iteminfo">
<b>${it.name}</b>
<div class="rarity ${it.key}">${it.rarity}</div>
<small>+${it.income} монет/сек</small>
</div>
<button class="btn" data-remove="${it.id}">Снять</button>
</div>
`).join("");

document.querySelectorAll("[data-remove]").forEach(b=>{
b.onclick=()=>{
s.equipped=s.equipped.filter(id=>id!==b.dataset.remove);
update();
save();
toast("Предмет снят с коллекции");
};
});
}

const achievementDefs=[
{id:"first",name:"Первый удар",desc:"Сломай первый блок.",check:()=>s.blocks>=1,reward:25},
{id:"ten",name:"Разрушитель",desc:"Сломай 10 блоков.",check:()=>s.blocks>=10,reward:100},
{id:"hundred",name:"Сотня разрушений",desc:"Сломай 100 блоков.",check:()=>s.blocks>=100,reward:1000},
{id:"rare",name:"Охотник за редкостями",desc:"Найди эпический предмет или лучше.",check:()=>s.items.some(i=>["Epic","Legendary","Mythic","Secret"].includes(i.key)),reward:250},
{id:"secret",name:"За гранью реальности",desc:"Найди секретный предмет.",check:()=>s.items.some(i=>i.key==="Secret"),reward:5000},
{id:"rich",name:"Первое состояние",desc:"Накопи 1000 монет.",check:()=>s.coins>=1000,reward:200},
{id:"level10",name:"Опытный охотник",desc:"Достигни 10 уровня.",check:()=>s.level>=10,reward:1000}
];

function checkAchievements(){
for(const a of achievementDefs){
if(!s.achievements.includes(a.id)&&a.check()){
s.achievements.push(a.id);
s.coins+=a.reward;
toast("Ачивка: "+a.name+" · +"+a.reward+" 🪙");
}
}
}

function renderAchievements(){
$("achievementList").innerHTML=achievementDefs.map(a=>{
const done=s.achievements.includes(a.id);
return `<div class="achievement">
<b>${done?"✅":"🔒"} ${a.name}</b>
<div class="muted" style="margin-top:6px">${a.desc}</div>
<div class="muted" style="margin-top:5px">${done?"Получено":"Награда: "+a.reward+" 🪙"}</div>
</div>`;
}).join("");
}

function renderStats(){
$("statsList").innerHTML=`
<div class="stat" style="margin-bottom:8px"><b>${s.blocks}</b><small>СЛОМАНО БЛОКОВ</small></div>
<div class="stat" style="margin-bottom:8px"><b>${s.clicks}</b><small>ВСЕГО УДАРОВ</small></div>
<div class="stat" style="margin-bottom:8px"><b>${s.critHits}</b><small>КРИТИЧЕСКИХ УДАРОВ</small></div>
<div class="stat" style="margin-bottom:8px"><b>${s.items.length}</b><small>ПРЕДМЕТОВ В ИНВЕНТАРЕ</small></div>
<div class="stat" style="margin-bottom:8px"><b>${s.drops}</b><small>УСПЕШНЫХ ДРОПОВ</small></div>
<div class="stat" style="margin-bottom:8px"><b>${s.emptyDrops}</b><small>БЛОКОВ БЕЗ ДРОПА</small></div>
<div class="stat" style="margin-bottom:8px"><b>${Math.floor(s.passive)}</b><small>ЗАРАБОТАНО ПАССИВНО</small></div>
<div class="stat" style="margin-bottom:12px"><b>${s.unlocked.length}/${locations.length}</b><small>ОТКРЫТО ЛОКАЦИЙ</small></div>`;
$("sound").textContent=s.sound?"🔇 Выключить звук":"🔊 Включить звук";
}

function playSound(){
if(!s.sound)return;
try{
const C=window.AudioContext||window.webkitAudioContext;
const c=new C(),o=c.createOscillator(),g=c.createGain();
o.type="square";
o.frequency.value=120;
g.gain.value=.035;
o.connect(g);
g.connect(c.destination);
o.start();
o.stop(c.currentTime+.06);
o.onended=()=>c.close();
}catch(e){}
}

$("hit").addEventListener("click",playSound);
$("block").addEventListener("click",playSound);

$("sound").onclick=()=>{
s.sound=!s.sound;
update();
save();
};

$("save").onclick=()=>{
save();
toast("Прогресс сохранён!");
};

$("reset").onclick=()=>{
if(confirm("Точно сбросить весь прогресс? Это нельзя отменить.")){
localStorage.removeItem("blockHunterSave");
s=defaultState();
s.currentHp=maxHp();
update();
save();
toast("Игра начата заново");
}
};

document.querySelectorAll("[data-tab]").forEach(b=>{
b.onclick=()=>{
document.querySelectorAll("[data-tab]").forEach(x=>x.classList.toggle("active",x===b));
document.querySelectorAll(".section").forEach(x=>x.classList.toggle("active",x.id===b.dataset.tab));
};
});

load();
update();

let lastTick=Date.now();

setInterval(()=>{
const now=Date.now();
const elapsed=Math.min(5,(now-lastTick)/1000);
lastTick=now;
const earned=incomeRate()*elapsed;

if(earned>0){
s.coins+=earned;
s.passive+=earned;
update();
save();
}
},1000);

setInterval(save,15000);
window.addEventListener("beforeunload",save);
</script>
</body>
</html>
