/* ======================================================
   DSCM ALUMNI – app.js
   Dark Nostalgic Emotional Theme
   Full admin control + match modes
   ====================================================== */

// ====== FIREBASE INIT ======
const firebaseConfig = {
  apiKey: "AIzaSyCUZI6yea-5uByGIjS7x2ubCtUZD0ls1VU",
  authDomain: "dscmclass123.firebaseapp.com",
  databaseURL: "https://dscmclass123-default-rtdb.firebaseio.com",
  projectId: "dscmclass123",
  storageBucket: "dscmclass123.firebasestorage.app",
  messagingSenderId: "230184692671",
  appId: "1:230184692671:web:c0a42ca1fd0c39ab640f0a",
  measurementId: "G-8Q304W2HHY"
};
firebase.initializeApp(firebaseConfig);
const db = firebase.database();
let storage;
try { storage = firebase.storage(); } catch(e) { console.warn("Storage not initialized", e); }

// ====== DATA ======
const DEF = {
  students:[
    {id:1,name:"Aarav Sharma",nick:"Ace",gender:"male",quote:"Dream big, work hard.",img:"",visible:true},
    {id:2,name:"Priya Patel",nick:"Princess",gender:"female",quote:"Be the change you wish to see.",img:"",visible:true},
  ],
  gallery:[
    {id:1,url:"https://images.unsplash.com/photo-1523050854058-8df90110c8f1?w=400&h=400&fit=crop",caption:"Annual Day 2025",cat:"Events"},
  ],
  memories:[
    {id:1,author:"Aarav",text:"Remember when we had that surprise test and nobody had studied? 😂 Best day ever!",time:Date.now()-86400000,likes:5,likedBy:[],approved:true},
  ],
  matchCfg:{mode:"random",fixedId:null,biasId:null,biasWeight:5,messages:["You two were meant to be! 💕","Match made in heaven! ✨"],excludeIds:[]},
  heroCfg:{
    bg1:'https://images.unsplash.com/photo-1523050854058-8df90110c8f1?w=1200&q=80', tag:'Class 12 · Batch 2025–26', title:'Forever <span class="gold">DSCM</span>', sub:'We came as strangers, left as memories.', school:'DSCM English Medium Higher Secondary School',
    bg2:'https://images.unsplash.com/photo-1577896851231-70ef18881754?w=1200&q=80', story1:'"Every classroom held a story..."', storySub:'Laughter in the corridors, friendships in the benches', cap2:'Memories 📸',
    bg3:'https://images.unsplash.com/photo-1427504494785-3a9ca7044f45?w=1200&q=80', story2:'"And every goodbye became a memory ❤️"', cap3:'Farewell ✨'
  },
  loaderCfg:{
    icon:'🎓', text:'Forever DSCM', sub:'Loading memories...',
    creatorName:'Debangshu Sen', creatorLink:'https://www.instagram.com/debangshusen15', copyright:'CLASS 12 ( 2025-26 )', tagline:'All memories are preserved forever ❤️', globalFont:'Inter',
    stuSub:'The ones who made these years golden', galTitle:'Gallery', galSub:'Snapshots of our golden days', 
    memTitle:'Message Wall of Reflection', memSub:'A space to leave your final words, memories, and wishes.',
    heroCta:'Explore Our Memories →', introTitle:'Memories', introSub:'A collection of moments that defined us.',
    ybTitle:'CLASS 12 BATCH', ybSub:'(2025-26)', ybHint:'Click to flip the story 📖',
    archiveLink:'',
    visStu:true, visGal:true, visWall:true, visMatch:true, visYb:true
  },
  adminPassword:"a%$5044444$$",
  nextStuId:3,nextGalId:10,nextMemId:4,nextHeroSlideId:1,
  heroSlides:[],
  yearbook:[
    {id:1, title:"The First Day",text:"Fresh faces...",img:"https://images.unsplash.com/photo-1523050854058-8df90110c8f1?w=600&q=80"}
  ]
};

let D = JSON.parse(JSON.stringify(DEF));

// ====== FIREBASE SYNC ======
function save(){
  db.ref('siteData').set(D).then(()=>{
    toast('Live database updated! 🌏','ok');
  }).catch(e=>{
    toast('Sync Error','err');
    localStorage.setItem('dscm_backup', JSON.stringify(D));
  });
}

function loadLive() {
  db.ref('siteData').once('value').then(snap => {
    const data = snap.val();
    if(data) {
      D = data;
      if (typeof ensureCodes === 'function') ensureCodes();
      applyLoaderUI();
      applyHeroUI();       // ← apply saved hero backgrounds & text
      renderYearbook();
      applyLayoutUI();     // ← was wrongly called as updateLayoutUI()
      applyAppearanceUI();
      applyFooterUI();
      if(curPage === 'hero') setupHeroScroll();
      toast('Live Sync Active ✅', 'ok');
    } else {
      // First time - push defaults
      save();
    }
  });
}

// Initial Load
document.addEventListener('DOMContentLoaded', () => {
  loadLive();
});

function applyLoaderUI(){
  const c=D.loaderCfg||DEF.loaderCfg;
  const e=(id,val)=>{if(document.getElementById(id))document.getElementById(id).textContent=val;};
  e('plIcon',c.icon); e('plText',c.text); e('plSub',c.sub);
  
  // Footer Sync
  document.querySelectorAll('[id^="fCreator"]').forEach(el=>{ el.href=c.creatorLink||'https://www.instagram.com/debangshusen15'; el.textContent='Made by '+(c.creatorName||'Debangshu Sen'); });
  document.querySelectorAll('[id^="fCopy"]').forEach(el=> el.textContent=c.copyright||'CLASS 12 ( 2025-26 )');
  document.querySelectorAll('[id^="fTagline"]').forEach(el=> el.textContent=c.tagline||'All memories are preserved forever ❤️');

  // Visibility Logic
  const tog=(sec,nav,vis)=>{
    const el=document.getElementById(sec); if(el) el.style.display=vis?'block':'none';
    const n=document.querySelector(`[data-p="${nav}"]`); if(n) n.style.display=vis?'flex':'none';
  };
  tog('students','students',c.visStu);
  tog('gallery','gallery',c.visGal);
  tog('memories','memories',c.visWall);
  tog('match','match',c.visMatch);
  tog('yearbook','yearbook',c.visYb);
}
applyLoaderUI();

// ====== NAVIGATION ======
let curPage='hero';
let lastHomeTap = 0;
// navigateTo is defined below (single authoritative version)
function initParticles(){
  if(document.getElementById('particleWrap')) return;
  const w=document.createElement('div');w.id='particleWrap';w.className='particle-wrap';
  w.style.pointerEvents = 'none';
  w.style.zIndex = '50';
  document.body.appendChild(w);

  // Emojis
  const emojis=['✨','🎓','📸','💫','❤️','🌟','🕊️','📝','📚','🎒','🚌','✍️','🎨','⚽','🏫'];
  for(let i=0;i<30;i++){
    const p=document.createElement('div');p.className='particle';
    p.textContent=emojis[Math.floor(Math.random()*emojis.length)];
    p.style.left=Math.random()*100+'vw';
    p.style.animationDuration=(15+Math.random()*25)+'s';
    p.style.animationDelay='-'+(Math.random()*15)+'s';
    p.style.fontSize=(14+Math.random()*22)+'px';
    p.style.opacity=(0.06+Math.random()*0.15).toFixed(2);
    w.appendChild(p);
  }

  // Glitter
  const glitters=['✦','⋆','✨','⁺','⭐'];
  for(let j=0;j<45;j++){
    const g=document.createElement('div');g.className='particle glit';
    g.textContent=glitters[Math.floor(Math.random()*glitters.length)];
    g.style.left=Math.random()*100+'vw';
    g.style.top=Math.random()*100+'vh';
    g.style.animationDuration=(4+Math.random()*8)+'s';
    g.style.animationDelay='-'+(Math.random()*7)+'s';
    g.style.fontSize=(10+Math.random()*15)+'px';
    g.style.color=Math.random()>.5?'var(--gold)':'#fff';
    w.appendChild(g);
  }

  // Paper Plane
  const plane=document.createElement('div');
  plane.className='paper-plane'; plane.textContent='✈️';
  w.appendChild(plane);

  // Doodles
  const doodles=['BFFs forever','xoxo','Class of 2026','Miss you all','Best days <3','12th Grade!','DSCM Souls'];
  for(let k=0;k<doodles.length;k++){
    const d=document.createElement('div');d.className='doodle-text';
    d.textContent=doodles[k];
    d.style.left=(10+Math.random()*70)+'vw';
    d.style.top=(15+Math.random()*75)+'vh';
    d.style.transform=`rotate(${(Math.random()*30)-15}deg)`;
    d.style.animationDelay=(Math.random()*12)+'s';
    w.appendChild(d);
  }
}
function updateNav(){
  document.querySelectorAll('.bnav-btn').forEach(b=>b.classList.toggle('active',b.dataset.p===curPage));
  const pw=document.getElementById('particleWrap');
  if(pw)pw.style.display=(curPage==='hero')?'block':'none';
}
function trigReveals(c){c.querySelectorAll('.reveal-up').forEach((e,i)=>setTimeout(()=>e.classList.add('vis'),i*70));}

