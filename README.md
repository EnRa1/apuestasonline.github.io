# enra1.github.io

<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>¿En qué momento jugar deja de ser solamente jugar?</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bungee&family=Fraunces:opsz,wght@9..144,500;9..144,700&family=Rubik:wght@400;500;600;800&display=swap" rel="stylesheet">
<style>
:root{
  --chrome-bg:#e7e3ef;--chrome-fg:#241b3a;--chrome-btn:#ffffff;--chrome-line:#c9c2da;
  --gold:#ffc933;--gold2:#ff9f1c;--red:#ff2d55;--violet:#7b2cff;--magenta:#ff3df2;--green:#20e58f;--cyan:#3be3ff;
  --ca-bg:#e8f0ee;--ca-card:#f6faf9;--ca-ink:#15303a;--ca-teal:#2a7b83;--ca-teal2:#1d5860;--ca-sage:#a9c8bc;--ca-amber:#b9791c;
  box-sizing:border-box;
  padding-top:env(safe-area-inset-top,0px);
  padding-bottom:env(safe-area-inset-bottom,0px);
}
@media (prefers-color-scheme:dark){
  :root:not([data-theme="light"]){--chrome-bg:#07040f;--chrome-fg:#e9e4ff;--chrome-btn:#1b1233;--chrome-line:#2c2150}
}
:root[data-theme="dark"]{--chrome-bg:#07040f;--chrome-fg:#e9e4ff;--chrome-btn:#1b1233;--chrome-line:#2c2150}
*{box-sizing:border-box}
html{height:100%;scroll-padding-top:env(safe-area-inset-top,0px)}
body{height:100%;margin:0;overflow:hidden;background:var(--chrome-bg);color:var(--chrome-fg);font-family:'Rubik',system-ui,-apple-system,'Segoe UI',Roboto,sans-serif;-webkit-tap-highlight-color:transparent}
#app{height:100%;display:flex;flex-direction:column}
#vp{flex:1;position:relative;overflow:hidden;min-height:0}
#bar{flex:0 0 auto;display:flex;align-items:center;gap:8px;padding:8px 12px;border-top:1px solid var(--chrome-line);overflow-x:auto;white-space:nowrap}
.cb{background:var(--chrome-btn);color:var(--chrome-fg);border:1px solid var(--chrome-line);border-radius:10px;padding:8px 14px;font:500 15px 'Rubik',system-ui,sans-serif;cursor:pointer}
.cb:focus-visible,.btn:focus-visible{outline:3px solid #3be3ff;outline-offset:3px}
#cnt{font:600 15px 'Rubik',system-ui,sans-serif;min-width:64px;text-align:center}
#secchip{font:600 14px 'Rubik',system-ui,sans-serif;opacity:.75;margin-left:auto}
#rot{display:none;position:absolute;top:8px;left:50%;transform:translateX(-50%);z-index:40;background:#000b;color:#fff;border-radius:20px;padding:6px 14px;font:500 14px 'Rubik',sans-serif}
@media (orientation:portrait){#rot{display:block}}
#notes{position:absolute;left:12px;right:12px;bottom:12px;max-height:42%;overflow:auto;background:#000d;color:#fff;border-radius:14px;padding:14px 18px;font:400 16px/1.5 'Rubik',sans-serif;display:none;z-index:50}
#notes.on{display:block}
#notes b{color:#ffc933}

/* ===== ESCENARIO 1920x1080 ===== */
.stage{position:absolute;left:50%;top:50%;width:1920px;height:1080px;margin:-540px 0 0 -960px;transform:scale(var(--s,.5));transform-origin:50% 50%;background:#000;overflow:hidden;box-shadow:0 10px 60px #0006}
.slide{position:absolute;inset:0;opacity:0;visibility:hidden;transition:opacity .4s,visibility 0s .4s;overflow:hidden;color:#fff}
.slide.active{opacity:1;visibility:visible;transition:opacity .4s}
.stage.cut .slide{transition:none!important}
.slide.t-calm{transition:opacity 1.1s,visibility 0s 1.1s}
.slide.t-calm.active{transition:opacity 1.1s}
.abs{position:absolute}
.gold{color:var(--gold)}

/* temas */
.t-casino{background:radial-gradient(1500px 850px at 50% -5%,#5b1aa8 0%,#2a0c5e 42%,#0d0524 100%)}
.t-casino::before{content:"";position:absolute;inset:0;pointer-events:none;background:
 radial-gradient(3px 3px at 8% 22%,#fff 60%,#0000 62%),radial-gradient(2px 2px at 22% 70%,#ffe08a 60%,#0000 62%),
 radial-gradient(3px 3px at 37% 12%,#fff 60%,#0000 62%),radial-gradient(2px 2px at 53% 84%,#fff 60%,#0000 62%),
 radial-gradient(3px 3px at 68% 30%,#ffe08a 60%,#0000 62%),radial-gradient(2px 2px at 81% 66%,#fff 60%,#0000 62%),
 radial-gradient(3px 3px at 92% 18%,#ffe08a 60%,#0000 62%),radial-gradient(2px 2px at 14% 92%,#fff 60%,#0000 62%);
 animation:twinkle 2.4s ease-in-out infinite alternate}
.t-dark{background:linear-gradient(160deg,#160c38 0%,#0b0620 65%),#0b0620}
.t-dark::before{content:"";position:absolute;inset:0;pointer-events:none;background-image:linear-gradient(#ffffff08 1px,transparent 1px),linear-gradient(90deg,#ffffff08 1px,transparent 1px);background-size:60px 60px}
.t-black{background:#000}
.t-calm{background:var(--ca-bg);color:var(--ca-ink)}
.bulbs::after{content:"";position:absolute;inset:18px;border-radius:40px;border:12px dotted #ffd766;pointer-events:none;filter:drop-shadow(0 0 10px #ffb020);animation:blink 1.2s steps(2) infinite}
@keyframes twinkle{from{opacity:.35}to{opacity:1}}
@keyframes blink{50%{opacity:.35}}
@keyframes spin{to{transform:rotate(360deg)}}
@keyframes pulse{50%{transform:scale(1.07)}}
@keyframes shine{0%{left:-60%}60%,100%{left:130%}}
@keyframes bob{50%{transform:translateY(-16px)}}
@keyframes pop{from{opacity:0;transform:scale(.8)}to{opacity:1;transform:none}}
@keyframes fadeIn{to{opacity:1}}
@keyframes shake{0%,100%{transform:translateX(0) rotate(0)}25%{transform:translateX(-14px) rotate(-3deg)}75%{transform:translateX(14px) rotate(3deg)}}
@keyframes glow{from{filter:drop-shadow(0 7px 0 #6b2200) drop-shadow(0 0 20px #ffb02066)}to{filter:drop-shadow(0 7px 0 #6b2200) drop-shadow(0 0 60px #ffb020)}}
@keyframes nearIn{from{opacity:0;transform:scale(1.5)}to{opacity:1;transform:scale(1)}}
@keyframes toastIn{to{transform:translateX(0)}}
@keyframes ping{0%{box-shadow:0 0 0 0 #3be3ffaa}100%{box-shadow:0 0 0 22px #3be3ff00}}
@keyframes spinReel{from{transform:translateY(0)}to{transform:translateY(-1600px)}}
@keyframes nodeGlow{0%,22%,100%{box-shadow:0 0 0 #0000}10%{box-shadow:0 0 44px currentColor}}
@keyframes crt{0%{height:1080px;top:0;opacity:1}40%{height:6px;top:537px;opacity:1}100%{height:6px;top:537px;transform:scaleX(0);opacity:0}}
@keyframes slideUp{from{opacity:0;transform:translateY(24px)}to{opacity:1;transform:none}}

/* barra XP y etiqueta de sección */
.xp{position:absolute;left:0;right:0;bottom:0;height:16px;background:#0008;z-index:30;transition:opacity .4s}
.xp i{display:block;height:100%;width:0;transition:width .6s;background:linear-gradient(90deg,#ff9f1c,#ffc933,#fff3a6);box-shadow:0 0 18px #ffc933}
.st-dark .xp i{background:linear-gradient(90deg,#7b2cff,#3be3ff);box-shadow:0 0 14px #3be3ff88}
.st-calm .xp{height:6px;background:#15303a14}
.st-calm .xp i{background:var(--ca-teal);box-shadow:none}
.st-black .xp,.st-black .stag{opacity:0}
.stag{position:absolute;top:34px;right:60px;z-index:30;font:800 26px 'Rubik',sans-serif;letter-spacing:.2em;padding:8px 24px;border-radius:30px;background:#000a;color:#fff;border:2px solid #fff5;transition:opacity .4s}
.st-casino .stag{border-color:var(--gold);color:var(--gold)}
.st-dark .stag{border-color:var(--cyan);color:var(--cyan)}
.st-calm .stag{background:#ffffffaa;color:var(--ca-teal2);border-color:var(--ca-teal)}
#confetti{position:absolute;inset:0;z-index:25;pointer-events:none}

/* tipografía casino */
.title-xl,.title-lg{font-family:Bungee,Impact,sans-serif;font-weight:400;background:linear-gradient(#fff7b8,#ffc933 48%,#ff8a00);-webkit-background-clip:text;background-clip:text;color:transparent;filter:drop-shadow(0 7px 0 #6b2200) drop-shadow(0 0 34px #ffb02099);margin:0}
.title-xl{font-size:116px;line-height:1.02}
.title-lg{font-size:84px;line-height:1.05}
.h2{font:400 66px/1.06 Bungee,Impact,sans-serif;color:#fff;text-shadow:0 5px 0 #0006;margin:0}
.hd{position:absolute;left:100px;top:64px;width:1480px}
.hd p{font:500 34px/1.3 'Rubik',sans-serif;color:#cfc4ff;margin:14px 0 0}
.rays{position:absolute;width:1400px;height:1400px;border-radius:50%;background:repeating-conic-gradient(from 0deg,#ffd76626 0 8deg,#0000 8deg 20deg);-webkit-mask:radial-gradient(circle,#000 18%,#0000 68%);mask:radial-gradient(circle,#000 18%,#0000 68%);animation:spin 40s linear infinite}

/* botones */
.btn{position:relative;display:inline-block;font:400 68px/1 Bungee,Impact,sans-serif;color:#fff;text-shadow:0 5px 0 #0004;padding:26px 72px;border-radius:30px;border:0;cursor:pointer;overflow:hidden}
.btn.green{background:linear-gradient(#54ff9f,#0fb85f);box-shadow:0 10px 0 #067a3d,0 0 50px #20e58f99}
.btn.red{background:linear-gradient(#ff7a4d,#e0122e);box-shadow:0 10px 0 #8a0a1c,0 0 50px #ff2d5599}
.btn.gold{background:linear-gradient(#ffe27a,#ff9f1c);color:#4a2500;text-shadow:none;box-shadow:0 10px 0 #a65a00,0 0 50px #ffb02099}
.btn::after{content:"";position:absolute;top:0;left:-60%;width:40%;height:100%;background:linear-gradient(100deg,#0000,#fff8,#0000);transform:skewX(-20deg);animation:shine 2.6s infinite}
.pulse{animation:pulse 1.1s ease-in-out infinite}
.coin{display:inline-block;width:1em;height:1em;border-radius:50%;background:radial-gradient(circle at 35% 30%,#fff3a0,#ffc933 45%,#c77700);box-shadow:inset 0 0 0 .09em #a85f00,0 0 .4em #ffb02088;vertical-align:-.12em}
.hud{position:absolute;top:34px;left:60px;display:flex;gap:18px;align-items:center;z-index:5;font:800 34px 'Rubik',sans-serif;color:#fff}
.pill{display:flex;align-items:center;gap:12px;padding:8px 24px;border-radius:40px;background:#0007;border:3px solid #ffffff33;box-shadow:inset 0 0 12px #0008}
.pill.lvl{background:linear-gradient(#7b2cff,#4a12b8)}
.pill b{color:var(--green)}
.pill svg{width:34px;height:34px}

/* cofre */
.chest{width:100%;height:auto;display:block;filter:drop-shadow(0 0 40px #ffb02088)}
.chest .inside{opacity:0;transition:opacity .3s}
.chest.open .inside{opacity:.95}
.chest .lid{transform-origin:40px 170px;transition:transform .45s cubic-bezier(.3,1.6,.5,1)}
.chest.open .lid{transform:rotate(-42deg)}
.shaking{animation:shake .12s 8}
.bob{animation:bob 2.4s ease-in-out infinite}

/* S1 portada */
.cover{position:absolute;left:120px;top:150px;width:1120px}
.cover .k{font:600 30px 'Rubik',sans-serif;color:var(--gold);margin-bottom:26px}
.cover .sub{font:600 46px/1.2 'Rubik',sans-serif;color:#e8dcff;margin:28px 0 0}
.reels{position:absolute;left:1290px;top:250px;display:flex;gap:16px;padding:22px;border-radius:30px;background:linear-gradient(#ffe27a,#c77700);box-shadow:0 0 60px #ffb020aa}
.reel{width:170px;height:200px;overflow:hidden;border-radius:16px;background:#150a35;border:4px solid #4a2500}
.strip{will-change:transform}
.slide.active .strip{animation:spinReel var(--d) cubic-bezier(.15,.75,.2,1) forwards}
.cell{height:200px;display:flex;align-items:center;justify-content:center}
.cell svg{width:112px;height:112px}
.qbadge{position:absolute;left:120px;top:740px;width:1680px;padding:24px 40px;border-radius:26px;background:linear-gradient(90deg,#c1123a,#ff2d55);border:5px solid var(--gold);font:800 56px/1.15 'Rubik',sans-serif;text-align:center;box-shadow:0 0 50px #ff2d5588}
.team{position:absolute;left:120px;right:120px;top:930px;font:500 28px/1.4 'Rubik',sans-serif;color:#cfc4ff;text-align:center}

/* S2-S3 */
.notif{position:absolute;left:1620px;top:220px;width:84px;height:84px;border-radius:50%;background:var(--red);border:5px solid #fff;font:800 50px/74px 'Rubik',sans-serif;text-align:center;z-index:4;animation:pulse 1s infinite}
.item-card{position:absolute;left:1030px;top:210px;width:640px;height:700px;border-radius:36px;padding:40px;background:linear-gradient(170deg,#3b3f4d,#171a25);border:8px solid #9aa3b2;text-align:center;opacity:0;transform:translateY(60px) scale(.8)}
.item-card.show{opacity:1;transform:none;transition:all .6s cubic-bezier(.3,1.5,.5,1)}
.item-card .ic-art{height:360px;display:flex;align-items:center;justify-content:center;color:#9aa3b2}
.item-card .ic-art svg{width:280px;height:280px}
.ic-name{font:400 52px Bungee,sans-serif;margin-top:6px}
.ic-tag{display:inline-block;margin-top:20px;padding:8px 30px;border-radius:30px;background:var(--c);color:#111;font:800 34px 'Rubik',sans-serif}
.teaser{position:absolute;left:1030px;top:940px;font:600 30px 'Rubik',sans-serif;color:#ffd77a;opacity:.9}

/* S4 ruleta */
.rwin{position:absolute;left:110px;top:330px;width:1700px;height:300px;overflow:hidden;border-radius:26px;background:#0007;border:4px solid #ffffff22}
.rstrip{display:flex;padding:10px 0;will-change:transform}
.rc{flex:0 0 220px;height:280px;margin-right:20px;border-radius:22px;background:linear-gradient(170deg,color-mix(in srgb,var(--c) 50%,#000),#120a2e);border:5px solid var(--c);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:14px;color:var(--c);box-shadow:0 0 30px color-mix(in srgb,var(--c) 45%,transparent)}
.rc svg{width:112px;height:112px}
.rc b{font:400 24px Bungee,sans-serif;color:#fff;text-align:center}
.pline{position:absolute;left:958px;top:330px;width:4px;height:300px;background:var(--gold);box-shadow:0 0 16px var(--gold);z-index:3}
.ptop,.pbot{position:absolute;left:934px;width:0;height:0;border-left:26px solid transparent;border-right:26px solid transparent;z-index:3}
.ptop{top:296px;border-top:44px solid var(--gold)}
.pbot{top:626px;border-bottom:44px solid var(--gold)}
.near{position:absolute;left:0;right:0;top:100px;text-align:center;opacity:0;font-size:72px;padding:0 60px}
.near.on{animation:nearIn .5s forwards,glow 1s infinite alternate .5s}
.cta-bot{position:absolute;left:0;right:0;top:740px;text-align:center;opacity:0;transition:opacity .5s}
.cta-bot.on{opacity:1}
.cost{display:block;margin-top:18px;font:600 34px 'Rubik',sans-serif;color:#ffd77a}
.toast{position:absolute;left:60px;bottom:70px;padding:16px 28px;border-radius:16px;background:#000b;border-left:8px solid #ffb020;font:600 30px 'Rubik',sans-serif;transform:translateX(-140%)}
.slide.active .toast{animation:toastIn .6s 6.6s forwards}

/* S5 oferta */
.offer-banner{position:absolute;left:100px;right:100px;top:130px;padding:22px 30px;border-radius:26px;background:linear-gradient(90deg,#c1123a,#ff2d55,#c1123a);border:6px solid var(--gold);text-align:center;font:400 68px Bungee,sans-serif;text-shadow:0 5px 0 #0005;animation:glow 1.2s infinite alternate}
.burst{position:absolute;left:770px;top:360px;width:330px;height:330px;animation:spin 18s linear infinite}
.burst::before,.burst::after{content:"";position:absolute;inset:0;background:var(--red);border-radius:30px;border:6px solid var(--gold)}
.burst::after{transform:rotate(45deg)}
.burst-t{position:absolute;left:770px;top:360px;width:330px;height:330px;display:flex;align-items:center;justify-content:center;font:400 100px Bungee,sans-serif;text-shadow:0 6px 0 #6b0a1a;z-index:2}
.cd-wrap{position:absolute;left:1220px;top:350px;width:600px}
.cd-wrap .lb{font:600 32px 'Rubik',sans-serif;color:#ffd0d9;margin-bottom:12px}
.cd{display:flex;align-items:center;gap:12px;font:400 70px Bungee,sans-serif}
.cd span.d{background:#000a;border:4px solid var(--red);border-radius:14px;padding:8px 22px;box-shadow:0 0 24px #ff2d5588}
.price{margin-top:30px;font:600 40px 'Rubik',sans-serif}
.price s{color:#ff9fb2}
.price b{color:var(--gold);font:400 60px Bungee,sans-serif}
.stockline{margin-top:18px;font:600 34px 'Rubik',sans-serif;color:#ff9fb2}
.stockline b{color:#fff;font:400 42px Bungee,sans-serif}

/* S6 packs */
.shop-t{position:absolute;left:0;right:0;top:110px;text-align:center;font-size:84px}
.packs{position:absolute;left:100px;right:100px;top:290px;display:flex;gap:44px;justify-content:center;align-items:flex-end}
.pack{position:relative;width:440px;padding:36px 24px 34px;border-radius:32px;background:linear-gradient(170deg,#4a1a9c,#1f0b52);border:6px solid #a07bff;text-align:center;box-shadow:0 0 40px #7b2cff66;opacity:0}
.slide.active .pack{animation:pop .6s cubic-bezier(.3,1.5,.5,1) forwards;animation-delay:calc(var(--i)*.35s + .3s)}
.pack.best{width:530px;border-color:var(--gold);background:linear-gradient(170deg,#7a2ad6,#2a0c66);box-shadow:0 0 70px #ffc933aa;padding-top:56px;padding-bottom:44px}
.pile{height:150px;display:flex;justify-content:center;align-items:flex-end;font-size:96px}
.pile .coin{margin-left:-34px}
.pack .amt{font:400 88px/1 Bungee,sans-serif;color:var(--gold);margin-top:10px}
.pack .lbl{font:400 34px Bungee,sans-serif;margin:6px 0 24px}
.pack .btn{font-size:44px;padding:18px 44px;border-radius:22px}
.ribbon{position:absolute;top:-24px;left:50%;transform:translateX(-50%) rotate(-3deg);background:linear-gradient(#ff5a36,#e0122e);color:#fff;font:400 36px Bungee,sans-serif;padding:10px 36px;border-radius:12px;box-shadow:0 6px 0 #8a0a1c;white-space:nowrap}
.paystrip{position:absolute;left:0;right:0;bottom:70px;text-align:center;font:600 40px 'Rubik',sans-serif;color:#e9dcff}

/* S7 corte */
.crt{position:absolute;left:0;right:0;background:#fff;z-index:9;opacity:0}
.slide.active .crt{animation:crt .55s forwards}
.cut-q{position:absolute;left:180px;right:180px;top:50%;transform:translateY(-50%);text-align:center;font:800 88px/1.15 'Rubik',sans-serif;opacity:0}
.slide.active .cut-q{animation:fadeIn 1.8s 1.4s forwards}

/* ENTENDER */
.grid9{position:absolute;left:100px;right:100px;top:250px;display:grid;grid-template-columns:repeat(3,1fr);gap:26px}
.tile{border-radius:24px;padding:26px 30px;background:linear-gradient(160deg,#2a1466,#160a3a);border:3px solid #7b5cff88;opacity:0;min-height:196px}
.slide.active .tile{animation:pop .5s cubic-bezier(.3,1.5,.5,1) forwards;animation-delay:calc(var(--i)*.28s + .4s)}
.tile h3,.gc h3{font:400 38px Bungee,sans-serif;color:var(--gold);margin:0 0 10px}
.tile p,.gc p{font:400 30px/1.3 'Rubik',sans-serif;margin:0;color:#e6ddff}
.grid4{position:absolute;left:100px;right:100px;top:290px;display:grid;grid-template-columns:repeat(4,1fr);gap:26px}
.gc{position:relative;border-radius:24px;padding:26px 28px;background:linear-gradient(160deg,#2a1466,#160a3a);border:3px solid #7b5cff88;min-height:270px;overflow:hidden}
.gc h3{font-size:32px}
.gc.hot{border-color:var(--red);background:linear-gradient(160deg,#5a0f3a,#2a0620);box-shadow:0 0 40px #ff2d5577}
.gc.hot::after{content:"?";position:absolute;right:16px;bottom:-40px;font:400 220px Bungee,sans-serif;color:#ff2d5533}
.banner{grid-column:span 1;border-radius:24px;padding:26px 28px;border:3px dashed var(--cyan);color:var(--cyan);font:600 32px/1.3 'Rubik',sans-serif;display:flex;align-items:center}
.pn{position:absolute;top:290px;width:820px;height:470px;border-radius:32px;padding:36px 44px}
.pn h3{font:400 46px Bungee,sans-serif;margin:0 0 20px}
.pn ul{list-style:none;margin:0;padding:0}
.pn li{font:500 36px/1.3 'Rubik',sans-serif;margin:0 0 14px;padding-left:46px;position:relative}
.pn li::before{position:absolute;left:0;top:0;font-weight:800}
.pn.ok{left:100px;background:linear-gradient(160deg,#0f4d3a,#0a2a24);border:5px solid var(--green)}
.pn.ok h3{color:var(--green)}
.pn.ok li::before{content:"✓";color:var(--green)}
.pn.no{left:1000px;background:linear-gradient(160deg,#5a0f3a,#2a0620);border:5px solid var(--red)}
.pn.no h3{color:#ff8aa5}
.pn.no li::before{content:"?";color:#ff8aa5}
.neq{position:absolute;left:905px;top:470px;width:110px;height:110px;border-radius:50%;background:var(--gold);color:#3a1b00;font:400 84px/104px Bungee,sans-serif;text-align:center;z-index:3;box-shadow:0 0 40px #ffc933aa}
.bar-msg{position:absolute;left:100px;right:100px;top:810px;padding:28px 40px;border-radius:24px;background:#ffffff12;border:3px solid #ffffff33;font:500 38px/1.35 'Rubik',sans-serif;text-align:center}
.mbox{position:absolute;left:150px;top:300px;width:500px;height:500px}
.mbox .rays{left:-450px;top:-450px}
.mbox .bx{position:absolute;inset:60px;border-radius:44px;background:linear-gradient(160deg,#8c3cff,#3a1290);border:10px solid var(--gold);box-shadow:0 0 80px #ffc933aa;display:flex;align-items:center;justify-content:center;font:400 260px Bungee,sans-serif;color:var(--gold);animation:bob 2.4s ease-in-out infinite}
.col2{position:absolute;left:760px;top:290px;width:1060px}
.col2 .def{font:500 38px/1.35 'Rubik',sans-serif;margin:0 0 22px}
.evi{margin-top:26px;border-radius:24px;padding:26px 34px;background:#ffffff10;border:3px solid var(--cyan)}
.evi h4{margin:0 0 10px;font:400 34px Bungee,sans-serif;color:var(--cyan)}
.evi p{margin:0 0 10px;font:400 31px/1.35 'Rubik',sans-serif}
.evi small{font:400 26px 'Rubik',sans-serif;color:#b9adf0}

/* anatomía */
.mock{position:absolute;left:90px;top:230px;width:1000px;height:640px;border-radius:26px;overflow:hidden;background:radial-gradient(900px 500px at 50% 0,#5b1aa8,#2a0c5e 45%,#0d0524);border:4px solid var(--gold);box-shadow:0 0 60px #7b2cff88;font-family:'Rubik',sans-serif}
.m-hud{position:absolute;left:30px;right:30px;top:18px;height:56px;display:flex;align-items:center;gap:16px;font:800 26px 'Rubik',sans-serif}
.m-chip{padding:6px 18px;border-radius:24px;background:#5a1fd0}
.m-rar{display:flex;gap:8px;margin-left:16px}
.m-rar i{width:34px;height:34px;border-radius:8px;background:var(--c);box-shadow:0 0 14px var(--c)}
.m-coins{margin-left:auto;padding:6px 18px;border-radius:24px;background:#0008}
.m-timer{position:absolute;left:90px;right:90px;top:96px;height:60px;border-radius:14px;background:linear-gradient(90deg,#c1123a,#ff2d55,#c1123a);display:flex;align-items:center;justify-content:center;gap:24px;font:400 28px Bungee,sans-serif}
.m-timer b{background:#000a;padding:2px 16px;border-radius:8px}
.m-packs{position:absolute;left:60px;right:60px;top:176px;height:300px;display:flex;gap:30px;align-items:flex-end}
.m-pack{width:250px;height:230px;border-radius:22px;background:linear-gradient(170deg,#4a1a9c,#1f0b52);border:4px solid #a07bff;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:6px;font:400 30px Bungee,sans-serif;color:var(--gold);position:relative}
.m-pack .coin{font-size:54px}
.m-pack.big{width:320px;height:290px;border-color:var(--gold);background:linear-gradient(170deg,#7a2ad6,#2a0c66);box-shadow:0 0 50px #ffc933aa;font-size:44px}
.m-pack em{position:absolute;top:-16px;left:50%;transform:translateX(-50%);background:var(--red);color:#fff;font:400 20px Bungee,sans-serif;padding:4px 16px;border-radius:8px;white-space:nowrap;font-style:normal}
.m-btn{position:absolute;left:320px;top:500px;width:360px;height:70px;border-radius:20px;background:linear-gradient(#54ff9f,#0fb85f);box-shadow:0 6px 0 #067a3d;font:400 36px/70px Bungee,sans-serif;text-align:center}
.m-pay{position:absolute;left:0;right:0;bottom:16px;text-align:center;font:600 26px 'Rubik',sans-serif;color:#e9dcff}
.pin{position:absolute;width:52px;height:52px;border-radius:50%;background:var(--cyan);color:#001;font:800 30px/52px 'Rubik',sans-serif;text-align:center;z-index:6;animation:ping 2s infinite}
.legend{position:absolute;left:1140px;top:225px;width:720px;display:flex;flex-direction:column;gap:11px}
.lg{display:flex;gap:16px;align-items:flex-start;opacity:0}
.slide.active .lg{animation:slideUp .5s forwards;animation-delay:calc(var(--i)*.35s + .3s)}
.lg .n{flex:0 0 46px;height:46px;border-radius:50%;background:var(--cyan);color:#001;font:800 26px/46px 'Rubik',sans-serif;text-align:center}
.lg b{display:block;font:600 30px/1.15 'Rubik',sans-serif}
.lg span{font:400 26px/1.25 'Rubik',sans-serif;color:#cfc4ff}

/* evidencia */
.g3{position:absolute;left:100px;right:100px;top:205px;display:grid;grid-template-columns:repeat(3,1fr);gap:26px}
.ev{border-radius:24px;padding:26px 28px;background:linear-gradient(160deg,#241058,#130a34);border:3px solid #7b5cff66;min-height:340px;display:flex;flex-direction:column}
.ev h3{font:400 28px/1.15 Bungee,sans-serif;color:var(--gold);margin:0 0 12px}
.ev p{font:400 27px/1.3 'Rubik',sans-serif;margin:0 0 auto;color:#efe9ff}
.ev small{display:block;margin-top:12px;font:500 23px/1.25 'Rubik',sans-serif;color:var(--cyan)}
.ev .lv{align-self:flex-start;margin-top:10px;padding:3px 14px;border-radius:20px;background:#ffffff18;font:600 21px 'Rubik',sans-serif;color:#d9ceff}
.foot{position:absolute;left:100px;right:100px;top:925px;font:500 28px/1.35 'Rubik',sans-serif;color:#cfc4ff;border-left:6px solid var(--gold);padding-left:24px}

/* recorridos */
.fl{position:absolute;left:90px;font:400 36px Bungee,sans-serif}
.flow{position:absolute;left:90px;right:90px;display:flex;gap:54px}
.nd{position:relative;flex:1;height:150px;border-radius:22px;padding:12px;font:600 28px/1.15 'Rubik',sans-serif;text-align:center;display:flex;align-items:center;justify-content:center;color:#fff}
.nd:not(:last-child)::after{content:"›";position:absolute;right:-42px;top:50%;transform:translateY(-54%);font:800 64px 'Rubik',sans-serif;color:inherit;opacity:.9}
.flow.v .nd{background:linear-gradient(160deg,#4a1a9c,#2a0c66);border:4px solid #a07bff;color:#c6b0ff}
.flow.v .nd span,.flow.a .nd span{color:#fff}
.flow.a .nd{background:linear-gradient(160deg,#7a0f2b,#3a0716);border:4px solid #ff6f8a;color:#ff9fb2}
.slide.active .nd{animation:nodeGlow 4.2s infinite;animation-delay:calc(var(--i)*.5s)}
.mlab{position:absolute;left:90px;right:90px;top:462px;text-align:center;font:500 26px 'Rubik',sans-serif;color:#cfc4ff}
.mech{position:absolute;left:90px;right:90px;top:505px;display:flex;gap:12px}
.mech div{flex:1;padding:16px 8px;border-radius:16px;background:#ffc93322;border:3px solid var(--gold);color:var(--gold);font:400 21px/1.2 Bungee,sans-serif;text-align:center;display:flex;align-items:center;justify-content:center;min-height:86px}
.disc{position:absolute;left:100px;right:100px;top:895px;padding:22px 34px;border-radius:20px;background:#ffffff12;border:3px solid #ffffff33;font:500 34px/1.35 'Rubik',sans-serif;text-align:center}

/* Argentina */
.hero-n{position:absolute;left:90px;top:210px;font:400 300px/1 Bungee,sans-serif;background:linear-gradient(#fff7b8,#ffc933 48%,#ff8a00);-webkit-background-clip:text;background-clip:text;color:transparent;filter:drop-shadow(0 8px 0 #6b2200) drop-shadow(0 0 40px #ffb02099)}
.hero-t{position:absolute;left:760px;top:290px;width:1060px;font:600 50px/1.25 'Rubik',sans-serif}
.stats{position:absolute;left:100px;right:100px;top:590px;display:grid;grid-template-columns:repeat(4,1fr);gap:26px}
.st{border-radius:24px;padding:26px 28px;background:linear-gradient(160deg,#2a1466,#160a3a);border:3px solid #7b5cff88}
.st .v{font:400 92px/1 Bungee,sans-serif;color:var(--gold)}
.st .l{margin-top:12px;font:400 29px/1.3 'Rubik',sans-serif;color:#e6ddff}
.srcline{position:absolute;left:100px;right:100px;top:930px;font:400 25px/1.4 'Rubik',sans-serif;color:#b9adf0}

/* bolsillo */
.g6{position:absolute;left:100px;top:270px;width:1140px;display:grid;grid-template-columns:repeat(2,1fr);gap:24px}
.bars{position:absolute;left:1320px;top:270px;width:500px}
.bars h4{margin:0 0 20px;font:600 30px/1.3 'Rubik',sans-serif;color:#e6ddff}
.brow{margin-bottom:30px}
.brow .bl{font:500 28px 'Rubik',sans-serif;margin-bottom:8px}
.brow .bt{height:38px;border-radius:19px;background:#ffffff18;overflow:hidden}
.brow .bt i{display:block;height:100%;width:0;border-radius:19px;background:linear-gradient(90deg,#ff9f1c,#ffc933)}
.slide.active .brow .bt i{animation:grow 1.4s .5s cubic-bezier(.2,.8,.2,1) forwards}
@keyframes grow{to{width:var(--w)}}
.brow .bv{font:400 46px Bungee,sans-serif;color:var(--gold);margin-top:6px}

/* problema */
.ring{position:absolute;left:1120px;top:270px;width:600px;height:600px;border-radius:50%;border:10px dashed #ff2d5599;animation:spin 26s linear infinite}
.rn{position:absolute;padding:14px 30px;border-radius:40px;background:#3a0716;border:4px solid #ff6f8a;font:400 32px Bungee,sans-serif;white-space:nowrap;z-index:2}
.rc-t{position:absolute;left:1120px;top:520px;width:600px;text-align:center;font:600 34px/1.3 'Rubik',sans-serif;color:#ffc4d0}
.plist{position:absolute;left:100px;top:290px;width:900px;list-style:none;margin:0;padding:0}
.plist li{font:500 40px/1.3 'Rubik',sans-serif;margin-bottom:26px;padding-left:44px;position:relative}
.plist li::before{content:"";position:absolute;left:0;top:18px;width:20px;height:20px;border-radius:50%;background:#ff6f8a;box-shadow:0 0 16px #ff6f8a}
.warn{position:absolute;left:100px;right:100px;top:900px;padding:22px 34px;border-radius:20px;background:#ffffff12;border:3px solid #ffffff33;font:500 34px/1.35 'Rubik',sans-serif;text-align:center}

/* CUIDAR */
.ch{font:700 84px/1.05 Fraunces,Georgia,serif;color:var(--ca-teal2);margin:0;letter-spacing:-.01em}
.ch.sm{font-size:68px}
.cp{font:400 38px/1.4 'Rubik',sans-serif;color:var(--ca-ink)}
.chd{position:absolute;left:110px;top:90px;width:1500px}
.sig{position:absolute;left:110px;right:110px;top:290px;display:grid;grid-template-columns:repeat(2,1fr);gap:18px 60px}
.sig div{font:500 37px/1.3 'Rubik',sans-serif;padding:14px 0 14px 46px;position:relative;border-bottom:2px solid #15303a1f}
.sig div::before{content:"";position:absolute;left:8px;top:28px;width:18px;height:18px;border-radius:50%;background:var(--ca-teal)}
.cnote{position:absolute;left:110px;right:110px;top:900px;font:500 34px/1.4 'Rubik',sans-serif;color:var(--ca-teal2);padding:20px 30px;background:#2a7b8318;border-radius:18px}
.big-c{position:absolute;left:110px;right:110px;top:250px;font:700 150px/1.05 Fraunces,Georgia,serif;color:var(--ca-teal2);letter-spacing:-.02em}
.verbs{position:absolute;left:110px;right:110px;top:700px;display:flex;flex-wrap:wrap;gap:20px}
.verbs span{padding:16px 40px;border-radius:50px;background:var(--ca-card);border:3px solid var(--ca-teal);font:600 44px 'Rubik',sans-serif;color:var(--ca-teal2)}
.steps{position:absolute;left:110px;right:110px;top:270px;display:grid;grid-template-columns:repeat(3,1fr);gap:30px}
.stp{border-radius:26px;padding:30px 34px;background:var(--ca-card);border:2px solid #15303a22;min-height:290px}
.stp h3{font:700 44px/1.1 Fraunces,Georgia,serif;color:var(--ca-teal2);margin:0 0 14px}
.stp p{font:400 33px/1.35 'Rubik',sans-serif;margin:0}
.dd{position:absolute;left:110px;right:110px;top:620px;display:grid;grid-template-columns:repeat(2,1fr);gap:30px}
.dd div{border-radius:26px;padding:26px 34px;font:400 33px/1.4 'Rubik',sans-serif}
.dd .yes{background:#2a7b8322;border:3px solid var(--ca-teal)}
.dd .nop{background:#b9791c1a;border:3px solid var(--ca-amber)}
.dd h4{margin:0 0 8px;font:700 40px Fraunces,Georgia,serif}
.dd .yes h4{color:var(--ca-teal2)}
.dd .nop h4{color:#7a4c0c}
.two{position:absolute;left:110px;right:110px;top:270px;display:grid;grid-template-columns:5fr 7fr;gap:40px}
.pbox{border-radius:28px;padding:34px 40px}
.pbox.n{background:#b9791c1a;border:3px solid var(--ca-amber)}
.pbox.y{background:var(--ca-card);border:3px solid var(--ca-teal)}
.pbox h3{font:700 48px/1.1 Fraunces,Georgia,serif;margin:0 0 20px}
.pbox.n h3{color:#7a4c0c}
.pbox.y h3{color:var(--ca-teal2)}
.pbox ul{margin:0;padding:0;list-style:none}
.pbox li{font:400 34px/1.35 'Rubik',sans-serif;margin-bottom:14px;padding-left:36px;position:relative}
.pbox li::before{content:"";position:absolute;left:4px;top:16px;width:14px;height:14px;border-radius:50%;background:var(--ca-teal)}
.pbox.n li::before{background:var(--ca-amber)}
.pbox.y .cols{display:grid;grid-template-columns:1fr 1fr;gap:0 30px}
.pillars{position:absolute;left:110px;right:110px;top:560px;display:grid;grid-template-columns:repeat(3,1fr);gap:30px}
.pl{border-radius:26px;padding:30px 34px;background:var(--ca-card);border:2px solid #15303a22;min-height:280px}
.pl h3{font:700 44px/1.1 Fraunces,Georgia,serif;color:var(--ca-teal2);margin:0 0 12px}
.pl p{font:400 33px/1.35 'Rubik',sans-serif;margin:0}
.lead-c{position:absolute;left:110px;right:110px;top:270px;font:600 60px/1.25 Fraunces,Georgia,serif;color:var(--ca-ink)}
.src{position:absolute;left:110px;right:110px;top:250px;display:grid;grid-template-columns:1fr 1fr;gap:0 50px;font:400 23px/1.35 'Rubik',sans-serif}
.src h4{font:700 34px Fraunces,Georgia,serif;color:var(--ca-teal2);margin:0 0 12px}
.src p{margin:0 0 9px}

/* cierre */
.closer{position:absolute;inset:0;background:#0b0620f2;opacity:0;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:44px;text-align:center;padding:0 140px;transition:opacity 1.6s;z-index:8}
.closer.on{opacity:1}
.cl{opacity:0;transition:opacity 1.4s}
.cl.on{opacity:1}
.cl.a{font:800 92px/1.15 'Rubik',sans-serif}
.cl.b{font:500 52px/1.25 'Rubik',sans-serif;color:var(--gold)}
.cl.c{font:400 40px/1.35 'Rubik',sans-serif;color:#cfc4ff}

@media (prefers-reduced-motion:reduce){
  .slide *,.slide::before,.slide::after{animation-iteration-count:1!important}
}
</style>
</head>
<body>
<svg width="0" height="0" style="position:absolute" aria-hidden="true"><defs>
  <linearGradient id="gWood" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#a5541f"/><stop offset="1" stop-color="#5e2a0c"/></linearGradient>
  <linearGradient id="gGold" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#fff3a6"/><stop offset=".5" stop-color="#ffc933"/><stop offset="1" stop-color="#d98200"/></linearGradient>
  <clipPath id="lidClip"><path d="M40 170 V120 Q40 50 200 50 Q360 50 360 120 V170 Z"/></clipPath>
</defs></svg>

<div id="app">
  <div id="vp">
    <div id="rot">Girá el dispositivo para verla mejor</div>
    <div class="stage" id="stage">

<!-- ================= JUGAR ================= -->
<section class="slide t-casino bulbs" id="s1" data-sec="JUGAR" data-note="<b>Apertura · Nahuel (presentación).</b> Presentá el tema y dejá la pregunta en pantalla. No expliques nada todavía: el siguiente paso es la experiencia.">
  <div class="rays" style="left:900px;top:-200px"></div>
  <div class="cover">
    <div class="k">Coloquio · exposición de unos 30 minutos</div>
    <h1 class="title-lg">APUESTAS ONLINE Y MECÁNICAS DE AZAR EN ENTORNOS DIGITALES</h1>
    <p class="sub">Del casino online a los videojuegos</p>
  </div>
  <div class="reels" id="reels"></div>
  <div class="qbadge">¿En qué momento jugar deja de ser solamente jugar?</div>
  <div class="team">Nahuel Agustín Quetglas · Lautaro Joaquín Bueno · Rafael Sandro Colina · Bernardo Sergio Antonio Lang · Thiago Giovanny Julián Leguizamón · Enzo Franco Darío Ramírez</div>
</section>

<section class="slide t-casino bulbs" id="s2" data-sec="JUGAR" data-hud data-note="<b>0–4 min · Lautaro (usuario) y Enzo (narración).</b> Empieza la representación. Nadie explica todavía. El público solo ve la pantalla. Avanzá con ABRIR o con la flecha →.">
  <div class="rays" style="left:800px;top:-160px"></div>
  <div class="notif">1</div>
  <div class="abs" style="left:110px;top:200px;width:920px"><h2 class="title-xl">TENÉS UNA RECOMPENSA GRATUITA</h2></div>
  <div class="abs bob" style="left:1030px;top:250px;width:700px" data-chest></div>
  <div class="abs" style="left:110px;top:780px"><button class="btn green pulse" data-next>ABRIR</button></div>
</section>

<section class="slide t-casino bulbs" id="s3" data-sec="JUGAR" data-hud data-note="<b>Objeto común.</b> El premio es pobre a propósito. Observá que igual hay confeti y luces: se celebra algo que casi no vale.">
  <div class="rays" style="left:-250px;top:-100px"></div>
  <div class="abs" id="chest3" style="left:130px;top:170px;width:720px" data-chest></div>
  <div class="item-card" id="itemCard">
    <div class="ic-art" data-icon="shirt"></div>
    <div class="ic-name">REMERA BÁSICA</div>
    <div class="ic-tag" style="--c:#9aa3b2">COMÚN</div>
  </div>
  <div class="teaser">Próximo premio: ✦ ??? ✦ LEGENDARIO</div>
  <div class="abs" style="left:130px;top:850px"><button class="btn gold" data-next>SEGUIR</button></div>
</section>

<section class="slide t-casino bulbs" id="s4" data-sec="JUGAR" data-hud data-note="<b>Casi-acierto.</b> La ruleta frena pegada al legendario. Dejá girar en silencio y esperá el mensaje. Aparece el aviso de otro jugador que sí lo consiguió.">
  <div class="near title-lg" id="near">¡CASI CONSEGUÍS UN OBJETO LEGENDARIO!</div>
  <div class="rwin"><div class="rstrip" id="rstrip"></div></div>
  <div class="pline"></div><div class="ptop"></div><div class="pbot"></div>
  <div class="cta-bot" id="cta4"><button class="btn red pulse" data-next>VOLVÉ A INTENTARLO<span class="cost"><i class="coin"></i> 100 monedas</span></button></div>
  <div class="toast">Fede_23 obtuvo ✦ LEGENDARIO ✦ hace 1 min</div>
</section>

<section class="slide t-casino bulbs" id="s5" data-sec="JUGAR" data-hud data-note="<b>Oferta por tiempo limitado.</b> La cuenta regresiva corre sola y el stock baja. Pasado un rato, avanzá a la tienda.">
  <div class="offer-banner">OFERTA POR TIEMPO LIMITADO</div>
  <div class="abs bob" style="left:110px;top:290px;width:580px" data-chest data-open></div>
  <div class="burst"></div><div class="burst-t">-60%</div>
  <div class="cd-wrap">
    <div class="lb">Termina en</div>
    <div class="cd"><span class="d" id="cdh">00</span>:<span class="d" id="cdm">09</span>:<span class="d" id="cds">59</span></div>
    <div class="price"><s><i class="coin"></i> 3.000</s> &nbsp;<b><i class="coin"></i> 1.200</b></div>
    <div class="stockline">¡Quedan solo <b id="stock">3</b>!</div>
  </div>
  <div class="abs" style="left:0;right:0;top:850px;text-align:center"><button class="btn red pulse" data-next>APROVECHAR AHORA</button></div>
</section>

<section class="slide t-casino bulbs" id="s6" data-sec="JUGAR" data-hud data-note="<b>Tienda de monedas.</b> El pack más grande se marca como «MEJOR VALOR». Fijate que en ningún lado aparece el precio en pesos.">
  <div class="shop-t title-xl">COMPRÁ MONEDAS</div>
  <div class="packs">
    <div class="pack" style="--i:0"><div class="pile" data-pile="3"></div><div class="amt">500</div><div class="lbl">MONEDAS</div><button class="btn green" data-next>COMPRAR</button></div>
    <div class="pack" style="--i:1"><div class="pile" data-pile="5"></div><div class="amt">1.200</div><div class="lbl">MONEDAS</div><button class="btn green" data-next>COMPRAR</button></div>
    <div class="pack best" style="--i:2"><div class="ribbon">MEJOR VALOR</div><div class="pile" data-pile="7"></div><div class="amt">2.500</div><div class="lbl">MONEDAS</div><button class="btn gold pulse" data-next>COMPRAR</button></div>
  </div>
  <div class="paystrip">Pagá con tu billetera virtual · en 1 toque</div>
</section>

<section class="slide t-black" id="s7" data-cut data-sec="JUGAR" data-note="<b>Corte abrupto.</b> Silencio de 3 o 4 segundos con la pantalla negra. Después, leer la pregunta en voz alta. Fin de la primera parte (0–4 min).">
  <div class="crt"></div>
  <div class="cut-q">¿EN QUÉ MOMENTO JUGAR DEJÓ DE SER SOLAMENTE JUGAR?</div>
</section>

<!-- ================= ENTENDER ================= -->
<section class="slide t-dark" id="s8" data-sec="ENTENDER" data-note="<b>4–9 min · Enzo (narración).</b> Cada casillero es un mecanismo que el público acaba de vivir. Nombralos de a uno mientras aparecen.">
  <div class="hd"><h2 class="h2">¿QUÉ ACABA DE OCURRIR?</h2><p>Nueve mecanismos en menos de un minuto de juego.</p></div>
  <div class="grid9">
    <div class="tile" style="--i:0"><h3>Moneda virtual</h3><p>Oculta el precio real: ¿cuántos pesos son 1.200?</p></div>
    <div class="tile" style="--i:1"><h3>Recompensa</h3><p>Un regalo gratis antes de pedirte nada.</p></div>
    <div class="tile" style="--i:2"><h3>Azar</h3><p>No sabías qué había adentro del cofre.</p></div>
    <div class="tile" style="--i:3"><h3>Rareza</h3><p>Común, épico, legendario: lo raro se desea.</p></div>
    <div class="tile" style="--i:4"><h3>Personalización</h3><p>Objetos que te diferencian de los demás.</p></div>
    <div class="tile" style="--i:5"><h3>Presión social</h3><p>Otros jugadores consiguen lo que vos no.</p></div>
    <div class="tile" style="--i:6"><h3>Oferta temporal</h3><p>Un contador que te apura a decidir.</p></div>
    <div class="tile" style="--i:7"><h3>Repetición</h3><p>«Volvé a intentarlo»: una tirada más.</p></div>
    <div class="tile" style="--i:8"><h3>Facilidad de pago</h3><p>Un toque desde la billetera virtual.</p></div>
  </div>
</section>

<section class="slide t-dark" id="s9" data-sec="ENTENDER" data-note="<b>9–14 min · Bernardo (entorno tecnológico).</b> Aclará que estos sistemas no son equivalentes entre sí. Evitá nombrar juegos o marcas concretas.">
  <div class="hd"><h2 class="h2">VIDEOJUEGOS Y SISTEMAS DE MONETIZACIÓN</h2></div>
  <div class="grid4">
    <div class="gc"><h3>Compras de contenido</h3><p>Sabés qué recibís y cuánto cuesta.</p></div>
    <div class="gc"><h3>Skins y cosméticos</h3><p>Personalizan el personaje o el equipo.</p></div>
    <div class="gc"><h3>Monedas virtuales</h3><p>Se compran con dinero real y se gastan dentro del juego.</p></div>
    <div class="gc"><h3>Pases de batalla</h3><p>Recompensas por progresar durante una temporada.</p></div>
    <div class="gc"><h3>Recompensas diarias</h3><p>Un motivo para volver todos los días.</p></div>
    <div class="gc"><h3>Ofertas por tiempo limitado</h3><p>Decidir rápido, antes de que se acaben.</p></div>
    <div class="gc hot"><h3>Loot boxes</h3><p>El contenido lo decide el azar.</p></div>
    <div class="banner">Estos mecanismos no son equivalentes entre sí.</div>
  </div>
</section>

<section class="slide t-dark" id="s10" data-sec="ENTENDER" data-note="<b>Frase clave.</b> Comprar algo que conocés no es lo mismo que pagar por una posibilidad. Lo segundo comparte rasgos con los juegos de azar y requiere análisis cuando llega a menores.">
  <div class="hd"><h2 class="h2">MICROTRANSACCIÓN ≠ APUESTA</h2></div>
  <div class="pn ok"><h3>COMPRA DIRECTA</h3><ul>
    <li>Elegís un objeto puntual</li><li>Sabés qué recibís</li><li>Sabés cuánto cuesta</li><li>Ejemplo: comprar una skin determinada</li></ul></div>
  <div class="neq">≠</div>
  <div class="pn no"><h3>RECOMPENSA ALEATORIA</h3><ul>
    <li>Pagás por una posibilidad</li><li>El contenido lo decide el azar</li><li>Puede repetirse hasta conseguir lo que querés</li><li>Ejemplo: ciertas loot boxes</li></ul></div>
  <div class="bar-msg">No toda compra dentro de un videojuego es una apuesta. Pero algunos mecanismos aleatorios comparten rasgos con los juegos de azar.</div>
</section>

<section class="slide t-dark" id="s11" data-sec="ENTENDER" data-note="<b>Cuidado con la causalidad.</b> Las investigaciones muestran asociaciones, no una relación causal automática. Repetilo con claridad.">
  <div class="hd"><h2 class="h2">¿QUÉ ES UNA LOOT BOX?</h2></div>
  <div class="mbox"><div class="rays"></div><div class="bx">?</div></div>
  <div class="col2">
    <p class="def">Una recompensa virtual cuyo contenido <b>no se conoce antes de abrirla</b>.</p>
    <p class="def">En algunos juegos se obtiene con dinero real, o con monedas compradas con dinero.</p>
    <div class="evi">
      <h4>Qué dice la evidencia</h4>
      <p>Hay asociaciones entre participar o gastar en loot boxes y ciertos indicadores de juego problemático.</p>
      <p><b>Asociación no es causa:</b> no se puede afirmar que provoquen ludopatía por sí solas.</p>
      <small>Montiel et al. (2022, PLOS ONE) · Han, Li y Lin (2026, Addictive Behaviors)</small>
    </div>
  </div>
</section>

<section class="slide t-dark" id="s12" data-sec="ENTENDER" data-note="<b>Anatomía de la pantalla.</b> Volvé sobre la tienda del inicio y señalá cada elemento. Sobre el color: rojo y dorado son práctica habitual de la industria, pero la evidencia experimental de un color aislado es limitada.">
  <div class="hd"><h2 class="h2">ANATOMÍA DE LA PANTALLA</h2></div>
  <div class="mock">
    <div class="m-hud"><span class="m-chip">NIV 7</span><span class="m-rar"><i style="--c:#9aa3b2"></i><i style="--c:#37d67a"></i><i style="--c:#3da5ff"></i><i style="--c:#b45cff"></i><i style="--c:#ffb020"></i></span><span class="m-coins"><i class="coin"></i> 120</span></div>
    <div class="m-timer">OFERTA LIMITADA <b>09:41</b></div>
    <div class="m-packs">
      <div class="m-pack"><i class="coin"></i>500</div>
      <div class="m-pack"><i class="coin"></i>1.200</div>
      <div class="m-pack big"><em>MEJOR VALOR</em><i class="coin"></i>2.500</div>
    </div>
    <div class="m-btn">COMPRAR</div>
    <div class="m-pay">Pagá con billetera virtual · 1 toque</div>
    <div class="pin" style="left:12px;top:300px">1</div>
    <div class="pin" style="left:690px;top:490px">2</div>
    <div class="pin" style="left:836px;top:92px">3</div>
    <div class="pin" style="left:894px;top:150px">4</div>
    <div class="pin" style="left:514px;top:192px">5</div>
    <div class="pin" style="left:394px;top:18px">6</div>
    <div class="pin" style="left:934px;top:72px">7</div>
    <div class="pin" style="left:880px;top:570px">8</div>
  </div>
  <div class="legend">
    <div class="lg" style="--i:0"><div class="n">1</div><div><b>Rojo y dorado sobre fondo oscuro</b><span>Contraste máximo; asociados a excitación y riqueza.</span></div></div>
    <div class="lg" style="--i:1"><div class="n">2</div><div><b>Un solo botón que late</b><span>Lleva la mirada a una única acción.</span></div></div>
    <div class="lg" style="--i:2"><div class="n">3</div><div><b>Cuenta regresiva</b><span>Urgencia: decidir rápido, sin pensar.</span></div></div>
    <div class="lg" style="--i:3"><div class="n">4</div><div><b>«Mejor valor» más grande</b><span>Empuja hacia la opción de mayor gasto.</span></div></div>
    <div class="lg" style="--i:4"><div class="n">5</div><div><b>Monedas, no pesos</b><span>El precio real queda fuera de la vista.</span></div></div>
    <div class="lg" style="--i:5"><div class="n">6</div><div><b>Colores por rareza</b><span>Lo raro se ve, se compara y se desea.</span></div></div>
    <div class="lg" style="--i:6"><div class="n">7</div><div><b>Luces, brillo y movimiento</b><span>Atención sostenida, sin pausas naturales.</span></div></div>
    <div class="lg" style="--i:7"><div class="n">8</div><div><b>Pago en un toque</b><span>Casi sin fricción entre el deseo y el gasto.</span></div></div>
  </div>
</section>

<section class="slide t-dark" id="s13" data-sec="ENTENDER" data-note="<b>Qué se sabe y con qué solidez.</b> Lo mejor documentado experimentalmente: sonido, casi-aciertos y recompensas variables. Los estudios sobre apps de apuestas y loot boxes son más descriptivos o correlacionales.">
  <div class="hd"><h2 class="h2">LO QUE DICE LA INVESTIGACIÓN</h2></div>
  <div class="g3">
    <div class="ev"><h3>RECOMPENSA VARIABLE Y CASI-ACIERTO</h3><p>Los premios impredecibles sostienen la conducta; el casi-acierto activa circuitos de recompensa como una victoria.</p><small>Clark et al. (2009) · Dixon et al. (2011)</small><span class="lv">Experimental</span></div>
    <div class="ev"><h3>PÉRDIDAS DISFRAZADAS DE GANANCIA</h3><p>Ganar menos de lo apostado, con luces y sonido, activa casi igual que una victoria real.</p><small>Dixon et al. (2010, Addiction)</small><span class="lv">Experimental</span></div>
    <div class="ev"><h3>SONIDO DE CELEBRACIÓN</h3><p>Aumenta la activación fisiológica y lleva a sobreestimar lo ganado.</p><small>Dixon et al. (2013, J. of Gambling Studies)</small><span class="lv">Experimental</span></div>
    <div class="ev"><h3>URGENCIA Y ESCASEZ</h3><p>Cuentas regresivas y mensajes de «tiempo limitado» están catalogados como patrones oscuros.</p><small>Mathur et al. (2019)</small><span class="lv">Relevamiento de sitios de compras</span></div>
    <div class="ev"><h3>DISEÑO DE LOOT BOXES</h3><p>Monedas intermedias, casi-aciertos y objetos exclusivos varían entre juegos y se estudian como posibles factores de riesgo.</p><small>«The hidden intricacy of loot box design» (DiGRA)</small><span class="lv">Análisis de diseño</span></div>
    <div class="ev"><h3>APPS DE APUESTAS DEPORTIVAS</h3><p>Colores, imágenes, marca, multiapuestas y herramientas grupales crean una experiencia inmersiva y sensación de urgencia.</p><small>Universidad de Glasgow · jóvenes en Australia</small><span class="lv">Cualitativa</span></div>
  </div>
  <div class="foot">Sobre el color: rojo y dorado son habituales en el diseño de casinos, pero la evidencia experimental de un color aislado es limitada. Lo mejor documentado es el efecto del sonido, los casi-aciertos y las recompensas variables.</div>
</section>

<section class="slide t-dark" id="s14" data-sec="ENTENDER" data-note="<b>14–19 min · Bernardo y Nahuel.</b> Dos recorridos paralelos y, en el medio, los mecanismos que pueden aparecer en distintos grados. Aclarar expresamente que compartir mecanismos no convierte a un videojuego en apuesta.">
  <div class="hd"><h2 class="h2">DEL VIDEOJUEGO A LAS APUESTAS ONLINE</h2></div>
  <div class="fl gold" style="top:232px;color:#c6b0ff">ENTORNO DE VIDEOJUEGO</div>
  <div class="flow v" style="top:290px">
    <div class="nd" style="--i:0"><span>Juego</span></div><div class="nd" style="--i:1"><span>Recompensa</span></div><div class="nd" style="--i:2"><span>Personalización</span></div><div class="nd" style="--i:3"><span>Objeto deseado</span></div><div class="nd" style="--i:4"><span>Microtransacción</span></div><div class="nd" style="--i:5"><span>Posible recompensa aleatoria</span></div><div class="nd" style="--i:6"><span>Repetición</span></div>
  </div>
  <div class="mlab">Mecanismos que pueden estar presentes, en distintos grados, en ambos recorridos</div>
  <div class="mech"><div>Expectativa</div><div>Recompensa</div><div>Azar</div><div>Repetición</div><div>Presión social</div><div>Facilidad de pago</div><div>Disponibilidad</div></div>
  <div class="fl" style="top:622px;color:#ff9fb2">APUESTA ONLINE</div>
  <div class="flow a" style="top:680px">
    <div class="nd" style="--i:0"><span>Curiosidad</span></div><div class="nd" style="--i:1"><span>Primera apuesta</span></div><div class="nd" style="--i:2"><span>Resultado</span></div><div class="nd" style="--i:3"><span>Nueva apuesta</span></div><div class="nd" style="--i:4"><span>Intento de recuperar</span></div><div class="nd" style="--i:5"><span>Más tiempo o dinero</span></div><div class="nd" style="--i:6"><span>Posibles consecuencias</span></div>
  </div>
  <div class="disc">Compartir algunos mecanismos <b>no convierte automáticamente</b> a un videojuego en un juego de apuestas.</div>
</section>

<section class="slide t-dark" id="s15" data-sec="ENTENDER" data-note="<b>Contexto argentino · Rafael.</b> Datos de UNICEF. Recordá que el juego de azar está prohibido para menores de 18 años y que el ingreso suele darse por apuestas deportivas, sobre todo fútbol.">
  <div class="hd"><h2 class="h2">APUESTAS ONLINE ENTRE ADOLESCENTES EN ARGENTINA</h2></div>
  <div class="hero-n"><span data-count="24" data-suf="%">24%</span></div>
  <div class="hero-t">de las y los adolescentes de 12 a 17 años dijo haber apostado dinero online alguna vez.</div>
  <div class="stats">
    <div class="st"><div class="v"><span data-count="13" data-suf="%">13%</span></div><div class="l">de chicas y chicos de 12 a 14 años también lo hizo</div></div>
    <div class="st"><div class="v"><span data-count="13" data-suf="">13</span></div><div class="l">años: edad en que suele abrirse la billetera virtual</div></div>
    <div class="st"><div class="v"><span data-count="8" data-suf="/10">8/10</span></div><div class="l">conoce a alguien que usó apps de apuestas, o las usó, en el último año</div></div>
    <div class="st"><div class="v"><span data-count="4" data-suf="/10">4/10</span></div><div class="l">nunca habló del tema en su casa</div></div>
  </div>
  <div class="srcline">Fuentes: UNICEF y UNESCO, Kids Online Argentina 2025 (5.910 niñas, niños y adolescentes); UNICEF Argentina y Bienestar Digital, consulta U-Report.</div>
</section>

<section class="slide t-dark" id="s16" data-sec="ENTENDER" data-note="<b>Normalización y accesibilidad · Rafael.</b> Un casino en el bolsillo: disponible siempre, rápido, con bonos y publicidad. Las barras muestran dónde chicas y chicos destacan la presencia de las marcas.">
  <div class="hd"><h2 class="h2">UN CASINO EN EL BOLSILLO</h2></div>
  <div class="g6">
    <div class="gc"><h3>Siempre disponible</h3><p>A cualquier hora, sin salir de casa.</p></div>
    <div class="gc"><h3>En el celular</h3><p>Un acceso que cabe en el bolsillo.</p></div>
    <div class="gc"><h3>Rápido</h3><p>Apostar y pagar toma segundos.</p></div>
    <div class="gc"><h3>Bonos y promociones</h3><p>El bono de bienvenida vuelve fácil y atractivo el ingreso.</p></div>
    <div class="gc"><h3>Pagos fáciles</h3><p>Billeteras virtuales, que suelen abrirse cerca de los 13 años.</p></div>
    <div class="gc"><h3>Publicidad e influencers</h3><p>Marcas presentes en redes, deportes e internet.</p></div>
  </div>
  <div class="bars">
    <h4>Dónde destacan la presencia de las marcas de apuestas</h4>
    <div class="brow"><div class="bl">En internet, todo el tiempo</div><div class="bt"><i style="--w:35%"></i></div><div class="bv">35%</div></div>
    <div class="brow"><div class="bl">En redes, vía influencers</div><div class="bt"><i style="--w:27%"></i></div><div class="bv">27%</div></div>
    <div class="brow"><div class="bl">En eventos deportivos</div><div class="bt"><i style="--w:14%"></i></div><div class="bv">14%</div></div>
    <div style="font:400 23px/1.3 Rubik,sans-serif;color:#b9adf0">Fuente: UNICEF Argentina, consulta U-Report.</div>
  </div>
</section>

<section class="slide t-dark" id="s17" data-sec="ENTENDER" data-note="<b>¿Cuándo aparece el problema? · Lautaro.</b> Foco en la pérdida de control. Una apuesta no permite diagnosticar ludopatía: se miran persistencia, intensidad y consecuencias.">
  <div class="hd"><h2 class="h2">¿CUÁNDO APARECE EL PROBLEMA?</h2></div>
  <ul class="plist">
    <li>Intentar recuperar el dinero perdido</li>
    <li>Aumentar de a poco el tiempo o el dinero</li>
    <li>Ocultar cuánto se apuesta</li>
    <li>Seguir a pesar de las consecuencias negativas</li>
  </ul>
  <div class="ring"></div>
  <div class="rn" style="left:1330px;top:236px">Apostar</div>
  <div class="rn" style="left:1622px;top:548px">Perder</div>
  <div class="rn" style="left:1230px;top:840px">Intentar recuperar</div>
  <div class="rn" style="left:960px;top:548px">Apostar más</div>
  <div class="rc-t" style="top:500px">un circuito que se retroalimenta</div>
  <div class="warn">Realizar una apuesta no permite diagnosticar ludopatía. Se mira la <b>persistencia</b>, la <b>intensidad</b> y las <b>consecuencias</b>.</div>
</section>

<!-- ================= CUIDAR ================= -->
<section class="slide t-calm" id="s18" data-sec="CUIDAR" data-note="<b>19–24 min · Thiago.</b> Cambia el clima: sin luces ni movimiento. Estas señales son motivos para prestar atención, no un diagnóstico.">
  <div class="chd"><h2 class="ch">Señales de alerta</h2></div>
  <div class="sig">
    <div>Preocupación frecuente por apuestas o resultados</div>
    <div>Cambios significativos de conducta</div>
    <div>Irritabilidad</div>
    <div>Alteraciones del sueño</div>
    <div>Retraimiento</div>
    <div>Disminución del rendimiento académico</div>
    <div>Gastos o movimientos de dinero difíciles de explicar</div>
    <div>Pedidos reiterados de dinero</div>
    <div>Ocultamiento o minimización del dinero y el tiempo utilizados</div>
    <div>Intentos repetidos de recuperar pérdidas</div>
  </div>
  <div class="cnote">No son un diagnóstico: son motivos para prestar atención y abrir un espacio de diálogo.</div>
</section>

<section class="slide t-calm" id="s19" data-sec="CUIDAR" data-note="<b>Idea principal.</b> Detectar no significa diagnosticar. Cinco verbos que sí le corresponden a la comunidad educativa.">
  <div class="big-c">Detectar no significa diagnosticar.</div>
  <div class="verbs"><span>Observar</span><span>Escuchar</span><span>Informar</span><span>Acompañar</span><span>Activar redes de ayuda</span></div>
</section>

<section class="slide t-calm" id="s20" data-sec="CUIDAR" data-note="<b>Breve representación · Lautaro y Thiago.</b> Un adulto de referencia detecta cambios y abre el diálogo sin acusaciones ni etiquetas. El guion de esta pantalla es una sugerencia editable.">
  <div class="chd"><h2 class="ch sm">Escena: un adulto de referencia nota un cambio</h2></div>
  <div class="steps">
    <div class="stp"><h3>Nota el cambio</h3><p>Duerme mal, se aísla, pide dinero seguido. Observa sin sacar conclusiones.</p></div>
    <div class="stp"><h3>Elige el momento</h3><p>Un lugar tranquilo, sin público y sin apuro.</p></div>
    <div class="stp"><h3>Abre el diálogo</h3><p>«Te noto distinto últimamente. ¿Querés que hablemos?»</p></div>
  </div>
  <div class="dd">
    <div class="yes"><h4>Ayuda</h4>Preguntar con curiosidad, escuchar sin interrumpir y ofrecer acompañamiento.</div>
    <div class="nop"><h4>Evitar</h4>Acusar, etiquetar («sos ludópata»), sermonear o castigar.</div>
  </div>
</section>

<section class="slide t-calm" id="s21" data-sec="CUIDAR" data-note="<b>24–28 min · Thiago.</b> Qué le corresponde y qué no a la institución educativa. No asume funciones diagnósticas ni resuelve sola una situación de juego problemático.">
  <div class="chd"><h2 class="ch">¿Qué puede hacer la comunidad educativa?</h2></div>
  <div class="two">
    <div class="pbox n"><h3>Lo que no le corresponde</h3><ul><li>Diagnosticar</li><li>Resolver sola una situación de juego problemático</li></ul></div>
    <div class="pbox y"><h3>Lo que sí puede</h3><div class="cols"><ul>
      <li>Abrir espacios de conversación y educación</li>
      <li>Trabajar la alfabetización y la ciudadanía digital</li>
      <li>Explicar los mecanismos comerciales y tecnológicos</li>
      <li>Promover pensamiento crítico frente a la publicidad</li></ul><ul>
      <li>Observar cambios significativos sin etiquetar</li>
      <li>Establecer canales para pedir ayuda</li>
      <li>Acompañar a las familias</li>
      <li>Recurrir a equipos y profesionales especializados</li></ul></div></div>
  </div>
</section>

<section class="slide t-calm" id="s22" data-sec="CUIDAR" data-note="<b>Prevención y ciudadanía digital.</b> El entorno está diseñado: la prevención no puede depender solo del autocontrol individual.">
  <div class="chd"><h2 class="ch">Prevención y ciudadanía digital</h2></div>
  <div class="lead-c" style="top:250px">El entorno está diseñado. La prevención no puede reducirse a exigir autocontrol individual.</div>
  <div class="pillars">
    <div class="pl"><h3>Entender el diseño</h3><p>Aprender a leer una pantalla como la del inicio: qué busca provocar cada elemento.</p></div>
    <div class="pl"><h3>Pensar con criterio</h3><p>Mirar con distancia la publicidad, los influencers y las promociones.</p></div>
    <div class="pl"><h3>Cuidar y escuchar</h3><p>Conversar sin estigmatizar y sostener canales para pedir ayuda.</p></div>
  </div>
</section>

<!-- ================= CIERRE ================= -->
<section class="slide t-casino bulbs" id="s23" data-sec="CUIDAR" data-note="<b>28–30 min · Cierre.</b> Vuelve la pantalla inicial. La recompensa no se abre. Esperá unos segundos: aparece «Ahora sabemos por qué queremos abrirla». Nahuel cierra.">
  <div class="rays" style="left:800px;top:-160px"></div>
  <div class="abs" style="left:110px;top:200px;width:920px"><h2 class="title-xl">TENÉS UNA RECOMPENSA GRATUITA</h2></div>
  <div class="abs bob" style="left:1030px;top:250px;width:700px" data-chest></div>
  <div class="abs" style="left:110px;top:780px"><button class="btn green pulse" id="noOpen">ABRIR</button></div>
  <div class="closer" id="closer">
    <div class="cl a" id="cla">Ahora sabemos por qué queremos abrirla.</div>
    <div class="cl b" id="clb">¿En qué momento jugar deja de ser solamente jugar?</div>
    <div class="cl c" id="clc">Comprender los mecanismos también es una forma de prevención.</div>
  </div>
</section>

<section class="slide t-calm" id="s24" data-sec="CUIDAR" data-note="<b>Fuentes.</b> Las del documento del grupo más la investigación de diseño usada en las pantallas de mecanismos y evidencia.">
  <div class="chd"><h2 class="ch sm">Fuentes</h2></div>
  <div class="src">
    <div>
      <h4>Del documento del grupo</h4>
      <p>UNICEF Argentina. Niñas, niños y adolescentes conectados. Kids Online Argentina. Informe de resultados, 2025.</p>
      <p>UNICEF Argentina. Zoom a las apuestas online. Guía para familias, 2025.</p>
      <p>UNICEF Argentina. Apuestas online: de la preocupación a la acción, 2026.</p>
      <p>Argentina.gob.ar, Con Vos en la Web. Pautas para evitar que los adolescentes apuesten online (jun. 2026).</p>
      <p>Argentina.gob.ar, Con Vos en la Web. Así protegerás a tus hijos o alumnos de las apuestas en línea (jun. 2026).</p>
      <p>OMS. Juegos de azar y de apuestas, 2024.</p>
      <p>Montiel, Basterra-González, Machimbarrena, Ortega-Barón y González-Cabrera (2022). Loot box engagement. PLOS ONE, 17(1).</p>
      <p>Han, Li y Lin (2026). Adolescents and loot boxes. Addictive Behaviors, 181.</p>
    </div>
    <div>
      <h4>Investigación de diseño</h4>
      <p>Dixon, Harrigan, Sandhu, Collins y Fugelsang (2010). Losses disguised as wins in modern multi-line video slot machines. Addiction, 105.</p>
      <p>Dixon et al. (2011). Psychophysical arousal signatures of near-misses in slot machine play. International Gambling Studies, 11.</p>
      <p>Dixon et al. (2013). The impact of sound in modern multiline video slot machine play. Journal of Gambling Studies.</p>
      <p>Clark, Lawrence, Astley-Jones y Gray (2009). Gambling near-misses enhance motivation to gamble and recruit win-related brain circuitry. Neuron, 61.</p>
      <p>Mathur et al. (2019). Dark Patterns at Scale: Findings from a Crawl of 11K Shopping Websites.</p>
      <p>The hidden intricacy of loot box design: A granular description of random monetized reward features. DiGRA.</p>
      <p>University of Glasgow. Sports Betting in Australia (proyecto sobre apps de apuestas deportivas y jóvenes).</p>
      <p>UNICEF Argentina y Bienestar Digital. Consulta U-Report sobre apuestas online.</p>
    </div>
  </div>
</section>

      <canvas id="confetti" width="1920" height="1080"></canvas>
      <div class="stag" id="stag">JUGAR</div>
      <div class="xp"><i id="xpf"></i></div>
    </div>
    <div id="notes"></div>
  </div>
  <div id="bar">
    <button class="cb" id="bPrev" aria-label="Anterior">‹ Anterior</button>
    <span id="cnt">1 / 24</span>
    <button class="cb" id="bNext" aria-label="Siguiente">Siguiente ›</button>
    <button class="cb" id="bSnd" aria-pressed="false">Sonido: no</button>
    <button class="cb" id="bNotes">Notas</button>
    <button class="cb" id="bFs">Pantalla completa</button>
    <span id="secchip"></span>
  </div>
</div>

<script>
(function(){
'use strict';
var stage=document.getElementById('stage'),vp=document.getElementById('vp');
var slides=Array.prototype.slice.call(document.querySelectorAll('.slide'));
var N=slides.length,cur=-1;

/* ===== iconos ===== */
var P={
 shirt:'M20 8 L8 16 L14 28 L20 25 V56 H44 V25 L50 28 L56 16 L44 8 Q32 18 20 8Z',
 shield:'M32 6 L54 14 V32 Q54 50 32 60 Q10 50 10 32 V14Z',
 gem:'M18 10 H46 L58 26 L32 58 L6 26Z',
 star:'M32 5 L39 24 L59 25 L43 38 L49 58 L32 46 L15 58 L21 38 L5 25 L25 24Z',
 crown:'M8 46 L12 18 L24 32 L32 12 L40 32 L52 18 L56 46Z M10 50 H54 V56 H10Z'
};
function ICON(n){return '<svg viewBox="0 0 64 64" fill="currentColor" stroke="#0007" stroke-width="2" stroke-linejoin="round"><path d="'+P[n]+'"/></svg>';}
var CHEST='<svg viewBox="0 0 400 360" class="chest">'+
'<ellipse cx="200" cy="342" rx="170" ry="14" fill="#0006"/>'+
'<rect x="40" y="170" width="320" height="165" rx="16" fill="url(#gWood)" stroke="#2b0d00" stroke-width="8"/>'+
'<path d="M48 225H352M48 280H352" stroke="#2b0d0055" stroke-width="5"/>'+
'<rect x="72" y="170" width="34" height="165" fill="url(#gGold)" stroke="#7a4a00" stroke-width="4"/>'+
'<rect x="294" y="170" width="34" height="165" fill="url(#gGold)" stroke="#7a4a00" stroke-width="4"/>'+
'<ellipse class="inside" cx="200" cy="172" rx="150" ry="14" fill="#fff7b0"/>'+
'<g class="lid"><path d="M40 170 V120 Q40 50 200 50 Q360 50 360 120 V170 Z" fill="url(#gWood)" stroke="#2b0d00" stroke-width="8"/>'+
'<g clip-path="url(#lidClip)"><rect x="72" y="40" width="34" height="140" fill="url(#gGold)" stroke="#7a4a00" stroke-width="4"/><rect x="294" y="40" width="34" height="140" fill="url(#gGold)" stroke="#7a4a00" stroke-width="4"/></g></g>'+
'<rect x="172" y="150" width="56" height="70" rx="12" fill="url(#gGold)" stroke="#7a4a00" stroke-width="5"/>'+
'<circle cx="200" cy="180" r="9" fill="#5a2f00"/><rect x="196" y="182" width="8" height="20" rx="3" fill="#5a2f00"/></svg>';

/* ===== construcción dinámica ===== */
var HUD='<div class="hud"><div class="pill lvl">NIV 7</div><div class="pill"><span class="coin"></span> 120 <b>+</b></div><div class="pill"><svg viewBox="0 0 64 64" fill="#3be3ff" stroke="#0007" stroke-width="2"><path d="'+P.gem+'"/></svg> 3 <b>+</b></div></div>';
Array.prototype.forEach.call(document.querySelectorAll('[data-hud]'),function(s){s.insertAdjacentHTML('afterbegin',HUD);});
Array.prototype.forEach.call(document.querySelectorAll('[data-chest]'),function(el){el.innerHTML=CHEST;if(el.hasAttribute('data-open'))el.querySelector('.chest').classList.add('open');});
Array.prototype.forEach.call(document.querySelectorAll('[data-icon]'),function(el){el.innerHTML=ICON(el.getAttribute('data-icon'));});
Array.prototype.forEach.call(document.querySelectorAll('[data-pile]'),function(el){var n=+el.getAttribute('data-pile'),h='';for(var i=0;i<n;i++)h+='<i class="coin" style="margin-bottom:'+(i%2?18:0)+'px"></i>';el.innerHTML=h;});

/* rodillos de la portada: terminan en corona, corona, gema (casi-acierto) */
(function(){
  var cols={crown:'#ffb020',gem:'#3da5ff',star:'#b45cff',shield:'#37d67a',shirt:'#9aa3b2'};
  var seq=['star','shield','gem','shirt','crown','star','shield','gem'];
  var targets=['crown','crown','gem'],box=document.getElementById('reels');
  targets.forEach(function(t,i){
    var rot=seq.slice(i*2).concat(seq.slice(0,i*2)),list=rot.concat([t]);
    var r=document.createElement('div');r.className='reel';r.style.setProperty('--d',(1.8+i*.9)+'s');
    r.innerHTML='<div class="strip">'+list.map(function(n){return '<div class="cell" style="color:'+cols[n]+'">'+ICON(n)+'</div>';}).join('')+'</div>';
    box.appendChild(r);
  });
})();

/* ruleta de la pantalla 4 */
var RAR={c:{n:'COMÚN',col:'#9aa3b2',ic:'shirt'},u:{n:'POCO COMÚN',col:'#37d67a',ic:'shield'},r:{n:'RARO',col:'#3da5ff',ic:'gem'},e:{n:'ÉPICO',col:'#b45cff',ic:'star'},l:{n:'LEGENDARIO',col:'#ffb020',ic:'crown'}};
var STOP=36,CARD=240,WIN_C=850;
(function(){
  var seed=7;function rnd(){seed=(seed*16807)%2147483647;return seed/2147483647;}
  var h='';
  for(var i=0;i<46;i++){
    var k,x=rnd();
    if(i===STOP-1)k='r';else if(i===STOP)k='e';else if(i===STOP+1)k='l';else if(i===STOP+2)k='e';
    else if(x<.46)k='c';else if(x<.72)k='u';else if(x<.88)k='r';else if(x<.98)k='e';else k='c';
    var d=RAR[k];
    h+='<div class="rc" style="--c:'+d.col+'">'+ICON(d.ic)+'<b>'+d.n+'</b></div>';
  }
  document.getElementById('rstrip').innerHTML=h;
})();

/* ===== utilidades ===== */
var timers=[],cdIv=0;
function T(f,ms){timers.push(setTimeout(f,ms));}
function clearT(){timers.forEach(clearTimeout);timers=[];if(cdIv){clearInterval(cdIv);cdIv=0;}}

/* sonido (apagado por defecto) */
var audioOn=false,ac=null;
function tone(f,d,type,v,t0){
  if(!audioOn)return;
  try{
    ac=ac||new (window.AudioContext||window.webkitAudioContext)();
    if(ac.state==='suspended')ac.resume();
    var o=ac.createOscillator(),g=ac.createGain(),t=ac.currentTime+(t0||0);
    o.type=type||'sine';o.frequency.value=f;
    g.gain.setValueAtTime(v||.06,t);g.gain.exponentialRampToValueAtTime(.0001,t+d);
    o.connect(g);g.connect(ac.destination);o.start(t);o.stop(t+d+.02);
  }catch(e){}
}
var sfx={
  coin:function(){tone(988,.08,'square',.04,0);tone(1319,.25,'square',.04,.08);},
  win:function(){[523,659,784,1047].forEach(function(f,i){tone(f,.18,'triangle',.07,i*.08);});},
  near:function(){[784,659,523,392].forEach(function(f,i){tone(f,.16,'sawtooth',.035,i*.1);});},
  thud:function(){tone(110,.3,'sine',.1,0);},
  alarm:function(){tone(880,.1,'square',.035,0);tone(880,.1,'square',.035,.16);}
};

/* confeti */
var cv=document.getElementById('confetti'),cx=cv.getContext('2d'),parts=[],raf=0;
function burst(x,y,n,cols){
  cols=cols||['#ffc933','#ff2d55','#3be3ff','#20e58f','#ff3df2','#ffffff'];
  for(var i=0;i<n;i++){var a=Math.random()*Math.PI*2,s=6+Math.random()*16;
    parts.push({x:x,y:y,vx:Math.cos(a)*s,vy:Math.sin(a)*s-8,w:10+Math.random()*12,h:6+Math.random()*8,r:Math.random()*6,vr:(Math.random()-.5)*.4,c:cols[i%cols.length],l:70+Math.random()*40});}
  if(!raf)raf=requestAnimationFrame(tick);
}
function tick(){
  cx.clearRect(0,0,1920,1080);
  parts=parts.filter(function(p){return p.l>0;});
  parts.forEach(function(p){p.x+=p.vx;p.y+=p.vy;p.vy+=.55;p.vx*=.985;p.r+=p.vr;p.l--;
    cx.save();cx.translate(p.x,p.y);cx.rotate(p.r);cx.globalAlpha=Math.min(1,p.l/30);cx.fillStyle=p.c;cx.fillRect(-p.w/2,-p.h/2,p.w,p.h);cx.restore();});
  raf=parts.length?requestAnimationFrame(tick):0;
  if(!raf)cx.clearRect(0,0,1920,1080);
}

/* ===== escenas con secuencia ===== */
var hooks={
 s3:{enter:function(){
   var ch=document.querySelector('#chest3 .chest'),card=document.getElementById('itemCard');
   ch.classList.remove('open');card.classList.remove('show');
   var wrap=document.getElementById('chest3');wrap.classList.remove('shaking');
   T(function(){wrap.classList.add('shaking');},250);
   T(function(){wrap.classList.remove('shaking');ch.classList.add('open');sfx.thud();burst(480,420,50,['#9aa3b2','#cfd4de','#ffffff']);},1400);
   T(function(){card.classList.add('show');},1650);
 }},
 s4:{enter:function(){
   var st=document.getElementById('rstrip'),near=document.getElementById('near'),cta=document.getElementById('cta4');
   near.classList.remove('on');cta.classList.remove('on');
   st.style.transition='none';st.style.transform='translateX(0)';
   void st.offsetWidth;
   var target=WIN_C-(STOP*CARD+110)-85;
   T(function(){st.style.transition='transform 5s cubic-bezier(.08,.6,.12,1)';st.style.transform='translateX('+target+'px)';},300);
   T(function(){near.classList.add('on');cta.classList.add('on');sfx.near();burst(960,470,60,['#ffc933','#ffe27a','#b45cff']);},5500);
 }},
 s5:{enter:function(){
   var m=9,s=59,stock=3;
   var eM=document.getElementById('cdm'),eS=document.getElementById('cds'),eK=document.getElementById('stock');
   function paint(){eM.textContent=('0'+m).slice(-2);eS.textContent=('0'+s).slice(-2);eK.textContent=stock;}
   paint();sfx.alarm();
   var t=0;
   cdIv=setInterval(function(){t++;s--;if(s<0){s=59;m--;}if(t===6){stock=2;sfx.alarm();}paint();},1000);
 }},
 s6:{enter:function(){sfx.coin();}},
 s15:{enter:function(){
   Array.prototype.forEach.call(document.querySelectorAll('#s15 [data-count]'),function(el,i){
     var to=+el.getAttribute('data-count'),suf=el.getAttribute('data-suf'),t0=null,dur=1600;
     el.textContent='0'+suf;
     function step(ts){if(t0===null)t0=ts+i*120;var p=Math.max(0,Math.min(1,(ts-t0)/dur)),e=1-Math.pow(1-p,3);
       el.textContent=Math.round(to*e)+suf;if(p<1&&cur===14)requestAnimationFrame(step);}
     requestAnimationFrame(step);
   });
 }},
 s23:{enter:function(){
   var c=document.getElementById('closer'),a=document.getElementById('cla'),b=document.getElementById('clb'),d=document.getElementById('clc');
   [c,a,b,d].forEach(function(e){e.classList.remove('on');});
   T(function(){c.classList.add('on');},6500);
   T(function(){a.classList.add('on');},8200);
   T(function(){b.classList.add('on');},13000);
   T(function(){d.classList.add('on');},17500);
 }}
};

/* ===== navegación ===== */
var cnt=document.getElementById('cnt'),stag=document.getElementById('stag'),xpf=document.getElementById('xpf'),
    notes=document.getElementById('notes'),secchip=document.getElementById('secchip');
function themeOf(s){return s.classList.contains('t-calm')?'calm':s.classList.contains('t-black')?'black':s.classList.contains('t-dark')?'dark':'casino';}
function go(n){
  n=Math.max(0,Math.min(N-1,n));
  if(n===cur)return;
  var old=slides[cur];
  if(old&&hooks[old.id]&&hooks[old.id].leave)hooks[old.id].leave();
  clearT();
  var s=slides[n];
  stage.classList.toggle('cut',s.hasAttribute('data-cut'));
  slides.forEach(function(x,i){x.classList.toggle('active',i===n);});
  cur=n;
  stage.className='stage'+(s.hasAttribute('data-cut')?' cut':'')+' st-'+themeOf(s);
  stag.textContent=s.getAttribute('data-sec');
  xpf.style.width=((n+1)/N*100)+'%';
  cnt.textContent=(n+1)+' / '+N;
  secchip.textContent=s.getAttribute('data-sec');
  notes.innerHTML=s.getAttribute('data-note')||'';
  try{history.replaceState(null,'','#'+(n+1));}catch(e){}
  if(hooks[s.id]&&hooks[s.id].enter)hooks[s.id].enter();
}
function next(){go(cur+1);}
function prev(){go(cur-1);}

document.getElementById('bNext').addEventListener('click',next);
document.getElementById('bPrev').addEventListener('click',prev);
Array.prototype.forEach.call(document.querySelectorAll('[data-next]'),function(b){b.addEventListener('click',next);});
document.getElementById('noOpen').addEventListener('click',function(e){var b=e.currentTarget;b.classList.remove('pulse');b.style.animation='shake .12s 4';setTimeout(function(){b.style.animation='';b.classList.add('pulse');},600);});

var bSnd=document.getElementById('bSnd');
function toggleSound(){audioOn=!audioOn;bSnd.textContent='Sonido: '+(audioOn?'sí':'no');bSnd.setAttribute('aria-pressed',audioOn);if(audioOn)sfx.coin();}
bSnd.addEventListener('click',toggleSound);
function toggleNotes(){notes.classList.toggle('on');}
document.getElementById('bNotes').addEventListener('click',toggleNotes);
function fs(){var d=document.documentElement;try{if(document.fullscreenElement)document.exitFullscreen();else if(d.requestFullscreen)d.requestFullscreen();}catch(e){}}
document.getElementById('bFs').addEventListener('click',fs);

document.addEventListener('keydown',function(e){
  var k=e.key;
  if(e.target&&e.target.tagName==='BUTTON'&&(k==='Enter'||k===' '))return;
  if(k==='ArrowRight'||k==='PageDown'||k===' '){e.preventDefault();next();}
  else if(k==='ArrowLeft'||k==='PageUp'){e.preventDefault();prev();}
  else if(k==='Home'){go(0);}
  else if(k==='End'){go(N-1);}
  else if(k==='f'||k==='F'){fs();}
  else if(k==='n'||k==='N'){toggleNotes();}
  else if(k==='s'||k==='S'){toggleSound();}
});
var sx=0,sy=0;
vp.addEventListener('pointerdown',function(e){sx=e.clientX;sy=e.clientY;});
vp.addEventListener('pointerup',function(e){var dx=e.clientX-sx,dy=e.clientY-sy;if(Math.abs(dx)>70&&Math.abs(dx)>Math.abs(dy)*1.5){if(dx<0)next();else prev();}});

/* ===== escala del escenario ===== */
function fit(){var r=vp.getBoundingClientRect(),s=Math.min(r.width/1920,r.height/1080);stage.style.setProperty('--s',s);}
window.addEventListener('resize',fit);
if(window.ResizeObserver)new ResizeObserver(fit).observe(vp);
fit();

var start=parseInt((location.hash||'').slice(1),10);
go(isNaN(start)?0:start-1);
})();
</script>
</body>
</html>
