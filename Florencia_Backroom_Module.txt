/* =========================================================
   FLORENCIA BACKROOM MODULE
   ไฟล์นี้ไม่ใช่หน้าเว็บแยก และไม่มีลิงก์เปิดโดยตรง
   วางไฟล์นี้ไว้โฟลเดอร์เดียวกับ Florenzia_Front_Page.html
========================================================= */

(() => {
  "use strict";

  if (document.getElementById("back-page")) return;

  const backroomCSS = `
/* =========================================================
   CURRENT COMPLICATIONS — GLOWING CIRCLES
   เปลี่ยนเฉพาะส่วน Current Complications
========================================================= */
#back-page .tension-section{
  position:relative;
  z-index:2;
  width:min(1120px,calc(100% - 44px));
  margin:0 auto;
  padding:72px 0 96px;
}

#back-page .tension-title{
  margin:0 0 30px;
  color:#f0ddc3;
  font:500 clamp(28px,5vw,48px)/1.1 "Cinzel",serif;
  text-align:center;
  letter-spacing:.04em;
}

/* Legend ด้านบน */
#back-page .status-legend{
  display:flex;
  flex-wrap:wrap;
  justify-content:center;
  align-items:center;
  width:fit-content;
  max-width:100%;
  margin:0 auto 42px;
  padding:12px 18px;
  gap:18px;
  border:1px solid rgba(221,201,143,.17);
  background:rgba(15,10,6,.34);
  color:rgba(234,220,197,.5);
  font-size:13px;
}

#back-page .legend-item{
  display:flex;
  align-items:center;
  gap:8px;
}

/* จุดใน Legend ให้เข้ากับวงกลมของรายการ */
#back-page .dot{
  position:relative;
  width:9px;
  height:9px;
  flex:0 0 9px;
  border:1px solid currentColor;
  border-radius:50%;
  background:currentColor;
  box-shadow:0 0 7px currentColor;
}

#back-page .dot.critical{
  color:#c87687;
  background:currentColor;
}

#back-page .dot.warning{
  color:#d1ae63;
  background:currentColor;
}

#back-page .dot.stable{
  color:#91a284;
  background:currentColor;
}

/* รายการแต่ละชิ้น */
#back-page .tension-item{
  position:relative;
  display:grid;
  grid-template-columns:46px minmax(0,1fr);
  gap:20px;
  align-items:start;
  margin:0;
  padding:28px 4px 31px;
  border-bottom:1px solid rgba(221,201,143,.11);
  background:transparent;
  transition:
    background .35s ease,
    padding-left .35s cubic-bezier(.22,1,.36,1);
}

#back-page .tension-item:first-of-type{
  border-top:1px solid rgba(221,201,143,.08);
}

#back-page .tension-item:hover{
  padding-left:8px;
  background:
    linear-gradient(
      90deg,
      rgba(169,104,117,.035),
      transparent 46%
    );
}

#back-page .tension-content{
  min-width:0;
}

/* ชื่อสินค้า — สถานะ */
#back-page .tension-heading{
  display:flex;
  flex-wrap:wrap;
  align-items:baseline;
  gap:7px;
  margin:0;
  font-family:"Cinzel",serif;
  line-height:1.4;
}

#back-page .tension-product{
  color:#ead8bd;
  font-size:16px;
  font-weight:500;
  letter-spacing:.035em;
  text-transform:uppercase;
}

#back-page .tension-dash{
  color:rgba(221,201,143,.38);
  font-size:14px;
}

#back-page .tension-status{
  font-size:12px;
  font-weight:500;
  letter-spacing:.09em;
  text-transform:uppercase;
}

/* เส้นใต้หัวข้อ */
#back-page .tension-rule{
  width:min(470px,76%);
  height:1px;
  margin:10px 0 13px;
  background:
    linear-gradient(
      90deg,
      rgba(221,201,143,.32),
      rgba(221,201,143,.10) 66%,
      transparent
    );
}

/* คำอธิบาย */
#back-page .tension-text{
  max-width:970px;
  margin:0;
  color:rgba(234,220,197,.59);
  font-size:16px;
  line-height:1.75;
}

/* =========================================================
   วงกลมสถานะ — วาดด้วย CSS
========================================================= */

#back-page .tension-orb{
  --orb-color:#d1ae63;
  position:relative;
  display:block;
  width:30px;
  height:30px;
  margin:1px auto 0;
  flex:none;
  border:1px solid var(--orb-color);
  border-radius:50%;

  background:
    radial-gradient(
      circle,
      var(--orb-color) 0 2px,
      transparent 2.5px 7px,
      color-mix(in srgb,var(--orb-color) 72%,transparent) 7.5px 8px,
      transparent 8.5px 100%
    );

  box-shadow:
    0 0 5px var(--orb-color),
    0 0 13px color-mix(in srgb,var(--orb-color) 55%,transparent),
    0 0 25px color-mix(in srgb,var(--orb-color) 20%,transparent),
    inset 0 0 8px color-mix(in srgb,var(--orb-color) 24%,transparent);

  opacity:.88;
  transition:
    transform .4s cubic-bezier(.22,1,.36,1),
    opacity .35s ease,
    filter .35s ease,
    box-shadow .35s ease;
}

/* วงแหวนชั้นใน */
#back-page .tension-orb::before{
  content:"";
  position:absolute;
  inset:5px;
  border:1px solid color-mix(in srgb,var(--orb-color) 60%,transparent);
  border-radius:50%;
}

/* จุดเรืองแสงตรงกลาง */
#back-page .tension-orb::after{
  content:"";
  position:absolute;
  left:50%;
  top:50%;
  width:4px;
  height:4px;
  border-radius:50%;
  background:var(--orb-color);
  transform:translate(-50%,-50%);
  box-shadow:
    0 0 6px var(--orb-color),
    0 0 12px var(--orb-color);
}

/* สีตามสถานะ */
#back-page .tension-critical{
  --status-color:#c87687;
}

#back-page .tension-warning{
  --status-color:#d1ae63;
}

#back-page .tension-stable{
  --status-color:#91a284;
}

#back-page .tension-critical .tension-orb,#back-page .tension-warning .tension-orb,#back-page .tension-stable .tension-orb{
  --orb-color:var(--status-color);
}

#back-page .tension-critical .tension-status,#back-page .tension-warning .tension-status,#back-page .tension-stable .tension-status{
  color:var(--status-color);
}

/* Hover แล้ววงกลมตื่นขึ้น แต่ยังคงขนาดเดิมโดยรวม */
#back-page .tension-item:hover .tension-orb{
  opacity:1;
  filter:brightness(1.22);
  transform:scale(1.07);
  box-shadow:
    0 0 7px var(--orb-color),
    0 0 17px color-mix(in srgb,var(--orb-color) 68%,transparent),
    0 0 31px color-mix(in srgb,var(--orb-color) 27%,transparent),
    inset 0 0 10px color-mix(in srgb,var(--orb-color) 30%,transparent);
}

/* หายใจเบา ๆ เหมือนวงเวท ไม่กะพริบแบบหลอดไฟ */
#back-page .tension-orb{
  animation:tensionOrbBreath 3.8s ease-in-out infinite;
}

#back-page .tension-item:nth-of-type(2n) .tension-orb{
  animation-delay:-1.9s;
}

@media (max-width:700px){
  #back-page .tension-section{
    width:calc(100% - 28px);
    padding:50px 0 70px;
  }

  #back-page .status-legend{
    width:100%;
    padding:12px 14px;
    gap:12px 16px;
    font-size:12px;
  }

  #back-page .tension-item{
    grid-template-columns:32px minmax(0,1fr);
    gap:14px;
    padding:24px 0 27px;
  }

  #back-page .tension-item:hover{
    padding-left:0;
  }

  #back-page .tension-orb{
    width:24px;
    height:24px;
  }

  #back-page .tension-orb::before{
    inset:4px;
  }

  #back-page .tension-product{
    font-size:14px;
  }

  #back-page .tension-status{
    font-size:10px;
  }

  #back-page .tension-rule{
    width:90%;
  }

  #back-page .tension-text{
    font-size:15px;
  }
}

@media (prefers-reduced-motion:reduce){
  #back-page .tension-orb{
    animation:none!important;
  }

  #back-page .tension-item,#back-page .tension-orb{
    transition:none!important;
  }
}

#back-page{min-height:100vh;transition:opacity 0.8s ease,transform 0.8s ease}
#back-page{display:none;opacity:0;background:var(--night);color:#c8b896}
#back-page.visible{display:block;opacity:1}

.back-hero{min-height:100vh;background:var(--night);background-image:radial-gradient(circle at 50% 18%,rgba(168,97,112,0.14),transparent 32%),radial-gradient(ellipse 30% 40% at 85% 85%,rgba(185,151,42,0.08) 0%,transparent 55%);display:flex;flex-direction:column;align-items:center;justify-content:center;padding:120px 40px 60px;position:relative;overflow:hidden}
.back-hero::before{content:none}
.seal-clock{position:relative;z-index:1;width:74px;aspect-ratio:1;display:grid;place-items:center;border-radius:50%;color:var(--soft-gold);font:600 1.05rem "Cinzel",serif;margin-bottom:22px;background:radial-gradient(circle,#5b363d 0 42%,#a76c76 43% 48%,#4c2a2f 49% 55%,#211713 56% 100%);box-shadow:0 0 0 4px #8b5761,0 0 0 7px rgba(214,191,134,.4),0 8px 24px rgba(0,0,0,.5)}
.seal-clock::before,.seal-clock::after{content:"";position:absolute;width:2px;height:22px;background:var(--soft-gold);transform-origin:bottom center;bottom:50%;left:calc(50% - 1px)}
.seal-clock::before{transform:rotate(42deg)}
.seal-clock::after{height:17px;transform:rotate(104deg)}
.back-eyebrow{position:relative;z-index:1;font-family:"Cinzel",serif;font-size:10px;letter-spacing:0.35em;text-transform:uppercase;color:var(--old-gold);margin-bottom:20px;font-weight:500}
.back-title{position:relative;z-index:1;font-family:"Cinzel",serif;font-size:clamp(38px,7.5vw,66px);font-weight:500;letter-spacing:0.05em;color:#c8b896;text-align:center;line-height:1.15;margin-bottom:8px;text-shadow:0 2px 0 #000}
.back-title em{color:var(--rose-pale);font-style:italic}
.back-subtitle{position:relative;z-index:1;font-family:"Cormorant Garamond",serif;font-style:italic;font-size:16px;color:rgba(200,184,150,0.5);margin-top:16px;margin-bottom:48px;text-align:center;letter-spacing:0.05em}
.warning-strip{position:relative;z-index:1;border:1px solid rgba(168,97,112,0.4);box-shadow:inset 0 0 0 3px rgba(20,12,5,.4),inset 0 0 0 4px rgba(214,191,134,.12);padding:12px 24px;font-family:"Cinzel",serif;font-size:11px;letter-spacing:0.15em;text-transform:uppercase;color:var(--rose-pale);margin-bottom:60px;background:rgba(107,26,26,0.12)}
.extracts-section{padding:80px 80px;background:var(--night-surface)}
.extracts-inner{width:min(100%,1280px);margin:0 auto}
.extract-table-header,.extract-row{display:grid;grid-template-columns:1.45fr .75fr 1.25fr .75fr;gap:48px}
.extract-table-header{padding:0 0 12px;border-bottom:1px solid rgba(184,151,42,0.2);font-size:10px;letter-spacing:0.25em;text-transform:uppercase;color:rgba(184,151,42,0.6);margin-bottom:4px}
.extract-row{position:relative;padding:22px 20px 22px 34px;margin-bottom:10px;align-items:start;transition:background 0.2s,box-shadow 0.2s;border:1px solid rgba(214,191,134,0.16);background:rgba(255,255,255,0.012);box-shadow:inset 0 0 0 1px rgba(0,0,0,0.2)}
.extract-row::before{content:"";position:absolute;top:0;bottom:0;left:0;width:6px;background:linear-gradient(#9f5d69,#6e3945)}
.extracts-ribbon{position:relative;display:flex;align-items:center;gap:16px;min-height:68px;margin:0 0 28px;padding:13px 20px 13px 80px;border:1px solid rgba(214,191,134,0.45);background:linear-gradient(90deg,rgba(168,97,112,.92),rgba(110,57,69,.88)),repeating-linear-gradient(45deg,rgba(255,255,255,.08) 0 12px,transparent 12px 24px);box-shadow:0 10px 26px rgba(0,0,0,.4),inset 0 0 0 2px rgba(255,255,255,.05)}
.extracts-ribbon .rose-cluster{position:absolute;left:16px;width:46px;aspect-ratio:1;display:grid;place-items:center;border-radius:50%;color:#f0c2ca;background:radial-gradient(circle,#b87482,#543038 68%);box-shadow:0 0 0 4px rgba(214,191,134,.22);font-size:1.5rem}
.extracts-ribbon h2{margin:0;font-family:"Cinzel",serif;font-weight:500;font-size:clamp(1.4rem,4vw,1.9rem);letter-spacing:0.03em;color:#fff3e2}
.circle-note{max-width:760px;margin:-10px 0 34px;padding:18px 24px;background:rgba(184,151,42,.03);border-left:1px solid rgba(184,151,42,.35)}
.circle-note p{margin:0 0 12px;font-family:"Cormorant Garamond",serif;font-size:15px;line-height:1.8;color:rgba(220,210,188,.75)}
.circle-note strong{color:#d2bb73;letter-spacing:.08em}
.circle-small{margin-top:18px!important;font-style:italic;opacity:.65}
@media (max-width:768px){.extracts-section{padding:48px 0}
.extracts-inner{width:100%;max-width:100%;margin:0 auto;padding:0 20px}
.circle-note{max-width:100%;margin:18px 0 28px;padding:16px}
.extract-table-header,.extract-row{grid-template-columns:1fr 1fr;gap:12px}
}
.extract-row>div{margin-bottom:12px}
.extract-row>div:last-child{margin-bottom:0}
.ext-name{font-size:22px}
.ext-source,.ext-effect{font-size:13px}
.ext-effect{line-height:1.7}
.ext-price{font-size:17px}
.extract-row:hover{background:rgba(168,97,112,0.05);box-shadow:inset 0 0 0 1px rgba(214,191,134,0.28)}
.ext-name{font-family:"IM Fell English",serif;font-size:18px;color:#c8b896;margin-bottom:4px}
.ext-source{font-size:12px;font-style:italic;color:rgba(200,184,150,0.4);font-family:"Cormorant Garamond",serif}
.ext-effect{font-size:13px;line-height:1.55;color:rgba(200,184,150,0.6)}
.ext-grade{display:inline-block;font-family:"Cinzel",serif;font-size:10px;letter-spacing:0.12em;text-transform:uppercase;padding:4px 12px;border-radius:999px;font-weight:600;box-shadow:inset 0 1px 0 rgba(255,255,255,.12)}
.grade-i{background:rgba(45,90,27,0.3);color:var(--poison-glow);border:1px solid rgba(74,140,42,0.3)}
.grade-ii{background:rgba(107,26,26,0.3);color:#e07070;border:1px solid rgba(160,40,40,0.3)}
.grade-iii{background:rgba(120,80,10,0.3);color:#d4a44a;border:1px solid rgba(180,100,15,0.3)}
.ext-price{font-family:"Cormorant Garamond",serif;font-size:15px;color:var(--gold-light);margin-top:4px}
.status-legend{display:flex;flex-wrap:wrap;gap:24px;margin:18px 0 38px;padding:12px 18px;width:fit-content;border:1px solid rgba(204,164,82,.22);background:rgba(15,10,6,.38);color:#b59664;font-size:.88rem}
.legend-item{display:flex;align-items:center;gap:9px}

.ledger-section{padding:60px;background:var(--night-card);display:grid;grid-template-columns:1fr 1fr;gap:40px}
.ledger-block{border-left:2px solid rgba(214,191,134,0.3);padding:0 0 0 20px}
.ledger-block.red-ledger{border-left-color:rgba(168,97,112,0.4)}
.ledger-title{font-family:"Cinzel",serif;font-weight:500;font-size:18px;letter-spacing:0.03em;color:#c8b896;margin-bottom:12px}
.ledger-body{font-size:14px;line-height:1.8;color:rgba(200,184,150,0.55)}
.ledger-body strong{color:rgba(200,184,150,0.85);font-weight:400}
.ledger-body em{color:var(--poison-bright);font-style:italic}
.tension-section{padding:60px;background:var(--void)}
.tension-title{font-family:"Cinzel",serif;font-weight:500;letter-spacing:0.03em;font-size:24px;color:#c8b896;margin-bottom:32px}
.tension-item{display:flex;gap:20px;margin-bottom:24px;align-items:flex-start}
.tension-marker{width:8px;height:8px;border-radius:50%;flex-shrink:0;margin-top:6px}
.t-red{background:var(--blood-bright);box-shadow:0 0 8px rgba(160,40,40,0.5)}
.t-amber{background:var(--gold);box-shadow:0 0 8px rgba(184,151,42,0.4)}
.t-green{background:#6f8b58;box-shadow:0 0 8px rgba(111,139,88,.75)}
.tension-name{font-family:"Cormorant Garamond",serif;font-size:16px;font-weight:500;color:#c8b896;margin-bottom:4px}
.tension-text{font-size:13px;line-height:1.65;color:rgba(200,184,150,0.5)}
.footer-back{padding:32px 60px;background:var(--night);display:flex;justify-content:space-between;align-items:center;border-top:1px solid rgba(184,151,42,0.1)}
.footer-back-text{font-family:"Cormorant Garamond",serif;font-style:italic;font-size:13px;color:rgba(200,184,150,0.3)}
.back-btn{background:none;border:1px solid rgba(184,151,42,0.25);cursor:pointer;font-family:"Crimson Pro",serif;font-size:12px;letter-spacing:0.18em;text-transform:uppercase;color:rgba(184,151,42,0.6);padding:8px 20px;transition:all 0.3s}
.back-btn:hover{color:var(--gold-light);border-color:rgba(184,151,42,0.6);background:rgba(184,151,42,0.05)}

@media (max-width:700px){.ledger-section{grid-template-columns:1fr}
.extracts-section,.ledger-section,.tension-section{padding:48px 28px}
.back-hero{padding:60px 24px 40px}
.extract-table-header,.extract-row{grid-template-columns:1fr 1fr}
.footer-back{flex-direction:column;gap:12px;text-align:center}
}
#back-page{--br-ink:#eadcc5;--br-muted:rgba(234,220,197,.66);--br-faint:rgba(234,220,197,.42);--br-black:#0d0708;--br-deep:#170b0d;--br-card:#211213;--br-burgundy:#6f3040;--br-burgundy-deep:#35151e;--br-rose:#a96875;--br-dusty:#c88b98;--br-pale:#e2b1b9;--br-gold:#b99a5b;--br-gold-light:#ddc98f;--br-line:rgba(221,201,143,.2);position:fixed;inset:0;z-index:9999;display:none;width:100%;height:100vh;overflow-y:auto;overflow-x:hidden;isolation:isolate;opacity:0;color:var(--br-ink);background:radial-gradient(ellipse at 50% -8%,rgba(168,97,112,.2),transparent 34%),radial-gradient(ellipse at 8% 35%,rgba(89,35,49,.18),transparent 30%),radial-gradient(ellipse at 92% 78%,rgba(185,154,91,.07),transparent 28%),linear-gradient(180deg,#0d0708 0%,#170b0d 42%,#110809 100%);font-family:"Cormorant Garamond",Georgia,serif;transition:opacity .7s ease}
#back-page.visible{display:block;opacity:1}
#back-page::before{content:"";position:fixed;inset:0;z-index:-2;pointer-events:none;opacity:.34;background:radial-gradient(circle at center,transparent 42%,rgba(0,0,0,.58) 100%)}
#back-page .back-hero{position:relative;z-index:2;width:min(1180px,calc(100% - 44px));min-height:clamp(620px,88vh,900px);margin:22px auto 0;padding:90px 40px 70px;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;border:1px solid rgba(221,201,143,.2);background:linear-gradient(90deg,transparent,rgba(90,38,51,.08),transparent),radial-gradient(circle at 50% 35%,rgba(200,139,152,.07),transparent 42%);box-shadow:inset 0 0 0 5px rgba(16,9,8,.72),inset 0 0 0 6px rgba(221,201,143,.055),0 24px 70px rgba(0,0,0,.32);overflow:hidden}
#back-page .back-hero::before{
  content:"Ah... it would seem thou hast found thy way unto the chamber that lieth behind my little florist's.";
  position:absolute;
  top:20px;
  left:50%;
  width:min(900px,calc(100% - 70px));
  padding-bottom:16px;
  border-bottom:1px solid rgba(221,201,143,.16);
  color:rgba(221,201,143,.62);
  font:italic 18px/1.55 "Cormorant Garamond",serif;
  letter-spacing:.06em;
  word-spacing:.04em;
  text-align:center;
  transform:translateX(-50%);
}
#back-page .seal-clock{position:relative;z-index:2;width:84px;aspect-ratio:1;display:grid;place-items:center;margin-bottom:28px;border-radius:50%;color:var(--br-gold-light);font:600 1rem "Cinzel",serif;background:radial-gradient(circle,#6d3542 0 34%,#351820 35% 47%,#a96875 48% 51%,#251015 52% 100%);border:1px solid rgba(221,201,143,.45);box-shadow:0 0 0 4px rgba(169,104,117,.16),0 0 0 7px rgba(221,201,143,.12),0 14px 34px rgba(0,0,0,.45)}
#back-page .seal-clock::before,#back-page .seal-clock::after{content:"";position:absolute;left:50%;bottom:50%;width:2px;background:var(--br-gold-light);transform-origin:50% 100%}
#back-page .seal-clock::before{height:24px;transform:translateX(-50%) rotate(38deg)}
#back-page .seal-clock::after{height:17px;transform:translateX(-50%) rotate(112deg)}
#back-page .back-eyebrow{position:relative;z-index:2;margin-bottom:18px;color:var(--br-gold);font:500 10px "Cinzel",serif;letter-spacing:.32em;text-transform:uppercase}
#back-page .back-title{position:relative;z-index:2;margin:0;color:#f0dfc5;font:500 clamp(42px,7vw,86px)/.98 "Cinzel",serif;letter-spacing:.06em;text-shadow:0 3px 0 #080405,0 12px 34px rgba(0,0,0,.55)}
#back-page .back-title em{color:var(--br-pale);font:500 1.12em "Cormorant Garamond",serif;font-style:italic;letter-spacing:.01em}
#back-page .back-subtitle{position:relative;z-index:2;max-width:680px;margin:22px auto 0;color:var(--br-faint);font-size:18px;font-style:italic;line-height:1.6;letter-spacing:.04em}
#back-page .warning-strip{position:relative;z-index:2;max-width:900px;margin:34px auto 0;padding:15px 22px;border:1px solid rgba(200,139,152,.45);background:linear-gradient(90deg,rgba(90,38,51,.12),rgba(169,104,117,.13),rgba(90,38,51,.12));color:var(--br-pale);font:500 10px/1.7 "Cinzel",serif;letter-spacing:.16em;text-transform:uppercase;box-shadow:inset 0 0 0 2px rgba(221,201,143,.055),0 10px 30px rgba(0,0,0,.18)}
#back-page .extracts-inner{position:relative;z-index:2;width:min(1120px,calc(100% - 44px));margin:0 auto;padding:78px 0 96px}
#back-page .extracts-ribbon{position:relative;display:flex;align-items:center;min-height:82px;margin:0 0 34px;padding:14px 32px 14px 94px;border:1px solid rgba(221,201,143,.42);background:linear-gradient(90deg,rgba(111,48,63,.96),rgba(73,28,40,.96) 72%,rgba(53,21,30,.96));box-shadow:0 18px 38px rgba(0,0,0,.36),inset 0 0 0 2px rgba(255,255,255,.025)}
#back-page .extracts-ribbon::before,#back-page .extracts-ribbon::after{content:"";position:absolute;bottom:-9px;width:18px;height:18px;background:var(--br-burgundy-deep);border-bottom:1px solid rgba(221,201,143,.24)}
#back-page .extracts-ribbon::before{left:-1px;transform:skewY(28deg)}
#back-page .extracts-ribbon::after{right:-1px;transform:skewY(-28deg)}
#back-page .rose-cluster{position:absolute;left:22px;width:52px;height:52px;display:grid;place-items:center;border-radius:50%;color:#f2c9d0;background:radial-gradient(circle,#c88b98 0 28%,#75404d 29% 57%,#3d1d27 58% 100%);border:1px solid rgba(221,201,143,.56);box-shadow:0 0 0 4px rgba(221,201,143,.08),0 8px 18px rgba(0,0,0,.25);font-size:24px}
#back-page .extracts-ribbon h2{margin:0;color:#fff0dc;font:500 clamp(22px,4vw,34px) "Cinzel",serif;letter-spacing:.04em}
#back-page .circle-note{max-width:920px;margin:0 auto 42px;padding:24px 28px;border-left:2px solid var(--br-gold);border-top:1px solid rgba(221,201,143,.1);border-bottom:1px solid rgba(221,201,143,.08);background:linear-gradient(90deg,rgba(185,154,91,.055),transparent 70%)}
#back-page .circle-note p{margin:0 0 12px;color:var(--br-muted);font-size:16px;line-height:1.8}
#back-page .circle-note p:last-child{margin-bottom:0}
#back-page .circle-note strong{color:var(--br-gold-light);font:500 13px "Cinzel",serif;letter-spacing:.09em}
#back-page .circle-small{margin-top:18px!important;color:rgba(234,220,197,.42)!important;font-style:italic}
#back-page .extract-table-header,#back-page .extract-row{display:grid;grid-template-columns:1.4fr .7fr 1.5fr .65fr;gap:30px}
#back-page .extract-table-header{padding:0 20px 12px;border-bottom:1px solid var(--br-line);color:rgba(221,201,143,.62);font:500 10px "Cinzel",serif;letter-spacing:.2em;text-transform:uppercase}
#back-page .extract-row{position:relative;align-items:start;margin-top:10px;padding:25px 24px 25px 34px;border:1px solid rgba(221,201,143,.14);background:linear-gradient(135deg,rgba(255,255,255,.022),rgba(169,104,117,.025));box-shadow:inset 0 0 0 1px rgba(0,0,0,.2);transition:transform .25s ease,border-color .25s ease,background .25s ease,box-shadow .25s ease}
#back-page .extract-row::before{content:"";position:absolute;inset:0 auto 0 0;width:5px;background:linear-gradient(180deg,var(--br-dusty),var(--br-burgundy))}
#back-page .extract-row:hover{transform:translateX(4px);border-color:rgba(221,201,143,.3);background:rgba(169,104,117,.055);box-shadow:0 12px 28px rgba(0,0,0,.25)}
#back-page .ext-name{margin:0;color:#f0ddc3;font:600 26px/1.15 "Cormorant Garamond",serif}
#back-page .ext-source{margin:6px 0 0;color:rgba(234,220,197,.42);font-size:13px;font-style:italic;line-height:1.5}
#back-page .ext-effect{margin:0;color:rgba(234,220,197,.67);font-size:15px;line-height:1.75}
#back-page .ext-price{margin:0;color:var(--br-gold-light);font:500 16px/1.4 "Cinzel",serif;white-space:nowrap}
#back-page .ext-grade{display:inline-flex;align-items:center;justify-content:center;min-width:82px;padding:7px 10px;border-radius:2px;font:500 10px "Cinzel",serif;letter-spacing:.06em;box-shadow:inset 0 0 0 1px rgba(255,255,255,.06)}
#back-page .grade-i{color:#f4e6c7;background:linear-gradient(135deg,#9b6872,#68404a)}
#back-page .grade-ii{color:#f1d5da;background:linear-gradient(135deg,#78424e,#4a2931)}
#back-page .grade-iii{color:#e6cf9b;background:linear-gradient(135deg,#5c4a30,#2d2419);border:1px solid rgba(221,201,143,.35)}
#back-page .ledger-section{position:relative;z-index:2;width:min(1120px,calc(100% - 44px));margin:0 auto;padding:70px 0;display:grid;grid-template-columns:1fr 1fr;gap:22px}
#back-page .ledger-block{position:relative;padding:34px;border:1px solid rgba(221,201,143,.2);background:linear-gradient(145deg,rgba(255,255,255,.022),rgba(169,104,117,.035));box-shadow:0 16px 34px rgba(0,0,0,.24)}
#back-page .ledger-block::before{content:"";position:absolute;top:0;left:0;right:0;height:2px;background:linear-gradient(90deg,var(--br-gold),transparent);opacity:.65}
#back-page .ledger-block.red-ledger::before{background:linear-gradient(90deg,var(--br-rose),transparent)}
#back-page .ledger-title{margin:0 0 18px;color:var(--br-gold-light);font:500 22px/1.2 "Cinzel",serif;letter-spacing:.04em}
#back-page .ledger-body{margin:0;color:rgba(234,220,197,.65);font-size:16px;line-height:1.8}
#back-page .ledger-body strong{color:var(--br-pale)}
#back-page .ledger-body em{color:#c88b98}
#back-page .tension-section{position:relative;z-index:2;width:min(1120px,calc(100% - 44px));margin:0 auto;padding:72px 0 96px}
#back-page .tension-title{margin:0 0 30px;color:#f0ddc3;font:500 clamp(28px,5vw,48px)/1.1 "Cinzel",serif;text-align:center;letter-spacing:.04em}
#back-page .status-legend{background:rgba(15,10,6,0.38)}
#back-page .status-legend{display:flex;flex-wrap:wrap;justify-content:center;align-items:center;width:fit-content;margin:0 auto 40px;gap:18px;color:rgba(234,220,197,.5);font-size:13px;background:rgba(15,10,6,.38);}
#back-page .legend-item{display:flex;align-items:center;gap:8px}
#back-page .dot{width:8px;height:8px;border-radius:50%;box-shadow:0 0 10px currentColor}
#back-page .dot.critical{color:#a85c68;background:#a85c68}
#back-page .dot.warning{color:#b99a5b;background:#b99a5b}
#back-page .dot.stable{color:#71816a;background:#71816a}
#back-page .tension-item{display:grid;grid-template-columns:6px 1fr;gap:22px;padding:24px 0;border-bottom:1px solid rgba(221,201,143,.11)}
#back-page .tension-marker{
  width:5px;
  height:54px;
  min-height:54px;
  align-self:center;
  border-radius:999px;
  box-shadow:0 0 8px currentColor;
}
#back-page .t-red{background:#9d5965}
.t-amber{background:#b99a5b}
.t-green{background:#71816a}
#back-page .tension-name{margin:0 0 6px;color:var(--br-pale);font:500 15px/1.4 "Cinzel",serif;letter-spacing:.04em}
#back-page .tension-text{margin:0;color:rgba(234,220,197,.58);font-size:16px;line-height:1.75}
#back-page .footer-back{position:relative;z-index:2;padding:70px 20px 100px;text-align:center;border-top:1px solid rgba(221,201,143,.16)}
#back-page .footer-back-text{margin:0 0 24px;color:rgba(234,220,197,.38);font-size:15px;font-style:italic}
#back-page .back-btn{padding:12px 24px;border:1px solid rgba(221,201,143,.38);border-radius:999px;background:rgba(20,10,11,.75);color:var(--br-gold-light);font:500 11px "Cinzel",serif;letter-spacing:.08em;cursor:pointer;transition:background .25s ease,color .25s ease,border-color .25s ease,transform .25s ease}
#back-page .back-btn:hover{transform:translateY(-2px);background:var(--br-burgundy);color:#fff1dc;border-color:var(--br-pale)}
@media (max-width:900px){#back-page .extract-table-header{display:none}
#back-page .extract-row{grid-template-columns:1fr 1fr;gap:16px 20px}
#back-page .extract-row>div:first-child{grid-column:1/-1}
#back-page .extract-row>div:nth-child(2){align-self:center}
#back-page .ext-price{white-space:normal}
#back-page .ledger-section{grid-template-columns:1fr}
}
@media (max-width:700px){

.ledger-section,.tension-section{padding:48px 28px}


#back-page .back-hero{width:calc(100% - 24px);margin:12px auto 0;min-height:640px;padding:76px 18px 62px}
#back-page .back-title{font-size:clamp(34px,11vw,58px)}
#back-page .back-subtitle{font-size:16px;max-width:92%}
#back-page .warning-strip{max-width:94%;padding:12px 15px;font-size:8px;letter-spacing:.12em}
#back-page .extracts-inner,#back-page .ledger-section,#back-page .tension-section{width:calc(100% - 28px)}
#back-page .extracts-inner{padding:52px 0 70px}
#back-page .extracts-ribbon{min-height:70px;padding:12px 18px 12px 78px}
#back-page .rose-cluster{left:16px;width:44px;height:44px;font-size:20px}
#back-page .extracts-ribbon h2{font-size:21px}
#back-page .circle-note{padding:18px 18px 18px 20px}
#back-page .extract-row{grid-template-columns:1fr;gap:14px;padding:22px 18px 22px 26px}
#back-page .extract-row>div:first-child{grid-column:auto}
#back-page .ext-name{font-size:23px}
#back-page .ledger-section{padding:50px 0}
#back-page .ledger-block{padding:25px}
#back-page .tension-section{padding:50px 0 70px}
}
@media (max-width:480px){#back-page .seal-clock{width:72px}
#back-page .back-title{font-size:34px}
#back-page .back-subtitle{font-size:15px}
#back-page .warning-strip{font-size:8px;line-height:1.8}
#back-page .ledger-title{font-size:19px}
#back-page .ledger-body,#back-page .tension-text{font-size:15px}
}

#back-page .extracts-section,#back-page .extracts-inner,#back-page .ledger-section,#back-page .tension-section,#back-page .footer-back{background:transparent !important}
#back-page .extracts-inner,#back-page .ledger-section,#back-page .tension-section{box-shadow:none !important;border:none !important}
#back-page .extract-row{background:linear-gradient(135deg,rgba(255,255,255,0.022),rgba(169,104,117,0.025))}
#back-page .ledger-block{background:linear-gradient(145deg,rgba(255,255,255,0.022),rgba(169,104,117,0.035))}
#back-page .tension-item{background:transparent}
#back-page .footer-back{box-shadow:none}
.seal-clock::before{animation:backroomMinuteHand 3600s linear infinite}
.seal-clock::after{animation:backroomHourHand 43200s linear infinite}


#back-page{background-size:115% 115%,110% 110%,112% 112%,100% 100%;animation:backroomBreath 18s ease-in-out infinite}

.backroom-dust-layer{position:fixed;inset:0;z-index:20;overflow:hidden;pointer-events:none}
.backroom-dust{position:absolute;bottom:-20px;width:var(--dust-size,3px);height:var(--dust-size,3px);border-radius:50%;background:rgba(221,201,143,.72);box-shadow:0 0 6px rgba(221,201,143,.35),0 0 12px rgba(200,139,152,.12);opacity:0;animation:backroomDustRise var(--dust-duration,18s) linear infinite,backroomDustFlicker 4s ease-in-out infinite;animation-delay:var(--dust-delay,0s)}


#back-page .back-hero{isolation:isolate}
#back-page .backroom-border-glint{position:absolute;inset:0;z-index:10;pointer-events:none;padding:1px;background:conic-gradient(from var(--glint-angle,0deg),transparent 0deg,transparent 310deg,rgba(221,201,143,.05) 330deg,rgba(255,235,180,.62) 344deg,rgba(221,201,143,.05) 354deg,transparent 360deg);-webkit-mask:linear-gradient(#000 0 0) content-box,linear-gradient(#000 0 0);-webkit-mask-composite:xor;mask-composite:exclude;animation:backroomBorderGlint 12s linear infinite}

.backroom-cursor-light{position:fixed;left:0;top:0;z-index:8;width:420px;height:420px;border-radius:50%;pointer-events:none;opacity:0;transform:translate3d(calc(var(--mouse-x,-500px) - 50%),calc(var(--mouse-y,-500px) - 50%),0);background:radial-gradient(circle,rgba(255,224,173,.07) 0%,rgba(200,139,152,.035) 28%,rgba(111,48,63,.014) 48%,transparent 72%);filter:blur(3px);transition:opacity .45s ease,transform .06s linear}
#back-page.visible .backroom-cursor-light{opacity:1}
#back-page .extract-row{overflow:hidden}
#back-page .extract-row::before{width:5px;transition:width .38s cubic-bezier(.22,1,.36,1),opacity .38s ease,filter .38s ease}
#back-page .extract-row:hover::before{width:13px;opacity:.95;filter:saturate(1.2) brightness(1.12);box-shadow:0 0 20px rgba(200,139,152,.18)}

#back-page.audio-awake .seal-clock{animation:backroomClockWake 1.8s ease}

#back-page .ext-name{letter-spacing:.01em;transition:letter-spacing .55s cubic-bezier(.22,1,.36,1),color .35s ease,text-shadow .35s ease}
#back-page .extract-row:hover .ext-name{letter-spacing:.065em;color:#f8e7ce;text-shadow:0 0 14px rgba(226,177,185,.08)}
.backroom-orbit{position:fixed;z-index:1;pointer-events:none;border-radius:50%;border:1px solid rgba(221,201,143,.09);opacity:.72}
.backroom-orbit::before,.backroom-orbit::after{content:"";position:absolute;border-radius:50%;border:1px solid rgba(200,139,152,.055)}
.backroom-orbit::before{inset:9%}
.backroom-orbit::after{inset:24%}
.backroom-orbit-one{width:760px;height:760px;left:-330px;top:52px;border-top-color:rgba(221,201,143,.22);border-right-color:transparent;animation:backroomOrbitClockwise 220s linear infinite}
.backroom-orbit-two{width:500px;height:500px;right:-270px;bottom:-170px;border-bottom-color:rgba(200,139,152,.14);border-left-color:transparent;animation:backroomOrbitCounter 280s linear infinite}


#back-page .grade-forbidden,#back-page .grade-restricted,#back-page .grade-occult,#back-page .grade-illicit{position:relative;overflow:hidden;color:#f1d8dc;border:1px solid rgba(200,139,152,.36);background:linear-gradient(135deg,rgba(111,48,63,.62),rgba(35,15,21,.86));transition:transform .32s ease,color .32s ease,border-color .32s ease,box-shadow .32s ease,filter .32s ease}
#back-page .grade-occult{color:#decda2;border-color:rgba(185,154,91,.38);background:linear-gradient(135deg,rgba(92,74,48,.78),rgba(25,18,12,.9))}
#back-page .grade-illicit{color:#f0c7ce;border-color:rgba(168,92,104,.48);background:linear-gradient(135deg,rgba(126,40,55,.82),rgba(40,12,18,.94))}
#back-page .grade-forbidden:hover,#back-page .grade-restricted:hover,#back-page .grade-occult:hover,#back-page .grade-illicit:hover{transform:translateY(-1px) scale(1.035);color:#fff1e4;border-color:rgba(244,214,177,.68);filter:brightness(1.18) saturate(1.08);box-shadow:0 0 10px rgba(200,139,152,.24),0 0 24px rgba(221,201,143,.11),inset 0 0 12px rgba(255,255,255,.04)}
@media (prefers-reduced-motion:reduce){#back-page,#back-page *,#back-page *::before,#back-page *::after{animation-duration:.001ms !important;animation-iteration-count:1 !important;scroll-behavior:auto !important}
.backroom-cursor-light,.backroom-dust-layer,.backroom-orbit{display:none !important}
}
@media (max-width:700px){.backroom-cursor-light{display:none}
.backroom-dust-layer{opacity:.55}
.backroom-orbit-one{width:520px;height:520px;left:-310px}
.backroom-orbit-two{width:360px;height:360px;right:-230px}
}
#back-page .back-title{display:block !important;visibility:visible !important;opacity:1 !important;transform:none !important;animation:backroomTitleReveal 0.8s ease both,backroomTitleFlicker 6s ease-in-out 0.8s infinite !important}

@media (hover:hover) and(pointer:fine){.back-btn{cursor:none !important}
}

#back-page .ledger-section{perspective:1200px;isolation:isolate}
#back-page .ledger-section.is-reading .ledger-block{opacity:.34;filter:brightness(.62) saturate(.72);transform:scale(.985)}
#back-page .ledger-section.is-reading .ledger-block.is-reading{z-index:6;opacity:1;filter:brightness(1.08) saturate(1);transform:translateY(-7px) scale(1.018);border-color:rgba(221,201,143,.42);box-shadow:0 28px 68px rgba(0,0,0,.52),0 0 44px rgba(185,154,91,.075),inset 0 0 0 1px rgba(255,255,255,.025)}
#back-page .ledger-block{overflow:hidden;transform-origin:center;transition:transform .5s cubic-bezier(.22,1,.36,1),opacity .45s ease,filter .45s ease,border-color .45s ease,box-shadow .45s ease;animation:ledgerLivingPaper 9s ease-in-out infinite}
#back-page .ledger-block:nth-child(2){animation-delay:-4.5s}

#back-page .ledger-candle{position:absolute;inset:0;z-index:0;pointer-events:none;opacity:0;background:radial-gradient(circle 190px at var(--ledger-x,50%) var(--ledger-y,50%),rgba(255,224,162,.15) 0%,rgba(221,201,143,.075) 28%,rgba(169,104,117,.025) 52%,transparent 74%);mix-blend-mode:screen;transition:opacity .4s ease}
#back-page .ledger-block.is-reading .ledger-candle{opacity:1}
#back-page .ledger-title,#back-page .ledger-body{position:relative;z-index:3}
#back-page .ledger-title::after{content:"";display:block;width:min(220px,72%);height:1px;margin-top:12px;background:linear-gradient(90deg,var(--br-gold-light),rgba(221,201,143,.35),transparent);transform:scaleX(0);transform-origin:left;opacity:0}
#back-page .red-ledger .ledger-title::after{background:linear-gradient(90deg,var(--br-pale),rgba(200,139,152,.34),transparent)}
#back-page .ledger-block.is-reading .ledger-title::after{animation:ledgerInkWrite .85s cubic-bezier(.22,1,.36,1) forwards}

#back-page .ledger-invisible-ink{position:absolute;right:25px;bottom:20px;z-index:1;max-width:48%;color:rgba(221,201,143,.04);font:italic 15px/1.45 "Cormorant Garamond",serif;letter-spacing:.07em;text-align:right;transform:rotate(-4deg) translateY(8px);opacity:0;filter:blur(1px);pointer-events:none;transition:opacity 1.1s ease .18s,color 1.1s ease .18s,transform 1.1s ease .18s,filter 1.1s ease .18s}
#back-page .red-ledger .ledger-invisible-ink{color:rgba(200,139,152,.04)}
#back-page .ledger-block.is-reading .ledger-invisible-ink{opacity:.62;color:rgba(221,201,143,.17);transform:rotate(-4deg) translateY(0);filter:blur(0)}
#back-page .red-ledger.is-reading .ledger-invisible-ink{color:rgba(226,177,185,.17)}
#back-page .ledger-page-curl{position:absolute;right:-1px;bottom:-1px;z-index:4;width:0;height:0;pointer-events:none;border-style:solid;border-width:0 0 0 0;border-color:transparent transparent rgba(221,201,143,.16) transparent;filter:drop-shadow(-4px -4px 7px rgba(0,0,0,.3));transition:border-width .55s cubic-bezier(.22,1,.36,1),filter .55s ease}
#back-page .ledger-block.is-reading .ledger-page-curl{border-width:0 0 52px 52px;filter:drop-shadow(-6px -5px 10px rgba(0,0,0,.42)) drop-shadow(-1px -1px 0 rgba(221,201,143,.12))}
#back-page .ledger-watermark{position:absolute;left:50%;top:54%;z-index:0;color:rgba(221,201,143,.022);font:130px/1 "Cormorant Garamond",serif;transform:translate(-50%,-50%) rotate(-8deg);pointer-events:none;transition:color 1s ease,transform 1s ease}
#back-page .red-ledger .ledger-watermark{color:rgba(200,139,152,.022)}
#back-page .ledger-block.is-reading .ledger-watermark{color:rgba(221,201,143,.055);transform:translate(-50%,-50%) rotate(-5deg) scale(1.04)}
#back-page .red-ledger.is-reading .ledger-watermark{color:rgba(200,139,152,.055)}
#back-page .ledger-dust{position:absolute;z-index:5;width:var(--ledger-dust-size,3px);height:var(--ledger-dust-size,3px);border-radius:50%;background:rgba(221,201,143,.72);box-shadow:0 0 7px rgba(221,201,143,.34);pointer-events:none;animation:ledgerDustRelease var(--ledger-dust-time,.9s) ease-out forwards}
#back-page .red-ledger .ledger-dust{background:rgba(226,177,185,.65);box-shadow:0 0 7px rgba(200,139,152,.28)}

#back-page .ledger-block::after{content:"";position:absolute;inset:-40% auto -40% -24%;z-index:2;width:16%;pointer-events:none;opacity:0;background:linear-gradient(90deg,transparent,rgba(255,235,190,.12),transparent);transform:skewX(-16deg)}
#back-page .ledger-block.is-reading::after{animation:ledgerEdgeShimmer 1.4s ease .18s 1}

@media (prefers-reduced-motion:reduce),(pointer:coarse){#back-page .ledger-block{animation:none}
#back-page .ledger-section.is-reading .ledger-block,#back-page .ledger-section.is-reading .ledger-block.is-reading{transform:none;opacity:1;filter:none}
#back-page .ledger-page-curl,#back-page .ledger-candle{display:none}
}

/* ===== FLORENCIA DESK EFFECTS ===== */
/* =========================================================
FLORENCIA DESK EFFECTS PACK
Works with #cwDeskFrame, #cwDeskLayers and existing cw* IDs
========================================================= */

/* ===== END FLORENCIA DESK EFFECTS ===== */
/* ===== FLORENCIA WINDOW SHADOW ===== */

/* ===== END FLORENCIA WINDOW SHADOW ===== */
/* =========================================================
FLORENCIA BACKROOM — VICTORIAN BOTANICAL MAGIC
ทำงานเฉพาะภายใน #back-page
========================================================= */
#back-page{--bm-gold:#d7bf82;--bm-rose:#b77a88;--bm-moss:#718066;background:radial-gradient(circle at 50% 15%,rgba(181,112,128,.18),transparent 29%),radial-gradient(circle at 12% 66%,rgba(113,128,102,.09),transparent 27%),radial-gradient(circle at 89% 75%,rgba(215,191,130,.08),transparent 25%),linear-gradient(180deg,#10090b 0%,#190e12 46%,#0d0809 100%)}
#back-page .backroom-magic-root{position:fixed;inset:0;z-index:1;overflow:hidden;pointer-events:none;isolation:isolate}
#back-page .bm-haze{position:absolute;inset:-20%;opacity:.38;filter:blur(38px);background:radial-gradient(ellipse at 28% 38%,rgba(168,97,112,.13),transparent 48%),radial-gradient(ellipse at 72% 57%,rgba(215,191,130,.09),transparent 45%),radial-gradient(ellipse at 48% 86%,rgba(113,128,102,.07),transparent 43%);animation:bmHazeDrift 25s ease-in-out infinite alternate}

#back-page .bm-sigil{position:absolute;left:50%;top:48%;width:min(78vw,980px);aspect-ratio:1;border-radius:50%;opacity:.10;transform:translate(-50%,-50%);background:radial-gradient(circle,transparent 0 43%,rgba(215,191,130,.18) 43.3% 43.8%,transparent 44.2%),radial-gradient(circle,transparent 0 31%,rgba(183,122,136,.15) 31.2% 31.7%,transparent 32.1%),repeating-conic-gradient(from 0deg,rgba(215,191,130,.14) 0 1deg,transparent 1deg 15deg);-webkit-mask:radial-gradient(circle,transparent 0 22%,#000 23% 58%,transparent 59%);mask:radial-gradient(circle,transparent 0 22%,#000 23% 58%,transparent 59%);animation:bmSigilTurn 190s linear infinite}
#back-page .bm-sigil::before,#back-page .bm-sigil::after{content:"";position:absolute;border-radius:50%}
#back-page .bm-sigil::before{inset:15%;border:1px solid rgba(215,191,130,.23)}
#back-page .bm-sigil::after{inset:28%;border:1px solid rgba(183,122,136,.18)}

#back-page .bm-arc{position:absolute;left:-25%;top:56%;width:150%;height:1px;opacity:0;background:linear-gradient(90deg,transparent,rgba(215,191,130,.28),rgba(183,122,136,.22),transparent);box-shadow:0 0 12px rgba(215,191,130,.15),0 0 28px rgba(183,122,136,.08);transform:translateX(-18%) rotate(-7deg);animation:bmArcSweep 17s ease-in-out infinite}

#back-page .bm-pollen{position:absolute;left:var(--x);top:var(--y);width:var(--s);height:var(--s);border-radius:50%;opacity:0;background:var(--c);box-shadow:0 0 8px var(--c),0 0 18px rgba(215,191,130,.18);animation:bmPollenRise var(--d) linear infinite,bmPollenPulse 4.5s ease-in-out infinite;animation-delay:var(--delay)}


#back-page .bm-petal{position:absolute;top:-12%;left:var(--x);width:var(--w);height:var(--h);border-radius:75% 25% 68% 32%;opacity:0;background:linear-gradient(145deg,rgba(232,181,191,.72),rgba(142,75,91,.34));filter:blur(.2px) drop-shadow(0 2px 5px rgba(0,0,0,.2));animation:bmPetalFall var(--d) ease-in forwards}

#back-page .bm-memory{position:absolute;left:var(--x);top:var(--y);max-width:240px;color:rgba(229,205,155,0);font:italic 15px/1.5 "Cormorant Garamond",serif;letter-spacing:.06em;text-shadow:0 0 14px rgba(215,191,130,.18);transform:translateY(10px) rotate(var(--r));animation:bmMemoryAppear 9s ease-in-out forwards}

#back-page .bm-bloom-light{position:absolute;left:var(--x);top:var(--y);width:4px;height:4px;border-radius:50%;opacity:0;background:#ead39a;box-shadow:0 0 8px rgba(234,211,154,.9),0 0 20px rgba(183,122,136,.35);animation:bmBloomWake 4.8s ease-in-out forwards}

#back-page .backroom-magic-root{animation:bmRoomBreath 18s ease-in-out infinite}

#back-page .back-hero{background:linear-gradient(rgba(18,9,11,.74),rgba(18,9,11,.74)),radial-gradient(circle at 50% 34%,rgba(183,122,136,.11),transparent 41%)}
#back-page .back-hero::after{content:"";position:absolute;inset:18px;z-index:1;pointer-events:none;opacity:.18;background:radial-gradient(ellipse 9% 3% at 6% 6%,rgba(119,139,92,.42) 0 45%,transparent 50%),radial-gradient(ellipse 9% 3% at 11% 10%,rgba(119,139,92,.34) 0 45%,transparent 50%),radial-gradient(ellipse 9% 3% at 94% 94%,rgba(119,139,92,.42) 0 45%,transparent 50%),radial-gradient(ellipse 9% 3% at 89% 90%,rgba(119,139,92,.34) 0 45%,transparent 50%)}
#back-page .back-title{text-shadow:0 3px 0 #080405,0 12px 34px rgba(0,0,0,.55),0 0 24px rgba(183,122,136,.07)}
#back-page .warning-strip{border-color:rgba(215,191,130,.36);background:linear-gradient(90deg,rgba(94,43,56,.17),rgba(111,48,63,.25),rgba(94,43,56,.17));box-shadow:inset 0 0 0 2px rgba(215,191,130,.04),0 0 24px rgba(183,122,136,.035)}
#back-page .extract-row{background:linear-gradient(135deg,rgba(255,255,255,.018),rgba(169,104,117,.03)),radial-gradient(circle at 90% 10%,rgba(215,191,130,.026),transparent 29%)}
#back-page .extract-row:hover{transform:translateX(4px) translateY(-1px);box-shadow:0 12px 28px rgba(0,0,0,.25),0 0 25px rgba(183,122,136,.05)}
@media (max-width:700px){#back-page .bm-sigil{width:130vw;opacity:.07}
#back-page .bm-memory{display:none}
}
@media (prefers-reduced-motion:reduce){#back-page .bm-haze,#back-page .bm-sigil,#back-page .bm-arc,#back-page .bm-pollen,#back-page .bm-petal,#back-page .bm-memory,#back-page .bm-bloom-light,#back-page .backroom-magic-root{animation:none!important}
}
/* =========================================================
FLORENCIA BACKROOM — LOWER SECTIONS MAGIC
CLEAN VERSION: no section bands, no rune bands, no grid cuts
========================================================= */
#back-page .extracts-inner,#back-page .ledger-section,#back-page .tension-section,#back-page .footer-back{position:relative;isolation:isolate;overflow:visible;background:transparent!important;}
/* Available Extracts */
#back-page .extracts-ribbon{overflow:visible}
#back-page .extracts-ribbon.is-awake{animation:brRibbonWake 1.35s cubic-bezier(.22,1,.36,1)}

#back-page .rose-cluster{animation:brRoseSealPulse 6s ease-in-out infinite}

/* Extract rows */
#back-page .extract-row{overflow:hidden}
#back-page .extract-row::after{content:"";position:absolute;left:-35%;top:-20%;width:26%;height:140%;pointer-events:none;opacity:0;background:linear-gradient(90deg,transparent,rgba(255,238,195,.12),transparent);transform:skewX(-18deg);}
#back-page .extract-row:hover::after{animation:brExtractSweep 1.1s ease 1}

#back-page .ext-name{position:relative}
#back-page .extract-row:hover .ext-name::after{content:"";position:absolute;left:0;bottom:-5px;width:min(180px,75%);height:1px;background:linear-gradient(90deg,rgba(221,201,143,.7),rgba(200,139,152,.26),transparent);transform-origin:left;animation:brInkUnderline .75s cubic-bezier(.22,1,.36,1) forwards;}

/* Ledger */
#back-page .ledger-section::before{content:"";position:absolute;inset:10% -10%;z-index:0;pointer-events:none;background:radial-gradient(circle at 28% 48%,rgba(221,201,143,.035),transparent 28%),radial-gradient(circle at 72% 52%,rgba(200,139,152,.035),transparent 28%);filter:blur(26px);animation:brLedgerGlow 14s ease-in-out infinite alternate;}

#back-page .ledger-block{z-index:2}
#back-page .ledger-block::after{content:"";position:absolute;inset:0;pointer-events:none;opacity:0;background:linear-gradient(115deg,transparent 32%,rgba(255,236,187,.10) 48%,transparent 62%);transform:translateX(-80%);}
#back-page .ledger-block.is-reading::after{animation:brLedgerShimmer 1.4s ease .1s 1}

/* Current Complications */
#back-page .tension-item{position:relative;z-index:2;transition:background .35s ease,transform .35s ease;}
#back-page .tension-item:hover{transform:translateX(5px);background:linear-gradient(90deg,rgba(169,104,117,.035),transparent 72%);}

/* ละอองส่วนล่าง */
#back-page .br-lower-mote{position:absolute;left:var(--x);top:var(--y);z-index:1;width:var(--s);height:var(--s);border-radius:50%;pointer-events:none;opacity:0;background:var(--c);box-shadow:0 0 8px var(--c);animation:brLowerMote var(--d) linear infinite;animation-delay:var(--delay);}

/* Footer */
#back-page .footer-back{
  min-height:150px;
  padding:40px 0 60px;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  gap:20px;
}
#back-page .footer-back::before{
  content:"";
  position:absolute;
  left:50%;
  bottom:-140px;
  width:min(460px,65vw);
  aspect-ratio:1;
  border-radius:50%;
  transform:translateX(-50%);
  pointer-events:none;
  opacity:.10;
  background:
    radial-gradient(circle,transparent 0 42%,rgba(221,201,143,.25) 42.4% 42.8%,transparent 43.2%),
    repeating-conic-gradient(from 0deg,rgba(200,139,152,.17) 0 1deg,transparent 1deg 18deg);
  -webkit-mask:radial-gradient(circle,transparent 0 30%,#000 31% 52%,transparent 53%);
  mask:radial-gradient(circle,transparent 0 30%,#000 31% 52%,transparent 53%);
  animation:brReturnSealTurn 120s linear infinite;
}


#back-page .back-btn{position:relative;z-index:3;overflow:hidden;box-shadow:0 0 0 rgba(221,201,143,0)}
#back-page .back-btn::before{
  content:"";
  position:absolute;
  inset:-2px;
  border-radius:inherit;
  opacity:0;
  pointer-events:none;
  background:linear-gradient(90deg,transparent,rgba(255,239,200,.38),transparent);
  transform:translateX(-120%);
}
#back-page .back-btn:hover{box-shadow:0 0 20px rgba(221,201,143,.12),0 0 40px rgba(200,139,152,.07)}
#back-page .back-btn:hover::before{animation:brReturnButtonSweep 1.05s ease 1}

#back-page .back-btn.is-returning{animation:brReturnPortal 1.2s cubic-bezier(.22,1,.36,1)}


/* กลีบส่วนล่าง */
#back-page .br-lower-petal{position:absolute;top:-18px;left:var(--x);z-index:1;width:var(--w);height:var(--h);border-radius:70% 30% 68% 32%;pointer-events:none;opacity:0;background:linear-gradient(145deg,rgba(226,177,185,.66),rgba(111,48,63,.28));filter:drop-shadow(0 2px 4px rgba(0,0,0,.18));animation:brLowerPetalFall var(--d) ease-in forwards;}

#back-page .br-section-aura,#back-page .br-rune-band{display:none!important}
@media (max-width:700px){#back-page .footer-back::before{width:min(420px,88vw);bottom:-125px}
}
@media (prefers-reduced-motion:reduce){#back-page .rose-cluster,#back-page .ledger-section::before,#back-page .footer-back::before,#back-page .br-lower-mote,#back-page .br-lower-petal{animation:none!important}
}
/* ===== END FLORENCIA BACKROOM LOWER SECTIONS MAGIC ===== */
/* ===== BACKROOM CLEAN BACKGROUND OVERRIDE ===== */
#back-page::before{background:radial-gradient(circle at center,transparent 42%,rgba(0,0,0,.58) 100%)!important;background-size:100% 100%!important;mask-image:none!important;}
#back-page .back-hero{background:linear-gradient(rgba(18,9,11,.74),rgba(18,9,11,.74)),radial-gradient(circle at 50% 34%,rgba(183,122,136,.11),transparent 41%)!important;}
#back-page .br-section-aura,#back-page .br-rune-band{display:none!important}
#back-page .extracts-inner,#back-page .ledger-section,#back-page .tension-section,#back-page .footer-back{background:transparent!important;overflow:visible!important;}
/* ===== END BACKROOM CLEAN BACKGROUND OVERRIDE ===== */

/* ===== BACKROOM FOOTER — TRUE FINAL EDGE ===== */
#back-page .footer-back{
  position:relative;
  z-index:2;
  width:100%;
  min-height:170px;
  margin:0;
  padding:30px 20px 34px;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  gap:16px;
  text-align:center;
  border-top:1px solid rgba(221,201,143,.16);
  background:transparent!important;
  overflow:hidden!important;
  box-shadow:none!important;
}

#back-page .footer-back-text{
  position:relative;
  z-index:2;
  width:100%;
  max-width:700px;
  margin:0;
  text-align:center;
}

#back-page .footer-back::before{
  content:"";
  position:absolute;
  left:50%;
  top:50%;
  bottom:auto!important;
  width:min(340px,62vw);
  aspect-ratio:1;
  border-radius:50%;
  transform:translate(-50%,-50%);
  pointer-events:none;
  opacity:.14;
  background:
    radial-gradient(circle,transparent 0 42%,rgba(221,201,143,.28) 42.4% 42.9%,transparent 43.4%),
    repeating-conic-gradient(from 0deg,rgba(200,139,152,.20) 0 1deg,transparent 1deg 18deg);
  -webkit-mask:radial-gradient(circle,transparent 0 30%,#000 31% 54%,transparent 55%);
  mask:radial-gradient(circle,transparent 0 30%,#000 31% 54%,transparent 55%);
  filter:drop-shadow(0 0 6px rgba(221,201,143,.14));
  animation:brReturnSealTurn 120s linear infinite;
}

#back-page .back-btn{
  position:relative;
  z-index:3;
}

/* ตัดพื้นที่เลื่อนที่เกิดจากวงแหวนซึ่งเคยยื่นต่ำกว่า Footer */
#back-page .footer-back + *{margin-top:0!important}

@media (max-width:700px){
  #back-page .footer-back{min-height:156px;padding:26px 14px 30px;gap:14px}
  #back-page .footer-back::before{width:min(310px,82vw)}
}
/* ===== END BACKROOM FOOTER — TRUE FINAL EDGE ===== */


/* ===== CURRENT COMPLICATIONS — EQUAL NEON MARKERS ===== */
#back-page .tension-item{
  grid-template-columns:5px minmax(0,1fr);
  align-items:center;
}

#back-page .tension-marker{
  display:block;
  width:5px;
  min-width:5px;
  max-width:5px;
  height:54px;
  min-height:54px;
  max-height:54px;
  margin:0;
  padding:0;
  align-self:center;
  border-radius:999px;
  transform:none;
  transform-origin:center;
  filter:none;
  box-shadow:0 0 6px currentColor,0 0 13px color-mix(in srgb,currentColor 45%,transparent);
}

#back-page .t-red{
  color:#9d5965;
  background:currentColor;
  box-shadow:0 0 6px currentColor,0 0 13px rgba(157,89,101,.34);
}

#back-page .t-amber{
  color:#b99a5b;
  background:currentColor;
  box-shadow:0 0 6px currentColor,0 0 13px rgba(185,154,91,.34);
}

#back-page .t-green{
  color:#71816a;
  background:currentColor;
  box-shadow:0 0 6px currentColor,0 0 13px rgba(113,129,106,.34);
}

#back-page .tension-item:hover .tension-marker{
  animation:equalMarkerPulse 1.5s ease-in-out infinite;
}


/* ===== END CURRENT COMPLICATIONS — EQUAL NEON MARKERS ===== */


/* ===== CURRENT COMPLICATIONS — INLINE ORBS FINAL =====
   คงชื่อปัญหาและคำอธิบายเดิมทั้งหมด
========================================================= */
#back-page .tension-item{
  --status-color:#d1ae63;
  position:relative;
  display:block;
  margin:0;
  padding:28px 0 31px;
  border-bottom:1px solid rgba(221,201,143,.11);
  background:transparent;
  transition:background .35s ease,padding-left .35s cubic-bezier(.22,1,.36,1);
}

#back-page .tension-item:hover{
  padding-left:5px;
  background:linear-gradient(90deg,rgba(169,104,117,.032),transparent 45%);
}

#back-page .tension-heading{
  display:flex;
  align-items:center;
  gap:11px;
  margin:0;
}

#back-page .tension-name{
  margin:0!important;
  color:var(--br-pale);
  font:500 15px/1.4 "Cinzel",serif;
  letter-spacing:.04em;
}

#back-page .tension-rule{
  width:min(470px,76%);
  height:1px;
  margin:11px 0 13px 27px;
  background:linear-gradient(90deg,rgba(221,201,143,.30),rgba(221,201,143,.09) 66%,transparent);
}

#back-page .tension-text{
  max-width:970px;
  margin:0 0 0 27px!important;
  color:rgba(234,220,197,.58);
  font-size:16px;
  line-height:1.75;
}

/* วงกลมเล็ก วางหน้าหัวข้อ */
#back-page .tension-orb{
  position:relative;
  display:inline-block;
  flex:0 0 16px;
  width:16px;
  height:16px;
  border:1px solid var(--status-color);
  border-radius:50%;
  background:radial-gradient(circle,var(--status-color) 0 1.2px,transparent 1.7px 4px,color-mix(in srgb,var(--status-color) 68%,transparent) 4.2px 4.7px,transparent 5px);
  box-shadow:0 0 4px var(--status-color),0 0 9px color-mix(in srgb,var(--status-color) 48%,transparent),0 0 15px color-mix(in srgb,var(--status-color) 18%,transparent),inset 0 0 5px color-mix(in srgb,var(--status-color) 22%,transparent);
  opacity:.88;
  animation:tensionOrbBreath 3.8s ease-in-out infinite;
  transition:transform .35s ease,filter .35s ease,opacity .35s ease;
}

#back-page .tension-orb::before{
  content:"";
  position:absolute;
  inset:3px;
  border:1px solid color-mix(in srgb,var(--status-color) 58%,transparent);
  border-radius:50%;
}

#back-page .tension-orb::after{
  content:"";
  position:absolute;
  left:50%;
  top:50%;
  width:2.5px;
  height:2.5px;
  border-radius:50%;
  background:var(--status-color);
  transform:translate(-50%,-50%);
  box-shadow:0 0 4px var(--status-color),0 0 7px var(--status-color);
}

#back-page .tension-critical{--status-color:#c87687}
#back-page .tension-warning{--status-color:#d1ae63}
#back-page .tension-stable{--status-color:#91a284}

#back-page .tension-item:hover .tension-orb{
  opacity:1;
  filter:brightness(1.18);
  transform:scale(1.06);
}

@media (max-width:700px){
  #back-page .tension-item{padding:24px 0 27px}
  #back-page .tension-heading{gap:9px}
  #back-page .tension-orb{flex-basis:14px;width:14px;height:14px}
  #back-page .tension-orb::before{inset:2.5px}
  #back-page .tension-name{font-size:13px}
  #back-page .tension-rule,#back-page .tension-text{margin-left:23px!important}
}

@media (prefers-reduced-motion:reduce){
  #back-page .tension-orb{animation:none!important}
}
/* ===== END CURRENT COMPLICATIONS — INLINE ORBS FINAL ===== */


/* ===== CURRENT COMPLICATIONS — ORB BEFORE TITLE FIX ===== */
#back-page .tension-heading{
  display:inline-flex!important;
  flex-wrap:nowrap!important;
  justify-content:flex-start!important;
  align-items:center!important;
  width:auto!important;
  max-width:100%;
  gap:10px!important;
  margin:0!important;
  text-align:left!important;
}

#back-page .tension-orb{
  position:relative!important;
  left:auto!important;
  right:auto!important;
  top:auto!important;
  bottom:auto!important;
  flex:0 0 16px!important;
  width:16px!important;
  height:16px!important;
  margin:0!important;
  transform:none;
}

#back-page .tension-name{
  display:inline-block!important;
  flex:0 1 auto!important;
  width:auto!important;
  margin:0!important;
  padding:0!important;
  text-align:left!important;
}

#back-page .tension-rule{
  margin-left:26px!important;
}

#back-page .tension-text{
  margin-left:26px!important;
}
/* ===== END CURRENT COMPLICATIONS — ORB BEFORE TITLE FIX ===== */

/* ===== AVAILABLE EXTRACTS — SOFT LEATHER LEDGER =====
   เปลี่ยนเฉพาะดีไซน์ของ Available Extracts
   ไม่แก้ข้อความ ไม่แก้ HTML ไม่ขยับโครงสร้างข้อมูล
========================================================= */

/* ให้พื้นส่วนนี้กลืนไปกับพื้นหลัง Backroom */
#back-page .extracts-inner{
  position:relative;
  isolation:isolate;
}

#back-page .extracts-inner::before{
  content:"";
  position:absolute;
  inset:38px -22px 36px;
  z-index:-2;
  pointer-events:none;
  background:
    radial-gradient(circle at 18% 10%,rgba(185,154,91,.035),transparent 24%),
    radial-gradient(circle at 84% 36%,rgba(119,68,78,.035),transparent 27%),
    linear-gradient(180deg,rgba(21,12,14,.05),rgba(10,6,7,.025));
}

#back-page .extracts-inner::after{
  content:"";
  position:absolute;
  inset:46px -10px 46px;
  z-index:-1;
  pointer-events:none;
  opacity:.08;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='180' height='180' viewBox='0 0 180 180'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.68' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='.18'/%3E%3C/svg%3E");
  mix-blend-mode:soft-light;
}

/* หัวข้อ: แถบหนังเก่า กลืนกับฉาก ไม่มีกรอบล้อม */
#back-page .extracts-ribbon{
  position:relative;
  display:flex;
  align-items:center;
  min-height:78px;
  margin:0 0 34px;
  padding:14px 28px 14px 88px;
  overflow:visible;
  border:0!important;
  border-radius:0!important;
  background:
    radial-gradient(circle at 18% 22%,rgba(255,239,203,.028),transparent 22%),
    linear-gradient(180deg,rgba(70,34,40,.74),rgba(42,21,25,.80)),
    repeating-linear-gradient(92deg,rgba(255,255,255,.012) 0 1px,transparent 1px 6px);
  box-shadow:
    0 12px 26px rgba(0,0,0,.22),
    inset 0 1px 0 rgba(221,201,143,.08),
    inset 0 -1px 0 rgba(0,0,0,.34);
}

/* เหลือเพียงเส้นทองบางด้านบนและล่าง */
#back-page .extracts-ribbon::before{
  content:"";
  position:absolute;
  left:0;
  right:0;
  top:0;
  bottom:auto;
  width:auto;
  height:1px;
  border:0;
  background:linear-gradient(90deg,transparent,rgba(221,201,143,.36) 10%,rgba(221,201,143,.18) 50%,rgba(221,201,143,.36) 90%,transparent);
  transform:none;
  box-shadow:none;
}

#back-page .extracts-ribbon::after{
  content:"";
  position:absolute;
  left:0;
  right:0;
  bottom:0;
  top:auto;
  width:auto;
  height:1px;
  border:0;
  background:linear-gradient(90deg,transparent,rgba(221,201,143,.22) 10%,rgba(221,201,143,.11) 50%,rgba(221,201,143,.22) 90%,transparent);
  transform:none;
  box-shadow:none;
}

/* ลบสามเหลี่ยม/หางริบบิ้นที่เคยเกิดจาก pseudo element ของหัวข้อ */
#back-page .extracts-ribbon h2::after{
  content:none!important;
  display:none!important;
}

/* ชื่อหัวข้อให้นุ่มขึ้น */
#back-page .extracts-ribbon h2{
  position:relative;
  z-index:2;
  margin:0;
  color:#eadcc4;
  font:400 clamp(24px,4vw,34px)/1.15 "IM Fell English",serif;
  letter-spacing:.015em;
  text-transform:none;
  text-shadow:0 1px 0 rgba(0,0,0,.52),0 3px 10px rgba(0,0,0,.18);
}

/* ตราดอกไม้แบบ Brass Seal — ลด glow และวงซ้อน */
#back-page .rose-cluster{
  position:absolute;
  left:27px;
  z-index:3;
  width:44px;
  height:44px;
  display:grid;
  place-items:center;
  border-radius:50%;
  color:#cdaeb2;
  font-size:19px;
  border:1px solid rgba(191,158,94,.48);
  background:
    radial-gradient(circle at 36% 30%,rgba(255,235,194,.14),transparent 18%),
    radial-gradient(circle,#5d3038 0 34%,#221315 35% 62%,#8f7444 63% 66%,#1b1012 67% 100%);
  box-shadow:
    inset 0 0 9px rgba(0,0,0,.56),
    0 4px 10px rgba(0,0,0,.26);
  text-shadow:none;
}

/* Circle note: กลืนกับพื้น ไม่มีกรอบแข็ง */
#back-page .circle-note{
  position:relative;
  max-width:920px;
  margin:0 auto 42px;
  padding:24px 28px 24px 34px;
  border:0!important;
  background:
    linear-gradient(90deg,rgba(185,154,91,.035),rgba(69,38,32,.018) 58%,transparent),
    repeating-linear-gradient(0deg,rgba(221,201,143,.009) 0 1px,transparent 1px 5px);
  box-shadow:none;
}

/* เส้นทองเดียวด้านซ้าย จางและละมุน */
#back-page .circle-note::before{
  content:"";
  position:absolute;
  left:0;
  top:16px;
  bottom:16px;
  width:1px;
  background:linear-gradient(transparent,rgba(221,201,143,.56) 18%,rgba(221,201,143,.56) 82%,transparent);
  box-shadow:0 0 8px rgba(221,201,143,.08);
}

#back-page .circle-note::after{
  content:"EX LIBRIS · PRIVATE LEDGER";
  position:absolute;
  right:16px;
  bottom:7px;
  color:rgba(221,201,143,.07);
  font:500 8px "Cinzel",serif;
  letter-spacing:.16em;
  pointer-events:none;
}

#back-page .circle-note strong{
  color:#d3bd8b;
  font:500 13px "Cinzel",serif;
  letter-spacing:.07em;
}

/* หัวตาราง: คงตำแหน่งเดิม แต่ลดเส้นแข็ง */
#back-page .extract-table-header{
  position:relative;
  padding:0 20px 13px;
  margin-bottom:0;
  border-bottom:1px solid rgba(221,201,143,.14);
  color:rgba(221,201,143,.58);
  background:transparent;
  font:500 10px "Cinzel",serif;
  letter-spacing:.17em;
  text-transform:uppercase;
}

#back-page .extract-table-header::before,#back-page .extract-table-header::after{
  content:none!important;
  display:none!important;
}

/* แถวสินค้า: กลืนกับฉาก ไม่มีกรอบกล่อง */
#back-page .extract-row{
  position:relative;
  align-items:start;
  margin-top:0;
  padding:26px 24px 27px 34px;
  overflow:hidden;
  border:0!important;
  border-bottom:1px solid rgba(221,201,143,.09)!important;
  background:
    linear-gradient(90deg,rgba(85,44,50,.028),transparent 27%),
    radial-gradient(circle at 92% 18%,rgba(221,201,143,.016),transparent 22%)!important;
  box-shadow:none!important;
  transition:background .35s ease,transform .35s cubic-bezier(.22,1,.36,1);
}

#back-page .extract-row::before{
  content:"";
  position:absolute;
  left:0;
  top:22px;
  bottom:22px;
  width:1px!important;
  background:linear-gradient(transparent,var(--br-dusty) 24%,var(--br-burgundy) 76%,transparent);
  opacity:.54;
  box-shadow:none!important;
  transition:opacity .35s ease,filter .35s ease;
}

#back-page .extract-row::after{
  content:none!important;
  display:none!important;
}

#back-page .extract-row:hover{
  transform:translateX(2px);
  background:
    linear-gradient(90deg,rgba(110,57,69,.052),rgba(185,154,91,.014) 54%,transparent),
    radial-gradient(circle at 92% 18%,rgba(221,201,143,.025),transparent 22%)!important;
  box-shadow:none!important;
}

#back-page .extract-row:hover::before{
  width:1px!important;
  opacity:.82;
  filter:brightness(1.08);
  box-shadow:0 0 8px rgba(200,139,152,.08)!important;
}

/* ตัวอักษรยังอยู่ตำแหน่งเดิม แค่ลดความเป็น UI */
#back-page .ext-name{
  margin:0;
  color:#ead9c0;
  font:400 27px/1.1 "IM Fell English",serif;
  letter-spacing:.008em;
  text-shadow:0 1px 0 rgba(0,0,0,.38);
}

#back-page .extract-row:hover .ext-name{
  letter-spacing:.016em;
  color:#efe0c8;
  text-shadow:0 1px 0 rgba(0,0,0,.42);
}

#back-page .ext-source{
  margin:7px 0 0;
  color:rgba(234,220,197,.38);
  font:italic 13px/1.55 "Cormorant Garamond",serif;
}

#back-page .ext-effect{
  margin:0;
  color:rgba(234,220,197,.62);
  font:400 15px/1.78 "Cormorant Garamond",serif;
}

#back-page .ext-price{
  margin:0;
  color:#d5bf8e;
  font:500 16px/1.4 "Cormorant Garamond",serif;
  letter-spacing:.02em;
}

/* ป้าย Circle: ฉลากหมึกเก่า ไม่ใช่ปุ่ม */
#back-page .ext-grade{
  position:relative;
  display:inline-flex;
  align-items:center;
  justify-content:center;
  min-width:82px;
  padding:7px 11px 6px;
  overflow:hidden;
  border:1px solid rgba(221,201,143,.18);
  border-radius:0!important;
  background:rgba(22,13,14,.34);
  color:#dfd0b6;
  font:500 10px "Cinzel",serif;
  letter-spacing:.065em;
  box-shadow:inset 0 0 0 1px rgba(0,0,0,.16);
}

#back-page .ext-grade::before{
  content:none!important;
  display:none!important;
}

#back-page .grade-i{
  color:#dfd6bd;
  border-color:rgba(145,161,132,.27);
  background:linear-gradient(90deg,rgba(80,98,70,.13),rgba(22,13,14,.32));
}

#back-page .grade-ii{
  color:#e2cbd0;
  border-color:rgba(200,118,135,.25);
  background:linear-gradient(90deg,rgba(111,48,63,.16),rgba(22,13,14,.32));
}

#back-page .grade-iii{
  color:#dcc894;
  border-color:rgba(185,154,91,.29);
  background:linear-gradient(90deg,rgba(92,74,48,.17),rgba(22,13,14,.32));
}

#back-page .grade-forbidden,#back-page .grade-restricted,#back-page .grade-occult,#back-page .grade-illicit{
  border-radius:0!important;
}

/* Availability ใต้ราคาให้จางเหมือนจดดินสอ */
#back-page .ext-price + p{
  color:rgba(221,201,143,.22)!important;
  font-family:"Cormorant Garamond",serif!important;
  font-style:italic;
  letter-spacing:.03em!important;
}

@media (max-width:700px){
  #back-page .extracts-ribbon{
    min-height:68px;
    padding:12px 18px 12px 72px;
  }

  #back-page .rose-cluster{
    left:18px;
    width:40px;
    height:40px;
    font-size:18px;
  }

  #back-page .circle-note{
    padding:20px 18px 22px 24px;
  }

  #back-page .circle-note::after{
    display:none;
  }

  #back-page .extract-row{
    padding:23px 18px 24px 26px;
  }

  #back-page .ext-name{
    font-size:24px;
  }
}
/* ===== END AVAILABLE EXTRACTS — SOFT LEATHER LEDGER ===== */


/* ===== AVAILABLE EXTRACTS — SOFT ARCHIVAL REFINEMENT =====
   ลดความแข็งของแถบหัวข้อ กล่องคำอธิบาย เส้นตาราง และแถวสินค้า
   ไม่เปลี่ยนข้อความหรือโครงสร้าง
========================================================= */

/* ตัดกรอบสี่เหลี่ยมกว้าง ๆ ออกจากหัวข้อ */
#back-page .extracts-ribbon{
  width:fit-content;
  max-width:100%;
  min-height:auto;
  margin:0 0 42px 18px;
  padding:14px 34px 15px 78px;
  background:
    radial-gradient(ellipse at 38% 45%,rgba(105,53,61,.52),rgba(47,24,28,.30) 58%,transparent 78%),
    linear-gradient(90deg,rgba(54,27,31,.72),rgba(37,20,23,.28) 82%,transparent);
  box-shadow:
    0 12px 28px rgba(0,0,0,.15),
    inset 0 1px 0 rgba(221,201,143,.055);
  filter:drop-shadow(0 7px 14px rgba(0,0,0,.12));
}

/* เส้นทองไม่ลากเต็มกล่อง ให้ค่อย ๆ จางออก */
#back-page .extracts-ribbon::before{
  left:16px;
  right:10%;
  top:0;
  background:linear-gradient(90deg,rgba(221,201,143,.34),rgba(221,201,143,.10) 62%,transparent);
}

#back-page .extracts-ribbon::after{
  left:10%;
  right:0;
  bottom:0;
  background:linear-gradient(90deg,transparent,rgba(221,201,143,.09) 38%,rgba(221,201,143,.24));
}

/* ให้ขอบของแถบดูไม่ตรงเกินไป */
#back-page .extracts-ribbon{
  clip-path:polygon(0 8%,96% 0,100% 84%,4% 100%);
}

/* ตราทองเหลืองเล็กลงและไม่เป็นปุ่ม */
#back-page .rose-cluster{
  left:20px;
  width:40px;
  height:40px;
  font-size:17px;
  border-color:rgba(191,158,94,.36);
  box-shadow:
    inset 0 0 8px rgba(0,0,0,.52),
    0 3px 8px rgba(0,0,0,.18);
  opacity:.9;
}

/* กล่อง Circle เดิมแข็งเกินไป: ตัดพื้นสี่เหลี่ยมออก */
#back-page .circle-note{
  max-width:900px;
  margin:0 auto 48px;
  padding:14px 24px 18px 30px;
  background:
    radial-gradient(ellipse at 22% 50%,rgba(185,154,91,.030),transparent 55%);
}

/* เส้นซ้ายสั้นและจาง ไม่เหมือนกรอบ */
#back-page .circle-note::before{
  top:24px;
  bottom:24px;
  opacity:.68;
  background:linear-gradient(transparent,rgba(221,201,143,.42) 30%,rgba(221,201,143,.42) 70%,transparent);
}

/* ลบป้าย EX LIBRIS ที่ทำให้ดูเหมือน UI */
#back-page .circle-note::after{
  content:none!important;
  display:none!important;
}

/* หัวตารางไม่มีเส้นตัดแข็งเต็มแนว */
#back-page .extract-table-header{
  margin:0 6px 4px;
  padding:0 18px 12px;
  border-bottom:0;
}

#back-page .extract-table-header::after{
  content:"";
  display:block!important;
  position:absolute;
  left:18px;
  right:18px;
  bottom:0;
  height:1px;
  background:linear-gradient(90deg,transparent,rgba(221,201,143,.16) 14%,rgba(221,201,143,.16) 86%,transparent);
}

/* แถวสินค้าไม่ใช้เส้นแนวนอนเต็มแถว */
#back-page .extract-row{
  margin:0 6px;
  padding:28px 22px 30px 34px;
  border-bottom:0!important;
  background:
    radial-gradient(ellipse at 18% 45%,rgba(92,48,54,.030),transparent 38%),
    radial-gradient(ellipse at 82% 50%,rgba(185,154,91,.010),transparent 34%)!important;
}

/* ใช้เส้นสั้นจาง ๆ ระหว่างแถวแทน */
#back-page .extract-row:not(:last-child)::after{
  content:""!important;
  display:block!important;
  position:absolute;
  left:8%;
  right:8%;
  bottom:0;
  height:1px;
  background:linear-gradient(90deg,transparent,rgba(221,201,143,.09) 18%,rgba(221,201,143,.09) 82%,transparent);
}

/* ตัดเส้นตั้งฝั่งซ้ายออก เหลือเพียงรอยหมึกบาง */
#back-page .extract-row::before{
  top:32%;
  bottom:32%;
  width:1px!important;
  opacity:.24;
}

/* Hover ไม่ขยับทั้งแถว ลดความเป็นเว็บแอป */
#back-page .extract-row:hover{
  transform:none;
  background:
    radial-gradient(ellipse at 20% 45%,rgba(110,57,69,.052),transparent 42%),
    radial-gradient(ellipse at 80% 50%,rgba(185,154,91,.018),transparent 36%)!important;
}

/* ชื่อสินค้าไม่กระโดดตอน hover */
#back-page .extract-row:hover .ext-name{
  letter-spacing:.008em;
  color:#efe0c8;
}

/* ป้าย Circle ให้นุ่มเหมือนตราหมึก */
#back-page .ext-grade{
  min-width:78px;
  padding:6px 10px 5px;
  border-color:rgba(221,201,143,.12);
  background:rgba(22,13,14,.20);
  box-shadow:none;
  opacity:.88;
}

#back-page .grade-i{
  border-color:rgba(145,161,132,.20);
  background:radial-gradient(ellipse at center,rgba(80,98,70,.12),rgba(22,13,14,.18));
}

#back-page .grade-ii{
  border-color:rgba(200,118,135,.19);
  background:radial-gradient(ellipse at center,rgba(111,48,63,.13),rgba(22,13,14,.18));
}

#back-page .grade-iii{
  border-color:rgba(185,154,91,.22);
  background:radial-gradient(ellipse at center,rgba(92,74,48,.14),rgba(22,13,14,.18));
}

/* ลดความเป็นกล่องของพื้นที่รวม */
#back-page .extracts-inner::before{
  inset:44px -8px 34px;
  background:
    radial-gradient(ellipse at 22% 18%,rgba(185,154,91,.022),transparent 28%),
    radial-gradient(ellipse at 82% 45%,rgba(119,68,78,.020),transparent 34%);
}

/* บนมือถือยังคงอ่านง่าย */
@media (max-width:700px){
  #back-page .extracts-ribbon{
    margin-left:0;
    padding:12px 24px 13px 68px;
    clip-path:polygon(0 6%,97% 0,100% 88%,3% 100%);
  }

  #back-page .rose-cluster{
    left:17px;
    width:36px;
    height:36px;
    font-size:16px;
  }

  #back-page .extract-row{
    margin:0;
  }
}
/* ===== END AVAILABLE EXTRACTS — SOFT ARCHIVAL REFINEMENT ===== */
/* =========================================================
   AVAILABLE EXTRACTS — HOVER GLOW FRAME
   กรอบเรืองแสงเมื่อเมาส์เลื่อนไปโดนสารสกัด
========================================================= */

#back-page .extract-row{
  position:relative;
  isolation:isolate;
  border:1px solid transparent!important;
  transition:
    border-color .38s ease,
    background .38s ease,
    box-shadow .38s ease,
    filter .38s ease;
}

/* กรอบชั้นในบาง ๆ */
#back-page .extract-row::after{
  content:""!important;
  display:block!important;
  position:absolute;
  inset:5px;
  z-index:-1;
  pointer-events:none;
  border:1px solid transparent;
  opacity:0;
  transition:
    opacity .38s ease,
    border-color .38s ease,
    box-shadow .38s ease;
}

/* Hover ทั่วไป */
#back-page .extract-row:hover{
  transform:none!important;
  border-color:rgba(200,139,152,.38)!important;

  background:
    linear-gradient(
      90deg,
      rgba(111,48,63,.07),
      rgba(185,154,91,.022) 55%,
      transparent
    )!important;

  box-shadow:
    0 0 8px rgba(200,139,152,.10),
    0 0 24px rgba(200,139,152,.055),
    inset 0 0 18px rgba(200,139,152,.025)!important;

  filter:brightness(1.035);
}

#back-page .extract-row:hover::after{
  opacity:1;
  border-color:rgba(221,201,143,.12);

  box-shadow:
    inset 0 0 12px rgba(221,201,143,.025),
    0 0 10px rgba(200,139,152,.035);
}

/* ให้ชื่อสารสกัดเรืองขึ้นเพียงเล็กน้อย */
#back-page .extract-row:hover .ext-name{
  color:#f3e3ca;
  text-shadow:
    0 1px 0 rgba(0,0,0,.42),
    0 0 12px rgba(226,177,185,.10);
}

/* ป้าย Circle ตื่นขึ้นพร้อมกรอบ */
#back-page .extract-row:hover .ext-grade{
  filter:brightness(1.18);
  border-color:rgba(221,201,143,.42);

  box-shadow:
    0 0 7px rgba(221,201,143,.13),
    0 0 16px rgba(200,139,152,.07),
    inset 0 0 10px rgba(255,255,255,.025);
}
    /* I Circle — เขียวหม่น */
#back-page .extract-row:has(.grade-i):hover{
  border-color:rgba(145,161,132,.34)!important;

  box-shadow:
    0 0 8px rgba(145,161,132,.10),
    0 0 24px rgba(145,161,132,.045),
    inset 0 0 18px rgba(145,161,132,.022)!important;
}

/* II Circle — กุหลาบหม่น */
#back-page .extract-row:has(.grade-ii):hover{
  border-color:rgba(200,118,135,.38)!important;

  box-shadow:
    0 0 8px rgba(200,118,135,.12),
    0 0 24px rgba(200,118,135,.055),
    inset 0 0 18px rgba(200,118,135,.025)!important;
}

/* III Circle — ทองเก่า */
#back-page .extract-row:has(.grade-iii):hover{
  border-color:rgba(185,154,91,.40)!important;

  box-shadow:
    0 0 8px rgba(185,154,91,.13),
    0 0 24px rgba(185,154,91,.055),
    inset 0 0 18px rgba(185,154,91,.025)!important;
}

/* Forbidden / Restricted / Illicit — เรืองชัดขึ้น */
#back-page .extract-row:has(.grade-forbidden):hover,#back-page .extract-row:has(.grade-restricted):hover,#back-page .extract-row:has(.grade-illicit):hover{
  border-color:rgba(214,126,145,.52)!important;

  background:
    linear-gradient(
      90deg,
      rgba(126,40,55,.10),
      rgba(72,27,36,.045) 54%,
      transparent
    )!important;

  box-shadow:
    0 0 10px rgba(214,126,145,.18),
    0 0 28px rgba(214,126,145,.085),
    inset 0 0 22px rgba(126,40,55,.045)!important;
}

/* Occult — สีทองน้ำตาล */
#back-page .extract-row:has(.grade-occult):hover{
  border-color:rgba(190,158,98,.46)!important;

  box-shadow:
    0 0 9px rgba(190,158,98,.15),
    0 0 26px rgba(190,158,98,.065),
    inset 0 0 20px rgba(92,74,48,.035)!important;
}

/* ===== CURRENT COMPLICATIONS — LIVING LEDGER HOVER =====
   เพิ่มเอฟเฟกต์เฉพาะ Current Complications
   ไม่แก้ข้อความ ไม่เปลี่ยน HTML และไม่ขยับตำแหน่งรายการ
========================================================= */

#back-page .tension-item{
  --status-color:#d1ae63;
  position:relative!important;
  isolation:isolate;
  overflow:hidden;
  padding:28px 14px 31px!important;
  border:1px solid transparent!important;
  border-bottom-color:rgba(221,201,143,.09)!important;
  background:transparent!important;
  box-shadow:none!important;
  transition:
    border-color .42s ease,
    background .42s ease,
    box-shadow .42s ease,
    filter .42s ease!important;
}

/* สีประจำสถานะ */
#back-page .tension-critical{--status-color:#c87687}
#back-page .tension-warning{--status-color:#d1ae63}
#back-page .tension-stable{--status-color:#91a284}

/* แสงหมึกกวาดผ่านช้า ๆ */
#back-page .tension-item::before{
  content:"";
  position:absolute;
  inset:-20% auto -20% -28%;
  z-index:-1;
  width:24%;
  pointer-events:none;
  opacity:0;
  background:linear-gradient(
    90deg,
    transparent,
    color-mix(in srgb,var(--status-color) 10%,transparent),
    rgba(255,242,215,.035),
    transparent
  );
  filter:blur(4px);
  transform:skewX(-15deg);
}

/* กรอบชั้นในแบบเอกสารเวท */
#back-page .tension-item::after{
  content:"";
  position:absolute;
  inset:5px;
  z-index:-1;
  pointer-events:none;
  opacity:0;
  border:1px solid color-mix(in srgb,var(--status-color) 24%,transparent);
  box-shadow:
    inset 0 0 18px color-mix(in srgb,var(--status-color) 5%,transparent);
  transition:opacity .42s ease,border-color .42s ease,box-shadow .42s ease;
}

/* Hover ทั้งรายการ */
#back-page .tension-item:hover{
  padding-left:14px!important;
  border-color:color-mix(in srgb,var(--status-color) 38%,transparent)!important;
  border-bottom-color:color-mix(in srgb,var(--status-color) 38%,transparent)!important;
  background:
    linear-gradient(
      90deg,
      color-mix(in srgb,var(--status-color) 6%,transparent),
      rgba(185,154,91,.012) 56%,
      transparent
    )!important;
  box-shadow:
    0 0 8px color-mix(in srgb,var(--status-color) 12%,transparent),
    0 0 26px color-mix(in srgb,var(--status-color) 6%,transparent),
    inset 0 0 24px color-mix(in srgb,var(--status-color) 3%,transparent)!important;
  filter:brightness(1.025);
}

#back-page .tension-item:hover::before{
  opacity:1;
  animation:tensionLedgerSweep 1.55s ease 1;
}

#back-page .tension-item:hover::after{
  opacity:1;
  border-color:color-mix(in srgb,var(--status-color) 20%,transparent);
  box-shadow:
    inset 0 0 16px color-mix(in srgb,var(--status-color) 5%,transparent),
    0 0 10px color-mix(in srgb,var(--status-color) 4%,transparent);
}

/* หัวข้อและคำอธิบายค่อย ๆ ตื่นขึ้น */
#back-page .tension-name{
  transition:color .38s ease,text-shadow .38s ease,letter-spacing .48s ease!important;
}

#back-page .tension-text{
  transition:color .38s ease,text-shadow .38s ease!important;
}

#back-page .tension-item:hover .tension-name{
  color:#f3dfc8!important;
  letter-spacing:.055em!important;
  text-shadow:
    0 0 10px color-mix(in srgb,var(--status-color) 14%,transparent);
}

#back-page .tension-item:hover .tension-text{
  color:rgba(241,226,204,.70)!important;
  text-shadow:0 0 12px rgba(221,201,143,.025);
}

/* เส้นใต้หัวข้อยาวขึ้นเล็กน้อย แต่ไม่ขยับ Layout */
#back-page .tension-rule{
  transform-origin:left center;
  transform:scaleX(.86);
  opacity:.64;
  transition:
    transform .7s cubic-bezier(.22,1,.36,1),
    opacity .38s ease,
    filter .38s ease!important;
}

#back-page .tension-item:hover .tension-rule{
  transform:scaleX(1);
  opacity:1;
  filter:drop-shadow(0 0 4px color-mix(in srgb,var(--status-color) 16%,transparent));
}

/* วงกลมเวทหมุนช้าและเรืองขึ้น */
#back-page .tension-orb{
  transform:rotate(0deg)!important;
  transition:
    transform .9s cubic-bezier(.22,1,.36,1),
    opacity .38s ease,
    filter .38s ease,
    box-shadow .38s ease!important;
}

#back-page .tension-item:hover .tension-orb{
  opacity:1!important;
  filter:brightness(1.24)!important;
  transform:rotate(180deg) scale(1.08)!important;
  box-shadow:
    0 0 6px var(--status-color),
    0 0 14px color-mix(in srgb,var(--status-color) 62%,transparent),
    0 0 25px color-mix(in srgb,var(--status-color) 25%,transparent),
    inset 0 0 7px color-mix(in srgb,var(--status-color) 28%,transparent)!important;
}

/* จุดกลางเต้นคล้ายชีพจร */
#back-page .tension-item:hover .tension-orb::after{
  animation:tensionOrbCorePulse 1.7s ease-in-out infinite;
}

/* Legend ตอบสนองเบา ๆ เพื่อให้ชุดเอฟเฟกต์ไปในทางเดียวกัน */
#back-page .status-legend{
  transition:border-color .4s ease,box-shadow .4s ease,background .4s ease;
}

#back-page .status-legend:hover{
  border-color:rgba(221,201,143,.25);
  background:rgba(22,13,10,.42);
  box-shadow:
    0 0 16px rgba(185,154,91,.035),
    inset 0 0 14px rgba(185,154,91,.018);
}

#back-page .legend-item{
  transition:color .32s ease,text-shadow .32s ease;
}

#back-page .legend-item:hover{
  color:rgba(234,220,197,.72);
  text-shadow:0 0 8px rgba(221,201,143,.07);
}

/* มือถือ: ใช้กรอบและแสง แต่ตัดการกวาดที่กินทรัพยากร */
@media (max-width:700px){
  #back-page .tension-item{
    padding:24px 10px 27px!important;
  }

  #back-page .tension-item:hover{
    padding-left:10px!important;
  }
}

@media (hover:none),(pointer:coarse){
  #back-page .tension-item::before{
    display:none;
  }
}

@media (prefers-reduced-motion:reduce){
  #back-page .tension-item::before{
    display:none!important;
  }

  #back-page .tension-item,#back-page .tension-item::after,#back-page .tension-orb,#back-page .tension-rule,#back-page .tension-name,#back-page .tension-text{
    animation:none!important;
    transition:none!important;
  }
}
/* ===== END CURRENT COMPLICATIONS — LIVING LEDGER HOVER ===== */
  `;

  const backroomHTML = `
<div id="back-page">
<div aria-hidden="true" class="backroom-cursor-light">
</div>
<div aria-hidden="true" class="backroom-dust-layer">
</div>
<div aria-hidden="true" class="backroom-orbit backroom-orbit-one">
</div>
<div aria-hidden="true" class="backroom-orbit backroom-orbit-two">
</div>
<section class="back-hero">
<div aria-hidden="true" class="seal-clock anim anim-d1">
<span>✦</span>
</div>
<p class="back-eyebrow anim anim-d1">Restricted · For known clients only</p>
<h1 class="back-title">
The
<em>Backroom</em>
<br/>Catalogue</h1>
<p class="back-subtitle anim anim-d3">Botanical extracts of restricted classification · By arrangement only</p>
<div class="warning-strip anim anim-d4">Discretion is assumed · All transactions unrecorded · Deny knowledge if questioned</div>
</section>
<!-- Extract table -->
<div class="extracts-inner">
<div class="extracts-ribbon">
<div aria-hidden="true" class="rose-cluster">ꕤ</div>
<h2>Available Extracts</h2>
</div>
<div class="circle-note">
<p>
<strong>I Circle</strong>— Preparations deemed permissible for discreet trade. Familiar patrons may request these without prior recommendation.</p>
<p>
<strong>II Circle</strong>— Certain flowers within this tier may refuse unfamiliar hands. Orders are reviewed individually.</p>
<p>
<strong>III Circle</strong>— Displayed nowhere openly. Available only through sealed correspondence or prior recommendation.</p>
<p class="circle-small">The Circle system measureth not potency, but permission. Certain flowers refuseth to be gathered for unfamiliar hands.</p>
</div>
<div class="extract-table-header">
<span>Extract</span>
<span>Circle</span>
<span>Effect</span>
<span>Price (per vial)</span>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Moonwake</p>
<p class="ext-source">Moon-fed petals gathered before first dawn · silver-steeped extraction</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">A silver hush laid gently upon the mind and pulse alike. Most patrons report dream-laden sleep, softened grief, and a strange reluctance to wake before dawn.</p>
</div>
<div>
<p class="ext-price">220 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Limited · 4 vials this season</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Gravesilk</p>
<p class="ext-source">Winter lilies and pallid roots bound in linen · sealed against stray virtue</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">The skin grows briefly insensate beneath cloth or guard, while motion remains free. A cold, winterlike touch follows the working.</p>
</div>
<div>
<p class="ext-price">140 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Sold per palm-wrapped bundle</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Velvet Ruin</p>
<p class="ext-source">Dark-garden dew brew’d slow over tender flame for many hours</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">Warmth and ease bloom first, then the body wanes by subtle degrees. Onlookers often mistake the decline for simple fatigue or sorrow.</p>
</div>
<div>
<p class="ext-price">360 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">3 phials per sealed set</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Vespermere</p>
<p class="ext-source">Dusk blossoms harvested at the day’s last bell · sealed close with cool ash</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Agitation is veiled and suspicion quieted, while thought and memory drift into a dim, softened mist.</p>
</div>
<div>
<p class="ext-price">180 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">6 thimbles per moon</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">The Seventh Petal</p>
<p class="ext-source">Origin unrecorded · rite-bound preparation forbidden to the unlearn’d</p>
</div>
<div>
<span class="ext-grade grade-forbidden">Forbidden</span>
</div>
<div>
<p class="ext-effect">Its working shifts with the bearer’s secret will and inward state; no two tellings agree, and no safe doctrine exists for its use.</p>
</div>
<div>
<p class="ext-price">—</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Price withheld by rite</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Saint Mire</p>
<p class="ext-source">Marsh herbs and bitter root steep’d within a milky draught</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">The tongue loosens and hidden truths surface with ease, though the candour often sows discord among companions.</p>
</div>
<div>
<p class="ext-price">160 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per cruet</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Duskroot</p>
<p class="ext-source">Ancient roots lifted at sunset and dry’d in shadow for many nights</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">The mind is roused and need for rest is held at bay, though when the virtue fails, weariness returns manifold.</p>
</div>
<div>
<p class="ext-price">120 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per root braid</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Hushwater</p>
<p class="ext-source">Thrice-filter’d through pale reed, ash, and fine mineral dust</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">Fresh memory blurs by measure and mood, taking words and deeds into a soft forgetting.</p>
</div>
<div>
<p class="ext-price">150 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per stoppered vial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Widow’s Mercy</p>
<p class="ext-source">Slow-grown thorns simmer’d for days and preserv’d with ash</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">Bodily strength fades by slow degrees while the mind stays keen, breeding a quiet and enduring torment.</p>
</div>
<div>
<p class="ext-price">280 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per draught sachet</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Cinder Psalm</p>
<p class="ext-source">Charred resin and funerary herbs wrought chiefly for incense</p>
</div>
<div>
<span class="ext-grade grade-occult">Occult</span>
</div>
<div>
<p class="ext-effect">The smoke unseals visions: prophetic dreams, fervent faith, and claims of speech with the departed, though truth and fancy are hard to divide.</p>
</div>
<div>
<p class="ext-price">240 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per incense cone</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Evermere</p>
<p class="ext-source">Dusk blossoms reduc’d by copper vessels and patient simmer</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Weariness is veiled briefly, including dark rings, red eyes, and pallor; yet the body repays the concealment with heavy fatigue afterward.</p>
</div>
<div>
<p class="ext-price">110 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per ampoule</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Mother Hemlock</p>
<p class="ext-source">Formula and keeping sealed under the shop mistress’s command</p>
</div>
<div>
<span class="ext-grade grade-restricted">Restricted</span>
</div>
<div>
<p class="ext-effect">No sure account remains. Its presence is known only through old inventory sheets and the faintest traveller whispers.</p>
</div>
<div>
<p class="ext-price">—</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Not for common sale</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Winter Thistle</p>
<p class="ext-source">Pure heart gathered beneath the year’s first snow</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">The pulse slows and panic is quelled at once, though prolonged use may leave the mind cold and estranged for many days.</p>
</div>
<div>
<p class="ext-price">130 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per fresh bloom</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Laurel Sanguine</p>
<p class="ext-source">Crimson laurel sap thrice refin’d through a barrier of sharp thorns</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">Feeling is bound with fierce constraint, and many grow protectively fix’d upon the first soul they behold when waking.</p>
</div>
<div>
<p class="ext-price">320 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per crimson ampoule</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Ivory Briar</p>
<p class="ext-source">Wild rose distilled with true silver needles for many nights</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Trembling, fear, and the bodily signs of anxiety are allayed in a soft, dreamlike, and short-lived manner.</p>
</div>
<div>
<p class="ext-price">100 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per vial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Rosethorn Rite</p>
<p class="ext-source">Black rose pollen and ritual wine reduc’d under unmoving heat</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">A swift bond of emotional attachment is woven between two persons, though the wound and yearning after it fades are harsher than the enchantment.</p>
</div>
<div>
<p class="ext-price">420 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Twin-vial binding kit</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Gloaming Poppy</p>
<p class="ext-source">Evening poppy resin pass’d through smoke to stabilize the draught</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">Gentle ecstasy is granted and time feels strange and untrue, making it a favored bloom among poets and musicians.</p>
</div>
<div>
<p class="ext-price">170 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per vial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Saint’s Veil</p>
<p class="ext-source">Pale lilies and cloister herbs rested within a sealed vessel for a full moon cycle</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">The tongue is held in grave restraint, lending persuasion while making deceit difficult to speak.</p>
</div>
<div>
<p class="ext-price">190 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per sealed flask</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Ash Dahlia</p>
<p class="ext-source">A half-burn’d dahlia head bury’d and preserv’d in old graveyard earth</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">The body decays by slow degrees while the outward form remains bright and healthful, making corruption difficult to perceive.</p>
</div>
<div>
<p class="ext-price">260 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per bloom-cask</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Mourning Jasmine</p>
<p class="ext-source">Night-blooming jasmine condens’d in a closed system</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">The spirit is led into lucid dream, senses open to hidden things, and shadowed communion may follow; sleepwalking is common afterward.</p>
</div>
<div>
<p class="ext-price">210 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per nocturne vial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Milkthorn</p>
<p class="ext-source">White milk from the stem gathered before first sunbeam touches the wood</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Bodily pain is numb’d without disturbing motion or reason, making it a favored aid for perilous labor.</p>
</div>
<div>
<p class="ext-price">95 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per dose</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Velour Briar</p>
<p class="ext-source">Dark thorned bloom kept in a vessel lined with thick velvet</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">Joy, pain, and the lightest touch are magnified into vast and overwhelming sensation; some say the heart can scarcely endure it.</p>
</div>
<div>
<p class="ext-price">300 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per blossom</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Rime Marigold</p>
<p class="ext-source">Winter marigold petals preserv’d in icy brine from an ancient glacier</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">Bloodflow slackens and consciousness may be preserved briefly even through grievous wounds.</p>
</div>
<div>
<p class="ext-price">175 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per brine jar</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Belladonna Hymnal</p>
<p class="ext-source">Cultivated in shut chambers and distill’d beneath an ancient temple’s choir loft</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">The soul is carried into profound religious ecstasy, while sweet choral harmonies seem to arise from nowhere.</p>
</div>
<div>
<p class="ext-price">390 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per choir phial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Rue Pallid</p>
<p class="ext-source">Rue ground fine and mix’d with true pearl dust by secret formula</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">The mind sharpens and memory of old knowledge strengthens for many hours.</p>
</div>
<div>
<p class="ext-price">145 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per pearl-dust sachet</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Coffin Orchis</p>
<p class="ext-source">Underground orchid extracted by pressure from intricate rootwork</p>
</div>
<div>
<span class="ext-grade grade-restricted">Restricted</span>
</div>
<div>
<p class="ext-effect">The body enters a stillness so deep it seems life has departed, while thought remains bright within. A watcher is required at all times.</p>
</div>
<div>
<p class="ext-price">—</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Not sold without license</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Elegy Iris</p>
<p class="ext-source">Iris tincture long matur’d in an oak cask once used in mourning rites</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">Grief is drawn from hidden chambers of the heart until the body shows signs one cannot easily command.</p>
</div>
<div>
<p class="ext-price">165 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per tincture vial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Selenite Yew</p>
<p class="ext-source">Yew resin purify’d and made translucent through many crystal layers</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">The sense of time is lengthened beyond its true measure, making minutes feel like hours.</p>
</div>
<div>
<p class="ext-price">155 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per crystal vial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Noctis Paeonia</p>
<p class="ext-source">Midnight peony pollen extract’d in mirrored vessels</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">An unnatural fondness for one’s own image arises, along with fierce satisfaction in appearance.</p>
</div>
<div>
<p class="ext-price">125 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per mirrored bloom</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Ruin Magnolia</p>
<p class="ext-source">Magnolia nectar preserv’d under strict and carefully govern’d conditions</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">Emotional attachment hastens at once while reason weakens, leaving quarrels and duels often in its wake.</p>
</div>
<div>
<p class="ext-price">205 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per nectar flask</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Winter Wisteria</p>
<p class="ext-source">Frozen wisteria stabilized in a dark ice chamber</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Calm judgment and steadfast resolve are foster’d under pressure, fit for those who must keep their wits amid chaos.</p>
</div>
<div>
<p class="ext-price">175 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per cold-set vial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Funeral Camellia</p>
<p class="ext-source">Black camellia oil mingled lightly with farewell incense</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">Emotional response to wounds and death is lessened in a manner most unusual.</p>
</div>
<div>
<p class="ext-price">185 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per rite oil</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Wane Jonquille</p>
<p class="ext-source">Grown beneath mirrored glass and refin’d thrice with exacting care</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Attention turns inward, fix’d upon reflection, countenance, and voice; prolonged use strengthens the compulsion.</p>
</div>
<div>
<p class="ext-price">115 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per reflection drop</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Flos Viviea</p>
<p class="ext-source">Rare bloom from the body of an elemental mage · unlawful to cultivate</p>
</div>
<div>
<span class="ext-grade grade-illicit">Illicit</span>
</div>
<div>
<p class="ext-effect">Violently stimulates nerve and muscle response; overuse may bring sudden heart failure and death.</p>
</div>
<div>
<p class="ext-price">520 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per emergency ampoule</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Sexus Velle</p>
<p class="ext-source">Deep violet bloom of the northern reaches · heavily controlled and smuggled</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">Emotions and bodily responses are heightened, with stronger feeling and sharper sensitivity to surrounding stimuli.</p>
</div>
<div>
<p class="ext-price">260 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per pollen bundle</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Beru Beru</p>
<p class="ext-source">Small bright-blue flower found by waterfalls and strong streams</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Best known for healing harms tied to water-elemental power, though its workings remain strange and hard to foretell.</p>
</div>
<div>
<p class="ext-price">135 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per blue blossom</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Geogia Tuis</p>
<p class="ext-source">Drought-hardy tropical bloom used in spiritual rites and magic</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Fresh scent quiets the mind and lessens emotional unrest; concentrated extract shows mild to moderate sedative virtue.</p>
</div>
<div>
<p class="ext-price">120 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per ritual sprig</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Purus Bloem</p>
<p class="ext-source">Translucent white blossom with root-only true extraction</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Gentle relaxation softens the heart’s guard, and root extract is widely used to ease bodily discomfort in women.</p>
</div>
<div>
<p class="ext-price">105 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per root extract</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Fuchsia Ella</p>
<p class="ext-source">Bloom found near cooled magma and remnants of earth-and-fire wielders</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">Vigor, alertness, and emotional sharpness are increased; the scent recalls earth after the season’s first rain.</p>
</div>
<div>
<p class="ext-price">190 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per ember bloom</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Tenebris Velle</p>
<p class="ext-source">Night-without-stars bloom · petals drinking light against nature</p>
</div>
<div>
<span class="ext-grade grade-iii">III Circle</span>
</div>
<div>
<p class="ext-effect">Bodily response and resistance are lessened without full unconsciousness, like sinking into silence.</p>
</div>
<div>
<p class="ext-price">310 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per night-shade phial</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Velaris</p>
<p class="ext-source">Rootless blossom borne aloft by wind and moisture</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">Brew’d with rainwater, it alters time perception so a short span may feel greatly prolong’d, often leaving fatigue afterward.</p>
</div>
<div>
<p class="ext-price">200 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per rain brew</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Eirwen</p>
<p class="ext-source">Flower from far northern ice mountains that never melt</p>
</div>
<div>
<span class="ext-grade grade-i">I Circle</span>
</div>
<div>
<p class="ext-effect">Outward use stops bleeding and numbs a small area; inward use may briefly hinder access to short-term memory.</p>
</div>
<div>
<p class="ext-price">115 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per frost petal</p>
</div>
</div>
<div class="extract-row">
<div>
<p class="ext-name">Lascivia</p>
<p class="ext-source">Deep red bloom with moving petals and viscous moisture ever gather’d upon it</p>
</div>
<div>
<span class="ext-grade grade-ii">II Circle</span>
</div>
<div>
<p class="ext-effect">It quells bodily urges and governs certain appetites, though scholars dispute the limits of prolonged use.</p>
</div>
<div>
<p class="ext-price">180 DNS</p>
<p style="font-size:11px; color:rgba(200,184,150,0.3); margin-top:3px; letter-spacing:.05em;">Per deep-red bloom</p>
</div>
</div>
</div>
<!-- Ledger notes -->
<section class="ledger-section">
<div class="ledger-block">
<h3 class="ledger-title">The Bloom Ledger</h3>
<p class="ledger-body">
All transactions are recorded in a proprietary notation system, written in
<em>elemental ink</em>
— visible only under sustained fire-weave light. The ledger is stored beneath the third floorboard from the east wall, behind the pressing cabinet.
<br/>
<br/>
Entries include
<strong>client pseudonyms, extract type, volume, and delivery method</strong>. No real names. The florist does not need them. She remembers faces.</p>
</div>
<div class="ledger-block red-ledger">
<h3 class="ledger-title">Notes on Certain Rootwork</h3>
<p class="ledger-body">
Certain extracts cannot be obtained through conventional botanical practice alone. Preparations marked as
<em>elemental-assisted</em>
require conditions not reproducible by ordinary cultivation or laboratory methods. The proprietress does not disclose her process. Availability remains dependent upon the condition and disposition of the source material at time of harvest.
<strong>Some commissions may therefore be declined without further explanation.</strong>
<p>*The deposit is non-refundable.</p>
</p>
</div>
</section>
<!-- Active tensions -->
<section class="tension-section" id="complications">
<h2 class="tension-title">Current Complications</h2>
<div class="status-legend">
<div class="legend-item">
<span class="dot critical"></span>
<span>Under Scrutiny — Immediate Concern</span>
</div>
<div class="legend-item">
<span class="dot warning"></span>
<span>Limited Review — Requires Attention</span>
</div>
<div class="legend-item">
<span class="dot stable"></span>
<span>Contained — Under Observation</span>
</div>
</div>
<div class="tension-item tension-critical">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Moonwake — Exposure Risk</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">A long-enduring patron hath purchas’d the preparation upon seven several occasions these two years past. Lately, a second intermediary hath arriv’d with questions that mirror the first. Further discourse is kept to a whisper, until intent be made plain.</p>
</div>
<div class="tension-item tension-warning">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Coffin Orchis — Inquiry</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">Independent mage-investigators do trace compounds that answer not unto any known record of cultivation. They abide patient, methodical, and ever harder to turn aside from their course.</p>
</div>
<div class="tension-item tension-stable">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Winter Wisteria — Shortage</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">Frost-wound hath cut this season’s bloom-count by near the half. Several standing patrons are like to receive not their wonted share.</p>
</div>
<div class="tension-item tension-critical">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Rosethorn Rite — Improper Use</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">Reports do speak of a diluted counterfeit abroad amongst the noble districts. One receiver fell into an obsessive attachment that linger’d beyond the term appointed.</p>
</div>
<div class="tension-item tension-stable">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Rue Pallid — Contamination</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">Two late batches did show strange bitterness, with an excess of sharpen’d wit and thought. The stock is isolated, pending assay beneath fire-weave light.</p>
</div>
<div class="tension-item tension-warning">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Mourning Jasmine — Demand Increase</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">The funeral districts continue to ask quantities beyond the bounds of sustainable gathering. More must needs be sought beyond the eastern marsh-routes.</p>
</div>
<div class="tension-item tension-warning">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Belladonna Hymnal — Restrictions</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">The ecclesiastical authorities have renew’d their inquiry concerning compounds touch’d by auditory visions and devotional unrest. Open carriage is no longer advis’d.</p>
</div>
<div class="tension-item tension-warning">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Evermere — Weariness Mask</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">Repeated requests now do exceed the season’s store. Diverse patrons ask for larger measures than erstwhile, seeking naught save the brief concealment it doth bestow.</p>
</div>
<div class="tension-item tension-warning">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Hushwater — Memory Drift</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">Small discordances have appear’d in recent accounts after private tastings. Notes taken within the hour no longer match the selfsame events by nightfall.</p>
</div>
<div class="tension-item tension-critical">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Laurel Sanguine — Attachment Residue</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">A few receivers have reported a fixation most persistent, even after the effect hath pass’d. The matter is handled softly, lest notice be drawn.</p>
</div>
<div class="tension-item tension-critical">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Flos Viviea — Unsafe Demand</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">Interest hath increas’d among those that seek swift vitality despite the known perils. Distribution is held beneath stricter lock and seal.</p>
</div>
<div class="tension-item tension-warning">
<div class="tension-heading">
<span aria-hidden="true" class="tension-orb"></span>
<p class="tension-name">Lascivia — Appetite Quiet</p>
</div>
<div aria-hidden="true" class="tension-rule"></div>
<p class="tension-text">Requests for the bloom have risen among patrons that seek restraint rather than indulgence. Several houses now keep it seal’d for private use, praising its steadier governance of bodily urge.</p>
</div>
</section>
<!-- Footer back -->
<footer class="footer-back">
<p class="footer-back-text">This record does not exist. Neither, officially, does this room.</p>
<button class="back-btn" onclick="exitBackroom()">← Return to shop floor</button>
</footer>
</div>
  `;

  const style = document.createElement("style");
  style.id = "florencia-backroom-styles";
  style.textContent = backroomCSS;
  document.head.appendChild(style);

  const template = document.createElement("template");
  template.innerHTML = backroomHTML.trim();

  const backroom = template.content.firstElementChild;
  const firstScript = document.body.querySelector("script");

  if (firstScript) {
    document.body.insertBefore(backroom, firstScript);
  } else {
    document.body.appendChild(backroom);
  }
})();