// ====== HERO SCROLL ======
function setupHeroScroll(){
  const obs=new IntersectionObserver((ents)=>{
    ents.forEach(e=>{
      if(e.isIntersecting){
        if(e.target.id==='heroContent1') e.target.classList.add('hc-visible');
        else e.target.classList.add('hc-vis'); // Using hc-vis for timeline slides
      }
      else{
        if(e.target.id==='heroContent1') e.target.classList.remove('hc-visible');
        else e.target.classList.remove('hc-vis');
      }
    });
  },{threshold:0.4});
  document.querySelectorAll('.hero-content').forEach(c=>obs.observe(c));
}

// ====== STUDENTS ======
function em(g){return g==='female'?'👩':'👦';}
function ini(n){return n.split(' ').map(w=>w[0]).join('').toUpperCase().slice(0,2);}

function renderStudents(){
  const q=(document.getElementById('studentSearch')?.value||'').toLowerCase();
  const list=D.students.filter(s=>s.visible!==false&&(s.name.toLowerCase().includes(q)||s.nick.toLowerCase().includes(q)));
  document.getElementById('studentsGrid').innerHTML=list.map((s,i)=>`
    <div class="stu-card" style="animation-delay:${i*.04}s" onclick="openStu(${s.id})">
      <div class="stu-ava">${s.img?`<img src="${s.img}" alt="${s.name}" loading="lazy"/>`  :em(s.gender)}</div>
      <div class="stu-name">${s.name}</div>
      <div class="stu-nick">${s.nick}</div>
    </div>`).join('');
}
function filterStudents(){renderStudents();}

function openStu(id){
  const s=D.students.find(x=>x.id===id);if(!s)return;
  document.getElementById('modalBody').innerHTML=`
    <div class="mp-center">
      <div class="mp-ava">${s.img?`<img src="${s.img}"/>`  :em(s.gender)}</div>
      <div class="mp-name">${s.name}</div>
      <div class="mp-nick">"${s.nick}"</div>
      ${s.quote?`<div class="mp-quote">"${s.quote}"</div>`:''}
      <div class="mp-socials">
        ${s.ig?`<a href="https://instagram.com/${s.ig.replace('@','')}" target="_blank" class="social-btn ig">📸 Instagram</a>`:''}
        ${s.fb?`<a href="${s.fb.startsWith('http')?s.fb:'https://'+s.fb}" target="_blank" class="social-btn fb">📘 Facebook</a>`:''}
      </div>
      ${s.stuMedia?`<a href="${s.stuMedia.startsWith('http')?s.stuMedia:'https://'+s.stuMedia}" target="_blank" class="btn-gold" style="display:block; text-align:center; margin-top:20px; font-weight:600; text-decoration:none;"><span style="font-size:18px; margin-right:8px;">🎞️</span> View My Memories</a>`:''}
    </div>`;
  document.getElementById('studentModal').classList.add('open');
  document.body.style.overflow='hidden';
  history.pushState({modalOpen: true}, '');
}

function closeModal(fromPopState = false){
  const m = document.getElementById('studentModal');
  if(!m.classList.contains('open')) return;
  m.classList.remove('open');
  document.body.style.overflow='';
  if(fromPopState !== true) history.back();
}

// ====== GALLERY ======
let galCat='All', lbI=0;

function renderGalleryCats(){
  const cats=['All',...new Set(D.gallery.map(g=>g.cat||'Uncategorized'))];
  document.getElementById('galleryCats').innerHTML=cats.map(c=>
    `<button class="gcat${c===galCat?' on':''}" onclick="setGalCat('${c}')">${c}</button>`
  ).join('');
}
function setGalCat(c){galCat=c;renderGalleryCats();renderGallery();}

function renderGallery(){
  const c = D.loaderCfg || DEF.loaderCfg;
  const list=galCat==='All'?D.gallery:D.gallery.filter(g=>(g.cat||'Uncategorized')===galCat);
  const activeList = list.filter(g => g.approved !== false);
  let html = activeList.map((g,i)=>`
    <div class="gal-item" style="animation-delay:${i*.05}s" onclick="openLB(${D.gallery.indexOf(g)})">
      ${g.type==='video'?`<video src="${g.url}" preload="metadata" muted playsinline></video><div class="vid-icon">▶ Video</div>`:`<img src="${g.url}" alt="${g.caption}" loading="lazy"/>`}
      <div class="gc">${g.caption}</div>
    </div>`).join('');
  if (c.archiveLink) {
    html += `
      <div style="grid-column: 1 / -1; display:flex; flex-direction:column; align-items:center; padding: 40px 10px; background:rgba(212, 168, 83, 0.05); border:1px dashed var(--gold2); border-radius:12px; margin-top:20px; text-align:center;">
        <h3 style="color:var(--gold); font-size:18px; margin-bottom:8px;">Wait, there is more!</h3>
        <p style="color:var(--txt3); font-size:14px; margin-bottom:20px;">We have a massive collection of 4,000+ unedited memories archived securely on Google Drive.</p>
        <button class="btn-gold" style="width:auto; padding:10px 24px; font-weight:600;" onclick="window.open('${c.archiveLink}', '_blank')">
          Access Full Photo Archive ☁️
        </button>
      </div>
    `;
  }
  document.getElementById('galleryGrid').innerHTML = html;
}

function openLB(i){lbI=i;const g=D.gallery[i];
  const img=document.getElementById('lbImg'), vid=document.getElementById('lbVid');
  if(g.type==='video'){img.style.display='none';vid.style.display='block';vid.src=g.url;vid.play();}
  else{vid.style.display='none';vid.pause();img.style.display='block';img.src=g.url;}
  document.getElementById('lbCap').textContent=g.caption;
  document.getElementById('lightbox').classList.add('open');document.body.style.overflow='hidden';
  history.pushState({lbOpen: true}, '');
}
function closeLB(fromPopState = false){
  const lb = document.getElementById('lightbox');
  if(!lb.classList.contains('open')) return;
  lb.classList.remove('open');
  document.body.style.overflow='';
  document.getElementById('lbVid').pause();
  if(fromPopState !== true) history.back();
}
function lbPrev(){lbI=(lbI-1+D.gallery.length)%D.gallery.length;updLB();}
function lbNext(){lbI=(lbI+1)%D.gallery.length;updLB();}
function updLB(){const img=document.getElementById('lbImg'),vid=document.getElementById('lbVid');
  img.style.opacity='0';img.style.transform='scale(.92)';vid.style.opacity='0';vid.style.transform='scale(.92)';
  setTimeout(()=>{const g=D.gallery[lbI];
    if(g.type==='video'){img.style.display='none';vid.style.display='block';vid.src=g.url;vid.play();vid.style.opacity='1';vid.style.transform='scale(1)';}
    else{vid.style.display='none';vid.pause();img.style.display='block';img.src=g.url;img.style.opacity='1';img.style.transform='scale(1)';}
    document.getElementById('lbCap').textContent=g.caption;},180);}

async function downloadCurrentMedia() {
    const g = D.gallery[lbI];
    if(!g || !g.url) return;
    try {
        toast('Downloading... ⏳', 'ok');
        const res = await fetch(g.url);
        const blob = await res.blob();
        const url = window.URL.createObjectURL(blob);
        const a = document.createElement('a');
        a.href = url;
        const ext = g.type === 'video' ? 'mp4' : 'jpg';
        a.download = `DSCM_Memory_${g.id}_${Date.now()}.${ext}`;
        document.body.appendChild(a);
        a.click();
        a.remove();
        window.URL.revokeObjectURL(url);
    } catch(e) {
        // Fallback for CORS issues
        const a = document.createElement('a');
        a.href = g.url;
        a.target = '_blank';
        a.download = `DSCM_Memory_${g.id}`;
        document.body.appendChild(a);
        a.click();
        a.remove();
    }
}

// Touch swipe
let tx=0;
document.addEventListener('DOMContentLoaded',()=>{
  const lb=document.getElementById('lightbox');
  lb.addEventListener('touchstart',e=>{tx=e.touches[0].clientX;},{passive:true});
  lb.addEventListener('touchend',e=>{const d=tx-e.changedTouches[0].clientX;if(Math.abs(d)>50){d>0?lbNext():lbPrev();}});
});

// ====== MEMORY WALL ======
function renderMemories(){
  const approved=D.memories.filter(m=>m.approved).sort((a,b)=>b.time-a.time);
  document.getElementById('memFeed').innerHTML=approved.map((m,i)=>`
    <div class="mem-card" style="animation-delay:${i*.07}s; --rot:${Math.random() * 4 - 2}deg;">
      <div class="mc-body">"${esc(m.text)}"</div>
      <div class="mc-head">
        <div class="mc-name">${esc(m.author)}</div>
        <button class="mc-like ${m.likedBy?.includes('u')?'liked':''}" onclick="togLike(${m.id})">
          <span class="lh">${m.likedBy?.includes('u')?'❤️':'🤍'}</span><span>${m.likes}</span>
        </button>
      </div>
    </div>`).join('');
}

function submitMemory(){
  const a=document.getElementById('memAuthor').value.trim(),t=document.getElementById('memText').value.trim();
  if(!a||!t){toast('Fill in both fields','err');return;}
  D.memories.push({id:D.nextMemId++,author:a,text:t,time:Date.now(),likes:0,likedBy:[],approved:false});
  save();document.getElementById('memAuthor').value='';document.getElementById('memText').value='';
  toast('Memory submitted for approval! ✨','ok');
}

function togLike(id){
  const m=D.memories.find(x=>x.id===id);if(!m)return;if(!m.likedBy)m.likedBy=[];
  const i=m.likedBy.indexOf('u');
  if(i>-1){m.likedBy.splice(i,1);m.likes=Math.max(0,m.likes-1);}else{m.likedBy.push('u');m.likes++;}
  save();renderMemories();
}

function ago(ts){const d=Date.now()-ts,m=Math.floor(d/60000),h=Math.floor(d/3600000),dy=Math.floor(d/86400000);
  if(m<1)return'Just now';if(m<60)return m+'m ago';if(h<24)return h+'h ago';if(dy<7)return dy+'d ago';return new Date(ts).toLocaleDateString();}
function esc(t){const d=document.createElement('div');d.textContent=t;return d.innerHTML;}

// ====== MATCH GAME ======
let selG='';
function pickGender(g){selG=g;document.querySelectorAll('.gender-btn').forEach(b=>b.classList.toggle('on',b.dataset.g===g));}

function findMatch(){
  const name=document.getElementById('matchName').value.trim();
  if(!name){toast('Enter your name','err');return;}
  if(!selG){toast('Select your gender','err');return;}

  const cfg=D.matchCfg||{mode:'random',excludeIds:[],messages:[]};
  const opp=selG==='male'?'female':'male';
  let pool=D.students.filter(s=>s.gender===opp&&s.visible!==false&&!(cfg.excludeIds||[]).includes(s.id));
  if(!pool.length){toast('No matches available!','err');return;}

  // Show loading
  document.getElementById('matchForm').style.display='none';
  document.getElementById('matchAnim').style.display='block';

  const getF = s => s.img ? `<img src="${s.img}" style="width:100%;height:100%;object-fit:cover;"/>` : em(s.gender);
  const c1=document.querySelector('.s1'),c2=document.querySelector('.s2');
  c1.innerHTML=em(selG);let cnt=0;
  const si=setInterval(()=>{c2.innerHTML=getF(pool[Math.floor(Math.random()*pool.length)]);if(++cnt>16)clearInterval(si);},110);

  setTimeout(()=>{
    let match;
    if(cfg.mode==='fixed'&&cfg.fixedId){
      match=D.students.find(s=>s.id===cfg.fixedId);
    }else if(cfg.mode==='biased'&&cfg.biasId){
      // weighted random
      const weighted=[];
      pool.forEach(s=>{
        const w=s.id===cfg.biasId?(cfg.biasWeight||5):1;
        for(let i=0;i<w;i++)weighted.push(s);
      });
      match=weighted[Math.floor(Math.random()*weighted.length)];
    }else{
      match=pool[Math.floor(Math.random()*pool.length)];
    }
    if(!match)match=pool[0];
    const compat=Math.floor(Math.random()*31)+70;
    const msgs=cfg.messages?.length?cfg.messages:["You two were meant to be! 💕"];
    const msg=msgs[Math.floor(Math.random()*msgs.length)];

    document.getElementById('matchAnim').style.display='none';
    document.getElementById('matchRes').style.display='block';
    
    // Change final shuffle box to matched user photo
    c2.innerHTML=getF(match);
    
    const resAva = s => s.img ? `<img src="${s.img}" style="width:28px;height:28px;border-radius:50%;object-fit:cover;margin-right:8px;border:1px solid var(--border);vertical-align:middle;"/>` : `<span class="rpe">${em(s.gender)}</span>`;
    
    document.getElementById('resP1').innerHTML=`<span class="rpe">${em(selG)}</span><span class="rpn">${name}</span>`;
    document.getElementById('resP2').innerHTML=`${resAva(match)}<span class="rpn">${match.name}</span>`;
    document.getElementById('resCompat').textContent=`${compat}% Compatible! 💕`;
    
    let dmHtml = '';
    if(match.ig || match.fb) {
      const dmLink = match.ig ? `https://instagram.com/${match.ig.replace('@','')}` : (match.fb.startsWith('http')?match.fb:'https://'+match.fb);
      dmHtml = `<br><br><a href="${dmLink}" target="_blank" class="btn-outline-light btn-dm">💌 Shoot your shot (DM)</a>`;
    }
    
    document.getElementById('resMsg').innerHTML=msg + dmHtml;
    confetti();
  },2800);
}

function resetMatch(){
  document.getElementById('matchForm').style.display='block';
  document.getElementById('matchAnim').style.display='none';
  document.getElementById('matchRes').style.display='none';
  document.getElementById('matchName').value='';selG='';
  document.querySelectorAll('.gender-btn').forEach(b=>b.classList.remove('on'));
}

function confetti(){
  const w=document.getElementById('confettiWrap');
  const cols=['#D4A853','#E8C170','#F5A623','#E8536C','#66BB6A','#4FC3F7'];
  for(let i=0;i<50;i++){const p=document.createElement('div');p.className='conf';p.style.left=Math.random()*100+'%';
    p.style.backgroundColor=cols[Math.floor(Math.random()*cols.length)];p.style.animationDuration=(2+Math.random()*2)+'s';
    p.style.animationDelay=Math.random()*.5+'s';p.style.width=(6+Math.random()*8)+'px';p.style.height=(6+Math.random()*8)+'px';
    p.style.borderRadius=Math.random()>.5?'50%':'2px';w.appendChild(p);}
  setTimeout(()=>{w.innerHTML='';},4000);
}

// ====== ADMIN ======
let isAdm=false;
let adminRole=null;
let loggedInUser=null;

function ensureCodes() {
   let updated = false;
   D.students.forEach(s => {
      if(!s.code) {
         s.code = Math.random().toString(36).substring(2,8).toUpperCase();
         updated = true;
      }
   });
   if(updated) save();
}

function doAdminLogin(){
  const u=document.getElementById('aUser').value.trim().toLowerCase();
  const p=document.getElementById('aPass').value.trim();
  
  if(u==='antiphile' && p===D.adminPassword){
     isAdm=true; adminRole='full'; loggedInUser=null;
     showAdminDash(); return;
  }
  
  const student = D.students.find(s => s.name.toLowerCase() === u && (s.code === p || p === D.adminPassword));
  if(student) {
     isAdm=true; loggedInUser=student;
     const lowerName = student.name.toLowerCase();
     if(lowerName.includes("debangshu sen") || lowerName.includes("mriganka basak")) {
        adminRole='full';
     } else if(lowerName.includes("biprajit basak")) {
        adminRole='limited';
     } else {
        adminRole='student';
     }
     showAdminDash();
  } else {
     document.getElementById('alErr').textContent='Invalid credentials or code';
     const c=document.querySelector('.admin-login-box');
     c.style.animation='none';c.offsetHeight;c.style.animation='shake .4s ease';
  }
}

function showAdminDash() {
    document.getElementById('adminLogin').style.display='none';
    document.getElementById('adminDash').style.display='block';
    
    document.querySelectorAll('.adtab').forEach(t => {
       const tabId = t.getAttribute('data-tab');
       if(!tabId) return; // for previous tabs without data-tab
       let show = true;
       if (adminRole === 'limited') {
           if (tabId !== 'adt-gallery' && tabId !== 'adt-portal') show = false;
       } else if (adminRole === 'student') {
           if (tabId !== 'adt-portal') show = false;
       } else {
           if (tabId === 'adt-portal') show = false;
       }
       t.style.display = show ? 'inline-block' : 'none';
    });

    let defaultTab = 'adt-students';
    if (adminRole === 'student') {
        defaultTab = 'adt-portal';
        renderPortal();
    } else if (adminRole === 'limited') {
        defaultTab = 'adt-gallery';
        renderAStu(); renderAGal(); renderAMem(); renderAYb(); loadMatchCfg(); loadHeroCfg(); renderAHeroSlides(); loadSettingsCfg();
    } else {
        renderAStu(); renderAGal(); renderAMem(); renderAYb(); loadMatchCfg(); loadHeroCfg(); renderAHeroSlides(); loadSettingsCfg();
    }
    
    adTab(defaultTab);
    document.getElementById('alErr').textContent='';
    toast('Welcome ' + (loggedInUser ? loggedInUser.name.split(' ')[0] : 'Admin') + '! 👋', 'ok');
}

function doAdminLogout(){
   isAdm=false; adminRole=null; loggedInUser=null;
   document.getElementById('adminLogin').style.display='flex';
   document.getElementById('adminDash').style.display='none';
   document.getElementById('aUser').value='';document.getElementById('aPass').value='';
   toast('Logged out','ok');
}

function adTab(id){
  document.querySelectorAll('.adtab').forEach(t=>t.classList.remove('active'));
  document.querySelectorAll('.adpanel, .admin-tab-content').forEach(p=>p.classList.remove('active'));
  const btn = document.querySelector(`[onclick="adTab('${id}')"]`) || document.querySelector(`[onclick="showTab('${id}')"]`);
  if(btn) btn.classList.add('active');
  const target = document.getElementById(id);
  if(target) target.classList.add('active');
}
function showTab(id){ adTab(id); } // Alias for safety
function togForm(id){const f=document.getElementById(id);f.style.display=f.style.display==='none'?'block':'none';}

// Admin Students
function editStu(id) {
  const s = D.students.find(x=>x.id==id);
  if(!s) return;
  document.getElementById('fStuId').value = s.id;
  document.getElementById('fStuName').value = s.name;
  document.getElementById('fStuNick').value = s.nick;
  document.getElementById('fStuGender').value = s.gender;
  document.getElementById('fStuQuote').value = s.quote;
  document.getElementById('fStuImg').value = s.img;
  document.getElementById('fStuMedia').value = s.stuMedia || '';
  document.getElementById('fStuIg').value = s.ig||'';
  document.getElementById('fStuFb').value = s.fb||'';
  const f = document.getElementById('formAddStu');
  f.style.display='block';
  f.scrollIntoView({ behavior: 'smooth', block: 'start' });
}
function cancelStuForm() {
  document.getElementById('fStuId').value = '';
  ['fStuName','fStuNick','fStuGender','fStuQuote','fStuImg','fStuMedia','fStuIg','fStuFb'].forEach(i=>document.getElementById(i).value='');
  document.getElementById('formAddStu').style.display='none';
}
function addStu(){
  const editId = document.getElementById('fStuId').value;
  const n=document.getElementById('fStuName').value.trim(),nk=document.getElementById('fStuNick').value.trim(),
  g=document.getElementById('fStuGender').value,q=document.getElementById('fStuQuote').value.trim(),img=document.getElementById('fStuImg').value.trim(),
  media=document.getElementById('fStuMedia').value.trim(), ig=document.getElementById('fStuIg').value.trim(),fb=document.getElementById('fStuFb').value.trim();
  if(!n||!g){toast('Name & gender required','err');return;}
  
  if (editId) {
    const s = D.students.find(x=>x.id==editId);
    if(s) {
      s.name=n; s.nick=nk||n.split(' ')[0]; s.gender=g; s.quote=q; s.img=img; s.stuMedia=media; s.ig=ig; s.fb=fb;
      toast('Student updated! ✏️','ok');
    }
  } else {
    D.students.push({id:D.nextStuId++,name:n,nick:nk||n.split(' ')[0],gender:g,quote:q,img,stuMedia:media,ig,fb,visible:true});
    toast('Student added! 🎉','ok');
  }
  save(); cancelStuForm(); renderAStu();
}
function moveStuUp(id){
  const idx = D.students.findIndex(s=>s.id==id);
  if(idx > 0) {
    const temp = D.students[idx];
    D.students[idx] = D.students[idx-1];
    D.students[idx-1] = temp;
    save(); renderAStu(); renderStudents();
  }
}
function moveStuDown(id){
  const idx = D.students.findIndex(s=>s.id==id);
  if(idx > -1 && idx < D.students.length - 1) {
    const temp = D.students[idx];
    D.students[idx] = D.students[idx+1];
    D.students[idx+1] = temp;
    save(); renderAStu(); renderStudents();
  }
}
function delStu(id){if(!confirm('Remove?'))return;D.students=D.students.filter(s=>s.id!=id);save();renderAStu();toast('Removed','ok');}
function togVisStu(id){const s=D.students.find(x=>x.id==id);if(s){s.visible=!s.visible;save();renderAStu();toast(s.visible?'Shown':'Hidden','ok');}}
function reviewEdits(id) {
    const s = D.students.find(x=>x.id==id);
    if(!s || !s.pendingProfile) return;
    const p = s.pendingProfile;
    const msg = `Approve changes for ${s.name}?\n\nName: ${p.name}\nNick: ${p.nick}\nGender: ${p.gender}\nQuote: ${p.quote}\n` +
                (p.newCode ? `\n⚠️ NEW LOGIN CODE REQUESTED: ${p.newCode}\n` : '') + `\nSelect OK to Approve, or Cancel to review further.`;
    if(confirm(msg)) {
        s.name=p.name; s.nick=p.nick; s.gender=p.gender; s.quote=p.quote; s.img=p.img; s.stuMedia=p.stuMedia; s.ig=p.ig; s.fb=p.fb;
        if(p.newCode) s.code = p.newCode;
        delete s.pendingProfile; save(); renderAStu(); renderStudents(); toast('Changes approved! ✅', 'ok');
    } else {
        if(confirm('Do you want to REJECT and delete these pending edits?')) {
            delete s.pendingProfile; save(); renderAStu(); toast('Edits rejected', 'err');
        }
    }
}

function renderAStu(){document.getElementById('adStuList').innerHTML=D.students.map((s, i)=>`
  <div class="adrow" style="opacity:${s.visible===false?'.5':'1'}; ${s.pendingProfile?'border-left: 4px solid var(--gold); border-radius: 4px;':''}">
    <div class="ar-info"><div class="ar-ico">${s.img?`<img src="${s.img}"/>`  :em(s.gender)}</div><div class="ar-nm">${s.name} (${s.nick}) ${s.pendingProfile?'<span style="color:var(--gold);font-size:12px;margin-left:6px;">[Edits Pending]</span>':''}</div></div>
    <div class="ar-actions">
      ${s.pendingProfile?`<button class="ar-btn ok" onclick="reviewEdits(${s.id})" title="Review Edits">🔔</button>`:''}
      ${adminRole==='full'?`<span style="font-size:12px; color:var(--txt3); margin-right:10px;">Code: <strong style="color:var(--gold)">${s.code||'—'}</strong></span>`:''}
      <button class="ar-btn" onclick="moveStuUp(${s.id})" title="Move Up" ${i===0?'style="opacity:0.3;pointer-events:none"':''}>↑</button>
      <button class="ar-btn" onclick="moveStuDown(${s.id})" title="Move Down" ${i===D.students.length-1?'style="opacity:0.3;pointer-events:none"':''}>↓</button>
      <button class="ar-btn" onclick="editStu(${s.id})" title="Edit">✏️</button>
      <button class="ar-btn" onclick="togVisStu(${s.id})" title="${s.visible===false?'Show':'Hide'}">${s.visible===false?'👁️':'👁️‍🗨️'}</button>
      <button class="ar-btn del" onclick="delStu(${s.id})" title="Delete">🗑️</button>
    </div>
  </div>`).join('');}

// Admin Gallery
function editGal(id) {
  const g=D.gallery.find(x=>x.id===id);if(!g)return;
  document.getElementById('fGalId').value=g.id;
  document.getElementById('fGalType').value=g.type||'image';
  document.getElementById('fGalUrl').value=g.url;
  document.getElementById('fGalCap').value=g.caption;
  document.getElementById('fGalCat').value=g.cat||'School Days';
  document.getElementById('formAddGal').style.display='block';
}
function cancelGalForm() {
  document.getElementById('fGalId').value='';
  document.getElementById('fGalUrl').value='';
  document.getElementById('fGalCap').value='';
  document.getElementById('formAddGal').style.display='none';
}
function addGal(){
  const editId=document.getElementById('fGalId').value;
  const u=document.getElementById('fGalUrl').value.trim(),c=document.getElementById('fGalCap').value.trim(),cat=document.getElementById('fGalCat').value,type=document.getElementById('fGalType').value;
  if(!u){toast('URL required','err');return;}
  if(editId){
    const g=D.gallery.find(x=>x.id==editId);
    if(g){g.url=u;g.caption=c||'Media';g.cat=cat;g.type=type;toast('Gallery updated! ✏️','ok');}
  }else{
    D.gallery.push({id:D.nextGalId++,type,url:u,caption:c||'Media',cat});toast('Media added! 📸','ok');
  }
  save();cancelGalForm();renderAGal();
}
function moveGalUp(id){
  const idx = D.gallery.findIndex(g=>g.id==id);
  if(idx > 0) {
    const temp = D.gallery[idx];
    D.gallery[idx] = D.gallery[idx-1];
    D.gallery[idx-1] = temp;
    save(); renderAGal(); renderGallery();
  }
}
function moveGalDown(id){
  const idx = D.gallery.findIndex(g=>g.id==id);
  if(idx > -1 && idx < D.gallery.length - 1) {
    const temp = D.gallery[idx];
    D.gallery[idx] = D.gallery[idx+1];
    D.gallery[idx+1] = temp;
    save(); renderAGal(); renderGallery();
  }
}
function delGal(id){if(!confirm('Remove?'))return;D.gallery=D.gallery.filter(g=>g.id!=id);save();renderAGal();toast('Removed','ok');}
function approveGal(id){
    const g=D.gallery.find(x=>x.id==id);
    if(g) { g.approved=true; save(); renderAGal(); renderGallery(); toast('Approved','ok'); }
}
function renderAGal(){document.getElementById('adGalList').innerHTML=D.gallery.map((g,i)=>`
  <div class="adrow" style="${g.approved===false?'border-left:4px solid var(--gold); border-radius:4px;':''}"><div class="ar-info"><div class="ar-ico" style="border-radius:6px">${g.type==='video'?`<video src="${g.url}" muted preload="metadata" style="width:100%;height:100%;object-fit:cover;"></video>`:`<img src="${g.url}" style="border-radius:6px"/>`}</div>
    <div class="ar-nm">${g.caption} ${g.approved===false?'<span style="color:var(--gold)">(Pending)</span>':''} <span style="opacity:0.6">(${g.type==='video'?'Video':(g.cat||'—')})</span></div></div>
    <div class="ar-actions">
      ${g.approved===false?`<button class="ar-btn ok" onclick="approveGal(${g.id})" title="Approve">✅</button>`:''}
      <button class="ar-btn" onclick="moveGalUp(${g.id})" title="Move Up" ${i===0?'style="opacity:0.3;pointer-events:none"':''}>↑</button>
      <button class="ar-btn" onclick="moveGalDown(${g.id})" title="Move Down" ${i===D.gallery.length-1?'style="opacity:0.3;pointer-events:none"':''}>↓</button>
      <button class="ar-btn" onclick="editGal(${g.id})" title="Edit">✏️</button>
      <button class="ar-btn del" onclick="delGal(${g.id})">🗑️</button>
    </div></div>`).join('');}

// Admin Memories (with approval)
function approveMem(id){const m=D.memories.find(x=>x.id===id);if(m){m.approved=true;save();renderAMem();toast('Approved ✅','ok');}}
function delMem(id){if(!confirm('Remove?'))return;D.memories=D.memories.filter(m=>m.id!==id);save();renderAMem();toast('Removed','ok');}
function renderAMem(){
  const sorted=[...D.memories].sort((a,b)=>{if(a.approved===b.approved)return b.time-a.time;return a.approved?1:-1;});
  document.getElementById('adMemList').innerHTML=sorted.map(m=>`
    <div class="adrow"><div class="ar-info"><div class="ar-ico">${ini(m.author)}</div>
      <div class="ar-nm">${m.approved?'':'⏳ '}${m.author}: ${m.text.substring(0,40)}…</div></div>
      <div class="ar-actions">
        ${!m.approved?`<button class="ar-btn ok" onclick="approveMem(${m.id})" title="Approve">✅</button>`:''}
        <button class="ar-btn del" onclick="delMem(${m.id})">🗑️</button>
      </div></div>`).join('');}

// ====== STUDENT PORTAL LOGIC ======
function renderPortal() {
   if(!loggedInUser) return;
   const s = D.students.find(x => x.id === loggedInUser.id) || loggedInUser;
   
   if(s.pendingProfile) {
       document.getElementById('portalNotice').style.display='block';
   } else {
       document.getElementById('portalNotice').style.display='none';
   }

   document.getElementById('pName').value = s.name || '';
   document.getElementById('pNick').value = s.nick || '';
   document.getElementById('pGender').value = s.gender || 'male';
   document.getElementById('pQuote').value = s.quote || '';
   document.getElementById('pImg').value = s.img || '';
   document.getElementById('pMedia').value = s.stuMedia || '';
   document.getElementById('pIg').value = s.ig || '';
   document.getElementById('pFb').value = s.fb || '';
   document.getElementById('pNewCode').value = '';
   renderPortalGal();
}

function savePortalProfile() {
   if(!loggedInUser) return;
   const s = D.students.find(x => x.id === loggedInUser.id);
   if(s) {
       s.pendingProfile = {
           name: document.getElementById('pName').value.trim() || s.name,
           nick: document.getElementById('pNick').value.trim() || s.name.split(' ')[0],
           gender: document.getElementById('pGender').value,
           quote: document.getElementById('pQuote').value.trim(),
           img: document.getElementById('pImg').value.trim(),
           stuMedia: document.getElementById('pMedia').value.trim(),
           ig: document.getElementById('pIg').value.trim(),
           fb: document.getElementById('pFb').value.trim(),
           newCode: document.getElementById('pNewCode').value.trim() || null
       };
       save();
       toast('Profile edits sent for Admin approval! ⏳','ok');
       renderPortal();
       renderAStu();
   }
}

function submitPortalGal() {
    const url = document.getElementById('fPGalUrl').value.trim();
    const cap = document.getElementById('fPGalCap').value.trim();
    if(!url) { toast('Image URL required','err'); return; }
    D.gallery.push({
        id: D.nextGalId++,
        type: 'image',
        url: url,
        caption: cap || 'My Memory',
        cat: 'Memories',
        approved: false,
        authorId: loggedInUser.id
    });
    save();
    togForm('formPortalGal');
    document.getElementById('fPGalUrl').value='';
    document.getElementById('fPGalCap').value='';
    renderPortalGal();
    toast('Photo submitted for approval! 📸','ok');
}

function delPortalGal(id) {
    if(!confirm('Remove this photo?')) return;
    D.gallery = D.gallery.filter(g => g.id !== id);
    save();
    renderPortalGal();
}

function renderPortalGal() {
   if(!loggedInUser) return;
   const myPhotos = D.gallery.filter(g => g.authorId === loggedInUser.id);
   document.getElementById('portalGalList').innerHTML = myPhotos.map(g => `
      <div class="adrow">
        <div class="ar-info">
          <div class="ar-ico" style="border-radius:6px"><img src="${g.url}" style="border-radius:6px"/></div>
          <div class="ar-nm">${g.caption} <span style="font-size:12px;color:var(--gold);">${g.approved===false?'(Pending)':'(Approved)'}</span></div>
        </div>
        <div class="ar-actions">
           ${g.approved===false?`<button class="ar-btn del" onclick="delPortalGal(${g.id})">🗑️</button>`:''}
        </div>
      </div>
   `).join('');
}


// Admin Match Config
function loadMatchCfg(){
  const c=D.matchCfg||{};
  document.getElementById('cfgMode').value=c.mode||'random';
  document.getElementById('cfgFixedId').value=c.fixedId||'';
  document.getElementById('cfgBiasId').value=c.biasId||'';
  document.getElementById('cfgBiasW').value=c.biasWeight||5;
  document.getElementById('cfgMsgs').value=(c.messages||[]).join('\n');
  document.getElementById('cfgExclude').value=(c.excludeIds||[]).join(',');
  updCfgUI();
}
function saveMatchCfg(){
  const mode=document.getElementById('cfgMode').value;
  D.matchCfg={
    mode,
    fixedId:parseInt(document.getElementById('cfgFixedId').value)||null,
    biasId:parseInt(document.getElementById('cfgBiasId').value)||null,
    biasWeight:parseInt(document.getElementById('cfgBiasW').value)||5,
    messages:document.getElementById('cfgMsgs').value.split('\n').filter(l=>l.trim()),
    excludeIds:document.getElementById('cfgExclude').value.split(',').map(x=>parseInt(x.trim())).filter(x=>!isNaN(x)),
  };
  save();updCfgUI();toast('Match config saved','ok');
}
function updCfgUI(){
  const m=document.getElementById('cfgMode').value;
  document.getElementById('cfgFixed').style.display=m==='fixed'?'block':'none';
  document.getElementById('cfgBiased').style.display=m==='biased'?'block':'none';
}

// Admin Hero Config
function loadHeroCfg(){
  const h=D.heroCfg||DEF.heroCfg;
  if(document.getElementById('cfgHTxtColor')) document.getElementById('cfgHTxtColor').value = h.txtColor || '#ffffff';
  if(document.getElementById('cfgHAccColor')) document.getElementById('cfgHAccColor').value = h.accColor || '#d4a853';
  
  document.getElementById('cfgHeroBg1').value=h.bg1; document.getElementById('cfgHTag').value=h.tag;
  document.getElementById('cfgHTitle').value=h.title; document.getElementById('cfgHSub').value=h.sub;
  document.getElementById('cfgHSchool').value=h.school; document.getElementById('cfgHeroBg2').value=h.bg2;
  document.getElementById('cfgHStory1').value=h.story1; document.getElementById('cfgHStorySub').value=h.storySub;
  document.getElementById('cfgHeroBg3').value=h.bg3; document.getElementById('cfgHStory2').value=h.story2;
  if(document.getElementById('cfgHCap2')) document.getElementById('cfgHCap2').value=h.cap2||'Memories 📸';
  if(document.getElementById('cfgHCap3')) document.getElementById('cfgHCap3').value=h.cap3||'Farewell ✨';
}
function saveHeroCfg(){
  D.heroCfg={
    txtColor: document.getElementById('cfgHTxtColor')?document.getElementById('cfgHTxtColor').value:'#ffffff',
    accColor: document.getElementById('cfgHAccColor')?document.getElementById('cfgHAccColor').value:'#d4a853',
    bg1:document.getElementById('cfgHeroBg1').value, tag:document.getElementById('cfgHTag').value,
    title:document.getElementById('cfgHTitle').value, sub:document.getElementById('cfgHSub').value,
    school:document.getElementById('cfgHSchool').value, bg2:document.getElementById('cfgHeroBg2').value,
    story1:document.getElementById('cfgHStory1').value, storySub:document.getElementById('cfgHStorySub').value, cap2:document.getElementById('cfgHCap2')?document.getElementById('cfgHCap2').value:'Memories 📸',
    bg3:document.getElementById('cfgHeroBg3').value, story2:document.getElementById('cfgHStory2').value, cap3:document.getElementById('cfgHCap3')?document.getElementById('cfgHCap3').value:'Farewell ✨'
  };
  save(); applyHeroUI(); setupHeroScroll(); toast('Hero Settings saved','ok');
}

function addHeroSlide(){
  const img=document.getElementById('fHeroSlideImg').value.trim(),txt=document.getElementById('fHeroSlideText').value.trim(),sub=document.getElementById('fHeroSlideSub').value.trim();
  const eid=document.getElementById('fHeroSlideId').value;
  if(!img){toast('Image URL required','err');return;}
  if(eid){
    const s=D.heroSlides.find(x=>x.id==eid);
    if(s){s.img=img;s.text=txt;s.sub=sub;}
  }else{
    D.heroSlides.push({id:D.nextHeroSlideId++,img,text:txt,sub});
  }
  save();
  document.getElementById('fHeroSlideId').value='';
  document.getElementById('fHeroSlideImg').value='';document.getElementById('fHeroSlideText').value='';document.getElementById('fHeroSlideSub').value='';
  document.getElementById('btnSaveHeroSlide').textContent='Save';
  togForm('formAddHeroSlide');renderAHeroSlides();applyHeroUI();setupHeroScroll();toast('Success!','ok');
}
function editHeroSlide(id){
  const s=D.heroSlides.find(x=>x.id==id); if(!s)return;
  document.getElementById('fHeroSlideId').value=s.id;
  document.getElementById('fHeroSlideImg').value=s.img;
  document.getElementById('fHeroSlideText').value=s.text||'';
  document.getElementById('fHeroSlideSub').value=s.sub||'';
  document.getElementById('btnSaveHeroSlide').textContent='Update Slide';
  const f=document.getElementById('formAddHeroSlide'); if(f.style.display==='none')togForm('formAddHeroSlide');
}
function delHeroSlide(id){if(!confirm('Remove?'))return;D.heroSlides=D.heroSlides.filter(s=>s.id!==id);save();renderAHeroSlides();applyHeroUI();setupHeroScroll();toast('Removed','ok');}
function renderAHeroSlides(){
  document.getElementById('adHeroSlideList').innerHTML=D.heroSlides.map(s=>`
    <div class="adrow"><div class="ar-info"><div class="ar-ico" style="border-radius:6px"><img src="${s.img}" style="border-radius:6px"/></div>
    <div class="ar-nm">${s.text||'Slide'}</div></div>
    <div class="ar-actions">
      <button class="ar-btn ok" onclick="editHeroSlide(${s.id})">✏️</button>
      <button class="ar-btn del" onclick="delHeroSlide(${s.id})">🗑️</button>
    </div></div>`).join('');
}

function applyHeroUI(){
  const h=D.heroCfg||DEF.heroCfg;
  const heroSec = document.getElementById('hero');
  if (heroSec) {
    heroSec.style.setProperty('--h-txt', h.txtColor || '#ffffff');
    heroSec.style.setProperty('--h-acc', h.accColor || '#d4a853');
  }

  const e=(id,val)=>{if(document.getElementById(id)){
    if(val) document.getElementById(id).innerHTML=val;
    else document.getElementById(id).style.display='none';
  }};
  const im=(id,val)=>{
    const el=document.getElementById(id);
    if(el){
      if(val){ el.src=val; el.style.opacity=1; }
      else{ el.style.opacity=0; }
    }
  };
  
  im('heroBg1',h.bg1); e('hTag',h.tag); e('hTitle',h.title); e('hSub',h.sub); e('hSchool',h.school);
  im('heroBg2',h.bg2); e('hStory1',h.story1); e('hStorySub',h.storySub); e('heroCap2',h.cap2||'Memories 📸');
  im('heroBg3',h.bg3); e('hStory2',h.story2); e('heroCap3',h.cap3||'Farewell ✨');
    const c=document.getElementById('extraHeroSlidesContainer');
    if(c) c.innerHTML=(D.heroSlides||[]).map(s=>`
      <div class="hero-slide tl-slide hs-extra" id="heroSlideEx_${s.id}">
        <div class="timeline-line"></div>
        <div class="tl-marker">★</div>
        <div class="hero-content">
          <div class="tl-col-txt">
            ${s.text?`<h2 class="tl-title">${s.text}</h2>`:''}
            ${s.sub?`<p class="tl-desc">${s.sub}</p>`:''}
          </div>
          <div class="tl-col-img">
            <div class="tl-polaroid">
              <img src="${s.img}" alt="" onerror="this.src='https://images.unsplash.com/photo-1523580846011-d3a5bc25702b?w=800&q=80'"/>
              <div class="tl-polaroid-cap">${s.text?s.text.split(' ').slice(0,2).join(' ')+'...':'Memory 📸'}</div>
            </div>
          </div>
        </div>
      </div>`).join('');
}

// Admin Settings & Loader
function loadSettingsCfg(){
  const c=D.loaderCfg||DEF.loaderCfg;
  document.getElementById('cfgPlIcon').value=c.icon;
  document.getElementById('cfgPlText').value=c.text;
  document.getElementById('cfgPlSub').value=c.sub;
  if(document.getElementById('cfgCreatorName')) document.getElementById('cfgCreatorName').value=c.creatorName||'Debangshu Sen';
  if(document.getElementById('cfgCreatorLink')) document.getElementById('cfgCreatorLink').value=c.creatorLink||'https://instagram.com/debangshu_sen';
  if(document.getElementById('cfgVisYb')) document.getElementById('cfgVisYb').checked=c.visYb!==false;
  
  if(document.getElementById('cfgGlobalFont')){
    document.getElementById('cfgGlobalFont').value=c.globalFont||'Inter';
  }
  
  if(document.getElementById('cfgStuSub')) document.getElementById('cfgStuSub').value=c.stuSub||'The ones who made these years golden';
  if(document.getElementById('cfgGalTitle')) document.getElementById('cfgGalTitle').value=c.galTitle||'Gallery';
  if(document.getElementById('cfgGalSub')) document.getElementById('cfgGalSub').value=c.galSub||'Snapshots of our golden days';
  if(document.getElementById('cfgArchiveLink')) document.getElementById('cfgArchiveLink').value=c.archiveLink||'';
  if(document.getElementById('cfgMemTitle')) document.getElementById('cfgMemTitle').value=c.memTitle||'Message Wall of Reflection';
  if(document.getElementById('cfgMemSub')) document.getElementById('cfgMemSub').value=c.memSub||'A space to leave your final words, memories, and wishes. These notes will remain here as a testament to our journey.';
  
  if(document.getElementById('cfgHeroCta')) document.getElementById('cfgHeroCta').value=c.heroCta||'Explore Our Memories →';
  if(document.getElementById('cfgIntroTitle')) document.getElementById('cfgIntroTitle').value=c.introTitle||'Memories';
  if(document.getElementById('cfgIntroSub')) document.getElementById('cfgIntroSub').value=c.introSub||'A collection of moments that defined us.';
  if(document.getElementById('cfgYbTitle')) document.getElementById('cfgYbTitle').value=c.ybTitle||'CLASS 12 BATCH';
  if(document.getElementById('cfgYbSub')) document.getElementById('cfgYbSub').value=c.ybSub||'(2025-26)';
  if(document.getElementById('cfgYbHint')) document.getElementById('cfgYbHint').value=c.ybHint||'Click to flip the story 📖';
  
  if(document.getElementById('cfgMapSub')) document.getElementById('cfgMapSub').value=c.mapSub||'Revisit the hallways where it all happened.';

  if(document.getElementById('cfgVisStu')) document.getElementById('cfgVisStu').checked=!!c.visStu;
  if(document.getElementById('cfgVisGal')) document.getElementById('cfgVisGal').checked=!!c.visGal;
  if(document.getElementById('cfgVisWall')) document.getElementById('cfgVisWall').checked=!!c.visWall;
  if(document.getElementById('cfgVisMatch')) document.getElementById('cfgVisMatch').checked=!!c.visMatch;
  if(document.getElementById('cfgVisYb')) document.getElementById('cfgVisYb').checked=!!c.visYb;
}
function saveSettingsCfg(){
  D.loaderCfg={
    icon:document.getElementById('cfgPlIcon').value,
    text:document.getElementById('cfgPlText').value,
    sub:document.getElementById('cfgPlSub').value,
    creatorName:document.getElementById('cfgCreatorName')?document.getElementById('cfgCreatorName').value:'Debangshu Sen',
    creatorLink:document.getElementById('cfgCreatorLink')?document.getElementById('cfgCreatorLink').value:'',
    copyright:document.getElementById('cfgCopyright')?document.getElementById('cfgCopyright').value:'© 2024–2025 DSCM ALUMNI',
    tagline:document.getElementById('cfgTagline')?document.getElementById('cfgTagline').value:'All memories are preserved forever ❤️',
    stuHeaderPos:document.getElementById('cfgStuHeaderPos')?document.getElementById('cfgStuHeaderPos').value:'top',
    globalTxt:document.getElementById('cfgGlobalTxt')?document.getElementById('cfgGlobalTxt').value:'#E8E4DC',
    globalAcc:document.getElementById('cfgGlobalAcc')?document.getElementById('cfgGlobalAcc').value:'#D4A853',
    globalFont:document.getElementById('cfgGlobalFont')?document.getElementById('cfgGlobalFont').value:'Inter',
    stuSub:document.getElementById('cfgStuSub')?document.getElementById('cfgStuSub').value:'',
    galTitle:document.getElementById('cfgGalTitle')?document.getElementById('cfgGalTitle').value:'',
    galSub:document.getElementById('cfgGalSub')?document.getElementById('cfgGalSub').value:'',
    archiveLink:document.getElementById('cfgArchiveLink')?document.getElementById('cfgArchiveLink').value:'',
    memTitle:document.getElementById('cfgMemTitle')?document.getElementById('cfgMemTitle').value:'',
    memSub:document.getElementById('cfgMemSub')?document.getElementById('cfgMemSub').value:'',
    mapImg:document.getElementById('cfgMapImg')?document.getElementById('cfgMapImg').value:'',
    mapTitle:document.getElementById('cfgMapTitle')?document.getElementById('cfgMapTitle').value:'',
    mapSub:document.getElementById('cfgMapSub')?document.getElementById('cfgMapSub').value:'',
    
    visStu:document.getElementById('cfgVisStu')?document.getElementById('cfgVisStu').checked:true,
    visGal:document.getElementById('cfgVisGal')?document.getElementById('cfgVisGal').checked:true,
    visWall:document.getElementById('cfgVisWall')?document.getElementById('cfgVisWall').checked:true,
    visMatch:document.getElementById('cfgVisMatch')?document.getElementById('cfgVisMatch').checked:true,
    visYb:document.getElementById('cfgVisYb')?document.getElementById('cfgVisYb').checked:true
  };
  save(); applyLoaderUI(); applyFooterUI(); applyLayoutUI(); applyAppearanceUI();
  toast('Settings saved','ok');
}

function applyAppearanceUI(){
  const c=D.loaderCfg||DEF.loaderCfg;
  const root = document.documentElement;
  if(c.globalTxt) root.style.setProperty('--txt', c.globalTxt);
  if(c.globalAcc) {
    root.style.setProperty('--gold', c.globalAcc);
    root.style.setProperty('--gold2', c.globalAcc + 'DD');
    root.style.setProperty('--grad-gold', `linear-gradient(135deg, ${c.globalAcc} 0%, ${c.globalAcc} 100%)`);
  }
  if(c.globalFont) root.style.setProperty('--f-body', c.globalFont + ', sans-serif');

  const e=(id,val)=>{if(document.getElementById(id)){if(val)document.getElementById(id).innerText=val;}};
  e('hStuSub', c.stuSub);
  e('hGalTitle', c.galTitle);
  e('hGalSub', c.galSub);
  e('hMemTitle', c.memTitle);
  e('hMemSub', c.memSub);
  if(curPage==='gallery') renderGallery();
}

function navigateTo(id){
  const now = Date.now();
  let target = id;
  if(id === 'hero'){
    if(now - lastHomeTap < 300){ target = 'admin'; }
    lastHomeTap = now;
  }
  if(curPage===target && target !== 'admin') return;
  
  // Transitions
  document.querySelectorAll('.page').forEach(p=>{
    p.classList.remove('active');
    p.style.opacity='';
    p.style.transform='';
  });
  
  if(target==='students')renderStudents();
  if(target==='gallery'){renderGalleryCats();renderGallery();}
  if(target==='memories')renderMemories();
  
  const pg=document.getElementById(target);
  if(!pg) return;
  
  window.scrollTo({top:0, left:0, behavior:'instant'});
  
  if(target === 'hero') {
    document.body.style.overflow = 'hidden';
    setupHeroScroll();
  } else {
    document.body.style.overflow = 'auto';
  }
  
  const pw=document.getElementById('particleWrap');
  if(pw) pw.style.display=(target==='hero')?'block':'none';
  
  pg.style.opacity='0'; pg.style.transform='translateY(18px)';
  pg.classList.add('active');
  curPage=target;
  updateNav();
  
  setTimeout(()=>{
    pg.style.transition='opacity .45s var(--ease),transform .45s var(--ease)';
    pg.style.opacity='1'; pg.style.transform='translateY(0)';
    trigReveals(pg);
  }, 10);
}

function applyLayoutUI(){
  const c=D.loaderCfg||DEF.loaderCfg;
  const s=document.getElementById('students'), h=document.getElementById('stuHead'), sb=document.getElementById('stuSearchBox'), g=document.getElementById('studentsGrid');
  if(!s||!h||!sb||!g)return;
  if(c.stuHeaderPos==='bottom'){ s.querySelector('.inner-page').appendChild(h); s.querySelector('.inner-page').appendChild(sb); }
  else{ s.querySelector('.inner-page').prepend(h); h.insertAdjacentElement('afterend',sb); }
}

function chgPass(){const p=document.getElementById('cfgNewPass').value;if(!p||p.length<4){toast('Min 4 chars','err');return;}
  D.adminPassword=p;save();document.getElementById('cfgNewPass').value='';toast('Password updated 🔒','ok');}
function exportJSON(){const b=new Blob([JSON.stringify(D,null,2)],{type:'application/json'});const a=document.createElement('a');a.href=URL.createObjectURL(b);
  a.download='dscm_data.json';a.click();URL.revokeObjectURL(a.href);toast('Exported 📦','ok');}
function importJSON(){const f=document.getElementById('importFile').files[0];if(!f){toast('Select file','err');return;}
  const r=new FileReader();r.onload=e=>{try{D=JSON.parse(e.target.result);save();renderAStu();renderAGal();renderAMem();renderAYb();loadMatchCfg();loadHeroCfg();renderAHeroSlides();loadSettingsCfg();applyLoaderUI();applyHeroUI();applyLayoutUI();applyAppearanceUI();applyFooterUI();renderYearbook();setupHeroScroll();toast('Imported ✅','ok');}catch{toast('Invalid JSON','err');}};r.readAsText(f);}

// ====== TOAST ======
function toast(msg,type='ok'){const w=document.getElementById('toastWrap');const t=document.createElement('div');t.className=`toast-item ${type}`;t.textContent=msg;
  w.appendChild(t);setTimeout(()=>{t.classList.add('out');setTimeout(()=>t.remove(),300);},2500);}

// ====== COUNTERS ======
function animNums(){animN('cntStudents',D.students.filter(s=>s.visible!==false).length,1200);animN('cntMemories',D.memories.filter(m=>m.approved).length,1400);animN('cntPhotos',D.gallery.length,1600);}
function animN(id,target,dur){const el=document.getElementById(id);if(!el)return;let st=0;const step=ts=>{if(!st)st=ts;const p=Math.min((ts-st)/dur,1);el.textContent=Math.floor(p*target);if(p<1)requestAnimationFrame(step);};requestAnimationFrame(step);}

// ====== KEYBOARD ======
document.addEventListener('keydown',e=>{
  if(e.key==='Escape'){closeModal();closeLB();}
  if(e.ctrlKey && e.key==='s'){e.preventDefault();save();}
  if(document.getElementById('lightbox').classList.contains('open')){
    if(e.key==='ArrowLeft')lbPrev();
    if(e.key==='ArrowRight')lbNext();
  }
});

window.addEventListener('popstate', (e) => {
  const lb = document.getElementById('lightbox');
  if(lb && lb.classList.contains('open')) {
     closeLB(true); return;
  }
  const modal = document.getElementById('studentModal');
  if(modal && modal.classList.contains('open')) {
     closeModal(true); return;
  }
});

// ====== INIT ======
document.addEventListener('DOMContentLoaded',()=>{
  // Preloader
  setTimeout(()=>{document.getElementById('preloader').classList.add('gone');
    setTimeout(()=>{
      trigReveals(document.getElementById('hero'));
      animNums();
      initParticles();
      setupHeroScroll();
      // Make hero content 1 visible
      document.getElementById('heroContent1').classList.add('hc-visible');
      
      // Layout
      applyLayoutUI();
      // Appearance
      applyAppearanceUI();
      renderYearbook();
      renderAYb();
      // Force Credit Footer
      applyFooterUI();
    },300);
  },1800);

  // Admin shortcut
  const hb=document.querySelector('[data-p="hero"]');let lt;
  hb.addEventListener('touchstart',()=>{lt=setTimeout(()=>navigateTo('admin'),2000);},{passive:true});
  hb.addEventListener('touchend',()=>clearTimeout(lt));
  hb.addEventListener('touchmove',()=>clearTimeout(lt));
  hb.addEventListener('dblclick',()=>navigateTo('admin'));
});
// ====== YEARBOOK LOGIC ======
let currentYbPage = -1; // -1 is cover
function renderYearbook(){
  const container = document.getElementById('ybPages');
  if(!container) return;
  const yb = D.yearbook || DEF.yearbook;
  container.innerHTML = yb.map((p, i) => `
    <div class="yb-page yb-content-page" id="ybPage_${i}" style="z-index:${yb.length - i}" onclick="nextPage()">
      <img src="${p.img}" class="yb-page-img" alt=""/>
      <div class="yb-page-title">${p.title}</div>
      <div class="yb-page-text">${p.text}</div>
    </div>
  `).join('');
  updateYbUI();
}

function updateYbUI(){
  const yb = D.yearbook || DEF.yearbook;
  const cov=document.getElementById('ybCover');
  if(!cov)return;
  
  if(currentYbPage === -1) {
    cov.classList.remove('flipped');
    for(let i=0; i<yb.length; i++){
      const p = document.getElementById(`ybPage_${i}`);
      if(p) p.classList.remove('flipped');
    }
    document.getElementById('ybPageNum').textContent = "Cover";
  } else {
    cov.classList.add('flipped');
    for(let i=0; i<yb.length; i++){
      const p = document.getElementById(`ybPage_${i}`);
      if(p){
        if(i < currentYbPage) p.classList.add('flipped');
        else p.classList.remove('flipped');
      }
    }
    document.getElementById('ybPageNum').textContent = currentYbPage < yb.length ? `Page ${currentYbPage + 1}` : "The End";
  }
}

function nextPage(){
  const max = (D.yearbook || DEF.yearbook).length;
  if(currentYbPage < max) {
    currentYbPage++;
    updateYbUI();
  }
}

function prevPage(){
  if(currentYbPage > -1) {
    currentYbPage--;
    updateYbUI();
  }
}

function resetBook(){
  currentYbPage = -1;
  updateYbUI();
}

// ====== YEARBOOK ADMIN ======
function addYbPage(){
  const yb = D.yearbook || DEF.yearbook;
  yb.push({
    id: Date.now(),
    title: "New Memory Title",
    text: "Describe this golden moment in your story...",
    img: "https://images.unsplash.com/photo-1540479859555-17af45c78602?w=800&q=80"
  });
  D.yearbook = yb;
  save();
  renderYearbook();
  renderAYb();
}

function deleteYbPage(id){
  const yb = D.yearbook || DEF.yearbook;
  D.yearbook = yb.filter(p => p.id !== id);
  save();
  renderYearbook();
  renderAYb();
}

function updateYbPage(id, field, val){
  const yb = D.yearbook || DEF.yearbook;
  const p = yb.find(item => item.id === id);
  if(p) p[field] = val;
  D.yearbook = yb;
  save();
  renderYearbook();
}

// ====== YEARBOOK ADMIN ======
function addYb(){
  const t=document.getElementById('fYbTitle').value.trim(),txt=document.getElementById('fYbText').value.trim(),img=document.getElementById('fYbImg').value.trim(),eid=document.getElementById('fYbId').value;
  if(!t||!img){toast('Title/Image required','err');return;}
  if(eid){
    const p=D.yearbook.find(x=>x.id==eid);
    if(p){p.title=t;p.text=txt;p.img=img;}
  }else{
    D.yearbook.push({id:Date.now(),title:t,text:txt,img:img});
  }
  save();renderAYb();renderYearbook();togForm('formAddYb');
  document.getElementById('fYbId').value='';document.getElementById('fYbTitle').value='';document.getElementById('fYbText').value='';document.getElementById('fYbImg').value='';
  document.getElementById('btnSaveYb').textContent='Save';toast('Yearbook updated','ok');
}
function editYb(id){
  const p=D.yearbook.find(x=>x.id==id);if(!p)return;
  document.getElementById('fYbId').value=p.id;
  document.getElementById('fYbTitle').value=p.title;
  document.getElementById('fYbText').value=p.text||'';
  document.getElementById('fYbImg').value=p.img;
  document.getElementById('btnSaveYb').textContent='Update Page';
  const f=document.getElementById('formAddYb');if(f.style.display==='none')togForm('formAddYb');
}
function delYb(id){if(!confirm('Remove?'))return;D.yearbook=D.yearbook.filter(x=>x.id!==id);save();renderAYb();renderYearbook();toast('Removed','ok');}
function renderAYb(){
  const yb = D.yearbook || [];
  document.getElementById('adYbList').innerHTML=yb.map(p=>`
    <div class="adrow"><div class="ar-info"><div class="ar-ico"><img src="${p.img}"/></div><div class="ar-nm">${p.title}</div></div>
    <div class="ar-actions"><button class="ar-btn ok" onclick="editYb(${p.id})">✏️</button><button class="ar-btn del" onclick="delYb(${p.id})">🗑️</button></div></div>`).join('');
}

// ====== DEVTOOLS / INSPECT PROTECTION ======
document.addEventListener('contextmenu', e => e.preventDefault());
document.addEventListener('keydown', e => {
  if (
    e.key === 'F12' ||
    (e.ctrlKey && e.shiftKey && ['I','J','C'].includes(e.key.toUpperCase())) ||
    (e.ctrlKey && e.key.toUpperCase() === 'U')
  ) {
    e.preventDefault();
    toast('Inspect is disabled for security \ud83d\udd12', 'err');
  }
});

function applyFooterUI(){
  const c=D.loaderCfg||DEF.loaderCfg;
  const name = c.creatorName||'Debangshu Sen';
  const link = c.creatorLink||'https://www.instagram.com/debangshusen15';
  const copy = c.copyright||'CLASS 12 ( 2025-26 )';
  const tag  = c.tagline||'All memories are preserved forever ❤️';

  // 1️⃣ Update dynamically-created footers on non-hero/non-admin pages
  document.querySelectorAll('.site-footer').forEach(f=>f.remove());
  document.querySelectorAll('.page').forEach(pg=>{
    if(pg.id!=='admin' && pg.id!=='hero'){
      const f=document.createElement('div');f.className='site-footer';
      f.style.cssText='text-align:center; padding:40px 20px 120px;';

      const a=document.createElement('a');a.className='site-footer-link';a.target='_blank';
      a.style.cssText='display:block;font-family:var(--f-hand);font-size:28px;color:var(--gold);text-decoration:none;margin-bottom:12px;';
      a.textContent='Made by '+name; a.href=link;

      const cp=document.createElement('div');cp.className='site-footer-copy';
      cp.style.cssText='font-size:12px;color:#666;letter-spacing:1.5px;text-transform:uppercase;line-height:1.8;';
      cp.innerHTML=`${copy}<br><span style="color:#888;">${tag}</span>`;

      f.appendChild(a);f.appendChild(cp);
      const inner=pg.querySelector('.inner-page');
      if(inner) inner.appendChild(f); else pg.appendChild(f);
    }
  });

  // 2️⃣ Update the hero section's static footer (inside hs-3)
  const heroCreator = document.getElementById('fCreatorHero');
  if(heroCreator){ heroCreator.textContent='Made by '+name; heroCreator.href=link; }
  const heroCopy = document.getElementById('fCopyHero');
  if(heroCopy) heroCopy.textContent=copy;
  const heroTag = document.getElementById('fTaglineHero');
  if(heroTag) heroTag.textContent=tag;
}
