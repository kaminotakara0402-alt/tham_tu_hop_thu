# tham_tu_hop_thu
Thám tử hộp thư
<!doctype html>
<html lang="vi">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<style>:root{color-scheme:light;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}[hidden]{display:none!important}</style>
<title>Thám Tử Hộp Thư</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@400;500;600;700;800&family=JetBrains+Mono:wght@400;700;800&display=swap">
<style>
/* Bố cục: hộp thư làm trục. Thanh trên màu ink, thân trang nền sương, thư là thẻ trắng.
   Ba lớp kiểm tra có ba màu riêng (xanh ngọc, hổ phách, xanh đen) dùng nhất quán ở mọi nơi. */
:root {
  --bg: #EEF2F6; --surface: #FFFFFF; --surface2: #F4F7FA; --fg: #12263F; --muted: #51647A; --line: #D3DCE6;
  --teal: #0F8B8D; --teal-s: #0B7476; --on-teal: #FFFFFF; --amber: #F2A541; --amber-s: #8A5400;
  --scam: #C8433F; --scam-bg: #FBECEB; --safe: #2E8B57; --safe-bg: #E6F4EC; --unsure: #A86A0A; --unsure-bg: #FBF1DE;
  --l1: #0F8B8D; --l1-bg: #DDF2F2; --l2: #D98A12; --l2-bg: #FDEFD5; --l3: #12263F; --l3-bg: #E1E8F1;
  --link: #1B5FAA; --top: #12263F; --on-top: #EAF1F8; --focus: #1B5FAA;
  --shadow: 0 1px 2px rgba(18,38,63,.08), 0 6px 18px rgba(18,38,63,.06);
  --font: 'Be Vietnam Pro', system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  --mono: 'JetBrains Mono', ui-monospace, 'SF Mono', Menlo, Consolas, 'DejaVu Sans Mono', monospace;
}
@media (prefers-color-scheme: dark) { :root:not([data-theme="light"]) { --bg: #0D1620; --surface: #152331; --surface2: #1B2C3D; --fg: #E7EEF6; --muted: #9FB1C4; --line: #2A3D50;
  --teal: #3CBABC; --teal-s: #35B3B5; --on-teal: #06242A; --amber: #F2A541; --amber-s: #F2B45E;
  --scam: #EA7A75; --scam-bg: #3A1E22; --safe: #5CC48C; --safe-bg: #173226; --unsure: #E5A94A; --unsure-bg: #382C14;
  --l1: #3CBABC; --l1-bg: #14393D; --l2: #F2A541; --l2-bg: #3A2D12; --l3: #9DB6D9; --l3-bg: #1E2F44;
  --link: #7FB2F0; --top: #091119; --on-top: #E7EEF6; --focus: #7FB2F0; --shadow: 0 1px 2px rgba(0,0,0,.4); color-scheme: dark; } }
:root[data-theme="dark"] { --bg: #0D1620; --surface: #152331; --surface2: #1B2C3D; --fg: #E7EEF6; --muted: #9FB1C4; --line: #2A3D50;
  --teal: #3CBABC; --teal-s: #35B3B5; --on-teal: #06242A; --amber: #F2A541; --amber-s: #F2B45E;
  --scam: #EA7A75; --scam-bg: #3A1E22; --safe: #5CC48C; --safe-bg: #173226; --unsure: #E5A94A; --unsure-bg: #382C14;
  --l1: #3CBABC; --l1-bg: #14393D; --l2: #F2A541; --l2-bg: #3A2D12; --l3: #9DB6D9; --l3-bg: #1E2F44;
  --link: #7FB2F0; --top: #091119; --on-top: #E7EEF6; --focus: #7FB2F0; --shadow: 0 1px 2px rgba(0,0,0,.4); color-scheme: dark; }

*, *::before, *::after { box-sizing: border-box; }
html { -webkit-text-size-adjust: 100%; }
body { margin: 0; background: var(--bg); color: var(--fg); font: 400 16px/1.6 var(--font); -webkit-font-smoothing: antialiased; }
body::before { content: ""; position: fixed; inset: 0 0 auto; height: env(safe-area-inset-top, 0px); background: var(--top); z-index: 30; }
h1, h2, h3, h4 { margin: 0; line-height: 1.25; text-wrap: balance; letter-spacing: -0.01em; }
h1 { font-size: clamp(1.7rem, 3.4vw, 2.4rem); font-weight: 800; }
h2 { font-size: 1.3rem; font-weight: 700; }
h3 { font-size: 1.05rem; font-weight: 700; }
h4 { font-size: 1rem; font-weight: 600; }
p { margin: 0; }
ul, ol { margin: 0; padding-left: 1.25em; }
li + li { margin-top: .3em; }
ul.plain { list-style: none; padding: 0; }
ul.plain li { padding-left: 0; }
button { font: inherit; color: inherit; }
code, .mono { font-family: var(--mono); font-size: .9em; }
.sm { font-size: 12.5px; }
.muted { color: var(--muted); }
.small { font-size: 14px; }
q { quotes: none; }
q::before { content: "“"; } q::after { content: "”"; }
:focus-visible { outline: 3px solid var(--focus); outline-offset: 2px; border-radius: 4px; }
.sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }
.ghost { position: fixed; left: -9999px; top: 0; }

.wrap { width: 100%; max-width: 1200px; margin-inline: auto; padding-left: max(16px, env(safe-area-inset-left, 0px)); padding-right: max(16px, env(safe-area-inset-right, 0px)); }
.main { padding-block: 28px 56px; outline: none; }
.stack { display: flex; flex-direction: column; gap: 14px; min-width: 0; }
.stack.lg { gap: 22px; }
.stack.xl { gap: 40px; }
.row { display: flex; align-items: center; gap: 10px; min-width: 0; }
.row.gap { gap: 10px; }
.row.spread { justify-content: space-between; }
.wrap-row { flex-wrap: wrap; }
.grid2 { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 14px; }
.two { display: grid; grid-template-columns: minmax(0, 1fr) minmax(0, 1fr); gap: 22px; align-items: start; }
.two > * { min-width: 0; }
.sticky-left > :first-child { position: sticky; top: calc(env(safe-area-inset-top, 0px) + 72px); }
@media (max-width: 880px) { .two, .grid2 { grid-template-columns: minmax(0, 1fr); } .sticky-left > :first-child { position: static; } }

/* ---- thanh trên và các chặng ---- */
.topbar { position: sticky; top: env(safe-area-inset-top, 0px); z-index: 20; background: var(--top); color: var(--on-top); }
.topbar-in { display: flex; align-items: center; justify-content: space-between; gap: 8px 16px; flex-wrap: wrap; min-height: 56px; padding-block: 6px; }
.brand { display: flex; align-items: center; gap: 10px; background: none; border: 0; color: inherit; cursor: pointer; padding: 4px 0; text-align: left; }
.logo { color: var(--on-top); display: inline-flex; }
.brand-t { display: flex; flex-direction: column; line-height: 1.15; }
.brand-t b { font-size: 1.05rem; font-weight: 800; letter-spacing: -0.01em; }
.brand-t small { font-size: 11.5px; letter-spacing: .08em; text-transform: uppercase; opacity: .75; }
.topnav { display: flex; gap: 4px; flex-wrap: wrap; }
.tnav { background: none; border: 0; color: var(--on-top); padding: 8px 12px; border-radius: 8px; font-size: 14px; font-weight: 500; cursor: pointer; opacity: .88; }
.tnav:hover, .tnav.on { background: rgba(255,255,255,.12); opacity: 1; }
.stepper { background: var(--surface); border-bottom: 1px solid var(--line); position: sticky; top: calc(env(safe-area-inset-top, 0px) + 56px); z-index: 15; }
.stepper-in { display: flex; gap: 8px; overflow-x: auto; padding-block: 10px; scrollbar-width: thin; }
.step { display: inline-flex; align-items: center; gap: 8px; white-space: nowrap; padding: 6px 12px 6px 6px; border-radius: 999px; border: 1.5px solid var(--line); background: var(--surface2); font-size: 13.5px; font-weight: 600; cursor: pointer; flex: none; }
.step .num { width: 24px; height: 24px; border-radius: 50%; display: inline-grid; place-items: center; background: var(--line); color: var(--fg); font-size: 12.5px; font-weight: 700; }
.step small { color: var(--muted); font-weight: 500; }
.step.skip { opacity: .65; border-style: dashed; }
.step.cur { background: var(--top); color: var(--on-top); border-color: var(--top); opacity: 1; }
.step.cur small { color: var(--on-top); opacity: .75; }
.step.cur .num { background: var(--amber); color: #12263F; }
.step.done .num { background: var(--safe); color: #fff; }
@media (max-width: 640px) { .topbar, .stepper { position: static; } .brand-t small { display: none; } .tnav { padding: 8px 9px; font-size: 13.5px; } }
.foot { border-top: 1px solid var(--line); padding-block: 22px calc(22px + env(safe-area-inset-bottom, 0px)); color: var(--muted); font-size: 13px; }
.foot p + p { margin-top: 4px; }

/* ---- nút, chip, trường nhập ---- */
.btn { appearance: none; border: 2px solid var(--teal-s); background: var(--teal-s); color: var(--on-teal); font-weight: 600; font-size: 15px; line-height: 1.2; padding: 10px 18px; border-radius: 10px; cursor: pointer; }
.btn:hover:not(:disabled) { filter: brightness(1.08); }
.btn.big { padding: 13px 22px; font-size: 16px; }
.btn.sec { background: transparent; color: var(--fg); border-color: var(--line); }
.btn.sec:hover:not(:disabled) { border-color: var(--teal-s); filter: none; }
.btn.ghost { background: var(--surface2); color: var(--fg); border-color: var(--surface2); }
.btn.danger { background: var(--scam); border-color: var(--scam); color: #fff; }
.btn:disabled, .vbtn:disabled, .chip:disabled, .sbtn:disabled { cursor: not-allowed; }
.btn:disabled { opacity: .45; }
.linkbtn { background: none; border: 0; padding: 0; color: var(--link); text-decoration: underline; cursor: pointer; font-size: 13px; }
.chips { display: flex; flex-wrap: wrap; gap: 8px; }
.chips.col { flex-direction: column; align-items: stretch; }
.chip { display: inline-flex; align-items: center; gap: 6px; border: 1.5px solid var(--line); background: var(--surface); color: var(--fg); padding: 7px 13px; border-radius: 999px; font-size: 14px; line-height: 1.35; cursor: pointer; text-align: left; }
.chip.col, .chips.col .chip { border-radius: 12px; }
.chip.small { font-size: 13px; padding: 5px 10px; }
.chip.big { font-size: 15px; padding: 10px 16px; }
.chip:hover:not(:disabled) { border-color: var(--teal-s); }
.chip[aria-pressed="true"], .chip.on { border-color: var(--teal-s); background: var(--l1-bg); box-shadow: inset 0 0 0 1px var(--teal-s); font-weight: 600; }
.chip.hit { border-color: var(--safe); background: var(--safe-bg); box-shadow: inset 0 0 0 1px var(--safe); }
.chip.extra { border-color: var(--scam); background: var(--scam-bg); box-shadow: inset 0 0 0 1px var(--scam); }
.chip.miss { border: 1.5px dashed var(--unsure); background: var(--unsure-bg); }
.cmark { font-weight: 800; }
.in { width: 100%; font: 400 15px/1.5 var(--font); color: var(--fg); background: var(--surface); border: 1.5px solid var(--line); border-radius: 10px; padding: 10px 12px; }
textarea.in { resize: vertical; min-height: 44px; }
.mono-in { font-family: var(--mono); font-size: 13px; }
.field { display: flex; flex-direction: column; gap: 6px; min-width: 0; }
.flabel { font-size: 14px; font-weight: 600; }
.fhint { font-size: 13px; color: var(--muted); }

/* ---- thẻ, tiêu đề trang ---- */
.card { background: var(--surface); border: 1px solid var(--line); border-radius: 14px; padding: 20px; box-shadow: var(--shadow); min-width: 0; }
.card.ok { border-color: var(--safe); } .card.bad { border-color: var(--scam); }
.phead { display: flex; flex-direction: column; gap: 8px; max-width: 78ch; }
.eyebrow { font-size: 12.5px; font-weight: 700; letter-spacing: .09em; text-transform: uppercase; color: var(--teal-s); }
.lead { font-size: 1.1rem; color: var(--fg); }
.why { background: var(--surface); border: 1px solid var(--line); border-radius: 10px; padding: 10px 14px; font-size: 14.5px; }
.why summary { cursor: pointer; font-weight: 600; }
.why p { margin-top: 8px; }
.note-ok { color: var(--safe); font-weight: 600; }
.note-warn { color: var(--scam); font-weight: 500; }
.note-warn-box { background: var(--unsure-bg); border-color: var(--unsure); }
.tip { background: var(--l1-bg); border-radius: 8px; padding: 10px 12px; }
.tag { display: inline-block; font-size: 12px; font-weight: 700; padding: 2px 8px; border-radius: 6px; background: var(--surface2); color: var(--muted); width: fit-content; }
.stats { display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr)); gap: 12px; }
.stat { background: var(--surface2); border-radius: 10px; padding: 12px 14px; display: flex; flex-direction: column; }
.stat b { font-size: 1.6rem; font-weight: 800; font-variant-numeric: tabular-nums; }
.stat span { font-size: 13px; color: var(--muted); }
.prog { position: relative; background: var(--line); border-radius: 999px; height: 26px; overflow: hidden; }
.prog .bar { position: absolute; inset: 0 auto 0 0; background: var(--teal); transition: width .3s; }
.prog span { position: relative; display: block; text-align: center; font-size: 13px; font-weight: 700; line-height: 26px; color: var(--fg); mix-blend-mode: normal; }

/* ---- trạng thái, kết luận ---- */
.vtag { display: inline-flex; gap: 6px; align-items: center; font-weight: 700; font-size: 13.5px; padding: 3px 10px; border-radius: 999px; border: 1.5px solid currentColor; white-space: nowrap; }
.vtag.v-scam { color: var(--scam); background: var(--scam-bg); } .vtag.v-real { color: var(--safe); background: var(--safe-bg); } .vtag.v-unsure { color: var(--unsure); background: var(--unsure-bg); }
.stbadge { display: inline-flex; align-items: center; gap: 6px; font-weight: 700; font-size: 13.5px; width: fit-content; }
.st-ok { color: var(--safe); } .st-bad { color: var(--scam); } .st-warn { color: var(--unsure); } .st-na { color: var(--muted); }
.vrow { display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 10px; }
@media (max-width: 560px) { .vrow { grid-template-columns: minmax(0, 1fr); } }
.vbtn { display: flex; align-items: center; justify-content: center; gap: 10px; padding: 14px 10px; border: 2px solid var(--line); background: var(--surface); border-radius: 12px; font-weight: 600; font-size: 15px; cursor: pointer; text-align: center; flex-wrap: wrap; }
.vbtn .vi { width: 26px; height: 26px; border-radius: 50%; display: inline-grid; place-items: center; font-weight: 800; background: var(--surface2); }
.vbtn em { font-style: normal; font-size: 12px; font-weight: 700; padding: 1px 8px; border-radius: 6px; background: var(--safe); color: #fff; }
.vbtn:hover:not(:disabled) { border-color: var(--teal-s); }
.vbtn.sel.v-scam { border-color: var(--scam); background: var(--scam-bg); } .vbtn.sel.v-scam .vi { background: var(--scam); color: #fff; }
.vbtn.sel.v-real { border-color: var(--safe); background: var(--safe-bg); } .vbtn.sel.v-real .vi { background: var(--safe); color: #fff; }
.vbtn.sel.v-unsure { border-color: var(--unsure); background: var(--unsure-bg); } .vbtn.sel.v-unsure .vi { background: var(--unsure); color: #fff; }
.vbtn.sel:not(.v-scam):not(.v-real):not(.v-unsure) { border-color: var(--teal-s); background: var(--l1-bg); }
.vbtn.truth { box-shadow: 0 0 0 3px var(--safe); }
.vbtn.wrong { border-color: var(--scam); background: var(--scam-bg); text-decoration: line-through; text-decoration-thickness: 1.5px; }
.spick { display: flex; flex-wrap: wrap; gap: 8px; }
.sbtn { border: 1.5px solid var(--line); background: var(--surface); border-radius: 999px; padding: 7px 13px; font-size: 14px; font-weight: 600; cursor: pointer; }
.sbtn.sel { box-shadow: inset 0 0 0 1px currentColor; background: var(--surface2); border-color: currentColor; }
.sbtn.st-ok.sel { background: var(--safe-bg); } .sbtn.st-bad.sel { background: var(--scam-bg); } .sbtn.st-warn.sel { background: var(--unsure-bg); }

/* ---- ba lớp ---- */
.lcards { display: grid; grid-template-columns: repeat(auto-fit, minmax(230px, 1fr)); gap: 12px; }
.lcards.one { grid-template-columns: minmax(0, 1fr); }
.lcard { border: 1px solid var(--line); border-radius: 12px; overflow: hidden; background: var(--surface); min-width: 0; --lc: var(--l1); --lb: var(--l1-bg); }
.lcard.l-link { --lc: var(--l2); --lb: var(--l2-bg); } .lcard.l-content { --lc: var(--l3); --lb: var(--l3-bg); }
.lhead { display: flex; align-items: center; gap: 10px; padding: 9px 14px; background: var(--lb); }
.lnum { width: 24px; height: 24px; border-radius: 50%; display: inline-grid; place-items: center; background: var(--lc); color: #fff; font-weight: 800; font-size: 13px; flex: none; }
.lcard.l-link .lnum { color: #12263F; }
.lbody { padding: 12px 14px; display: flex; flex-direction: column; gap: 8px; }
.lq { color: var(--muted); font-size: 14px; }
.lcard.given { opacity: .92; } .lcard.mine { border-width: 2px; border-color: var(--lc); }
.sgroup { display: flex; flex-direction: column; gap: 6px; }
.sg-name { font-size: 12.5px; font-weight: 700; letter-spacing: .06em; text-transform: uppercase; color: var(--muted); }
.sgroup.l-sender .sg-name { color: var(--l1); } .sgroup.l-link .sg-name { color: var(--l2); }
.tabs { display: flex; gap: 6px; overflow-x: auto; padding-bottom: 4px; }
.tab { flex: none; border: 1.5px solid var(--line); background: var(--surface); border-radius: 10px; padding: 8px 14px; font-size: 14px; font-weight: 600; cursor: pointer; white-space: nowrap; }
.tab.cur { background: var(--top); color: var(--on-top); border-color: var(--top); }
.tab.done:not(.cur)::after, .tab.seen:not(.cur)::after { content: " ✓"; color: var(--safe); }
.tabs.small .tab { padding: 6px 12px; font-size: 13.5px; }
.tab.l-sender.cur { background: var(--l1); border-color: var(--l1); color: #fff; } .tab.l-link.cur { background: var(--l2); border-color: var(--l2); color: #12263F; } .tab.l-content.cur { background: var(--l3); border-color: var(--l3); color: var(--bg); }
.evline { font-size: 14px; background: var(--surface2); padding: 8px 10px; border-radius: 8px; }
.hints { display: flex; flex-direction: column; gap: 8px; align-items: flex-start; }
.hintlist { background: var(--unsure-bg); border-radius: 10px; padding: 10px 12px 10px 30px; font-size: 14.5px; width: 100%; }

/* ---- thư ---- */
.mail { background: var(--surface); border: 1px solid var(--line); border-radius: 14px; box-shadow: var(--shadow); overflow: hidden; min-width: 0; }
.mail-head { display: flex; gap: 12px; padding: 16px 18px 0; }
.avatar { width: 40px; height: 40px; border-radius: 50%; color: #fff; display: grid; place-items: center; font-weight: 700; flex: none; }
.mail-from { min-width: 0; flex: 1; display: flex; flex-direction: column; gap: 2px; }
.who-row { display: flex; justify-content: space-between; gap: 10px; flex-wrap: wrap; }
.who { font-weight: 700; }
.time, .to { color: var(--muted); font-size: 13px; }
.addr { font-family: var(--mono); font-size: 13px; word-break: break-all; }
.addr-row { min-height: 20px; }
.subject { padding: 10px 18px 2px; font-size: 1.15rem; }
.ctx { margin: 8px 18px 0; padding: 8px 12px; background: var(--l1-bg); border-radius: 8px; font-size: 14px; font-style: italic; }
.mail-body { padding: 10px 18px 16px; }
.mail-body p { margin-bottom: .75em; }
.mail-body p:last-child { margin-bottom: 0; }
.mlink { color: var(--link); text-decoration: underline; cursor: pointer; }
.ph { border-radius: 3px; }
.show-ph .ph { background: var(--l3-bg); box-shadow: 0 0 0 2px var(--l3-bg); }
.atts { padding: 0 18px 14px; display: flex; gap: 8px; flex-wrap: wrap; }
.att { border: 1.5px solid var(--line); background: var(--surface2); border-radius: 8px; padding: 6px 10px; font-size: 14px; cursor: pointer; }
.mstatus { border-top: 1px solid var(--line); background: var(--surface2); font: 13px/1.5 var(--font); padding: 8px 18px; color: var(--muted); min-height: 38px; word-break: break-all; }
.mstatus.on { color: var(--fg); background: var(--l2-bg); font-family: var(--mono); font-size: 12.5px; }
.ev-on [data-ev] { cursor: crosshair; }
.ev-on [data-ev]:hover { outline: 2px dashed var(--teal); outline-offset: 1px; }
.mail [data-ev].picked { outline: 2px solid var(--teal); outline-offset: 1px; background: var(--l1-bg); }
.mail[data-hl="sender"] [data-ev="sender"] { background: var(--l1-bg); box-shadow: 0 0 0 3px var(--l1-bg), 0 0 0 5px var(--l1); border-radius: 3px; }
.mail[data-hl="link"] [data-ev="link"] { background: var(--l2-bg); box-shadow: 0 0 0 3px var(--l2-bg), 0 0 0 5px var(--l2); border-radius: 3px; }
.mail[data-hl="content"] .ph { background: var(--l3-bg); box-shadow: 0 0 0 3px var(--l3-bg), 0 0 0 5px var(--l3); }
.annot [data-n] { position: relative; }
.annot [data-n]::after { content: attr(data-n); position: absolute; top: -11px; right: -9px; width: 19px; height: 19px; border-radius: 50%; background: var(--l3); color: #fff; font: 700 11px/19px var(--font); text-align: center; }
.annot .addr[data-n] { box-shadow: 0 0 0 2px var(--l1); border-radius: 3px; } .annot .addr[data-n]::after { background: var(--l1); }
.annot .mlink[data-n] { box-shadow: 0 0 0 2px var(--l2); border-radius: 3px; } .annot .mlink[data-n]::after { background: var(--l2); color: #12263F; }
.annot .ph[data-n] { box-shadow: 0 0 0 2px var(--l3); }
.legend { list-style: none; padding: 0; display: flex; flex-direction: column; gap: 8px; font-size: 14px; }
.legend li { display: flex; gap: 10px; align-items: flex-start; margin: 0; }
.legend .l-link .lnum { background: var(--l2); color: #12263F; } .legend .l-sender .lnum { background: var(--l1); } .legend .l-content .lnum { background: var(--l3); color: var(--bg); }

/* ---- hộp thư Chặng 1 ---- */
.box { display: grid; grid-template-columns: minmax(220px, 280px) minmax(0, 1fr); gap: 20px; align-items: start; }
@media (max-width: 880px) { .box { grid-template-columns: minmax(0, 1fr); } }
.mlist { display: flex; flex-direction: column; gap: 6px; position: sticky; top: calc(env(safe-area-inset-top, 0px) + 132px); max-height: calc(100vh - 160px); overflow-y: auto; }
@media (max-width: 880px) { .mlist { flex-direction: row; overflow-x: auto; position: static; max-height: none; padding-bottom: 6px; } .mitem { min-width: 190px; } }
.mitem { display: flex; gap: 10px; align-items: center; text-align: left; border: 1.5px solid var(--line); background: var(--surface); border-radius: 10px; padding: 9px 11px; cursor: pointer; flex: none; }
.mitem.cur { border-color: var(--teal-s); box-shadow: inset 0 0 0 1px var(--teal-s); }
.mitem.ok .mi-n { background: var(--safe); color: #fff; } .mitem.bad .mi-n { background: var(--scam); color: #fff; }
.mi-n { width: 26px; height: 26px; border-radius: 50%; background: var(--surface2); display: grid; place-items: center; font-weight: 700; font-size: 13px; flex: none; }
.mi-t { display: flex; flex-direction: column; min-width: 0; }
.mi-t b { font-size: 13.5px; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
.mi-t small { color: var(--muted); white-space: nowrap; overflow: hidden; text-overflow: ellipsis; font-size: 12.5px; }
.fb-head { display: flex; gap: 12px; align-items: center; }
.fb-ic { width: 40px; height: 40px; border-radius: 50%; display: grid; place-items: center; font-weight: 800; font-size: 1.2rem; color: #fff; flex: none; }
.fb.ok .fb-ic { background: var(--safe); } .fb.bad .fb-ic { background: var(--scam); }
.tcase { gap: 14px; }

/* ---- bảng ---- */
.tblwrap { overflow-x: auto; }
.tbl { border-collapse: collapse; width: 100%; font-size: 14px; }
.tbl th, .tbl td { padding: 8px 10px; border-bottom: 1px solid var(--line); text-align: left; vertical-align: top; }
.tbl th { background: var(--surface2); font-weight: 700; white-space: nowrap; }
.tbl.cm td { text-align: center; font-variant-numeric: tabular-nums; } .tbl.cm td.nz { font-weight: 800; background: var(--l1-bg); }

/* ---- trang chủ ---- */
.hero { display: grid; grid-template-columns: minmax(0, 1.05fr) minmax(0, .95fr); gap: 36px; align-items: center; }
@media (max-width: 880px) { .hero { grid-template-columns: minmax(0, 1fr); } }
.hero h1 { font-size: clamp(2.3rem, 6vw, 3.9rem); font-weight: 800; letter-spacing: -0.025em; line-height: 1.05; }
.hero-mail { padding: 14px 10px 0 4px; }
.opts { display: flex; flex-direction: column; gap: 14px; }
.opt { display: flex; flex-wrap: wrap; align-items: center; gap: 8px 10px; }
.olabel { font-size: 13px; font-weight: 700; letter-spacing: .06em; text-transform: uppercase; color: var(--muted); min-width: 110px; }
.pcards { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 14px; }
.pcard { display: flex; flex-direction: column; gap: 8px; text-align: left; background: var(--surface); border: 2px solid var(--line); border-radius: 14px; padding: 18px; cursor: pointer; box-shadow: var(--shadow); }
.pcard:hover { border-color: var(--teal-s); }
.pcard b { font-size: 1.15rem; } .pcard span { color: var(--muted); font-size: 14.5px; } .pcard small { color: var(--teal-s); font-weight: 700; margin-top: auto; }
.split { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 18px; }
@media (max-width: 880px) { .split { grid-template-columns: minmax(0, 1fr); } }

/* ---- nguồn, phản biện, kết quả ---- */
.srcgrid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 14px; }
.srccard { border: 1px solid var(--line); border-radius: 12px; padding: 14px; background: var(--surface2); display: flex; flex-direction: column; gap: 8px; min-width: 0; }
.srccard dl { margin: 0; display: flex; flex-direction: column; gap: 6px; font-size: 14px; }
.srccard dt { font-size: 12px; font-weight: 700; color: var(--muted); text-transform: uppercase; letter-spacing: .05em; }
.srccard dd { margin: 0; }
.tr { width: fit-content; font-weight: 700; font-size: 13px; padding: 3px 10px; border-radius: 999px; }
.tr-high { background: var(--safe-bg); color: var(--safe); } .tr-mid { background: var(--unsure-bg); color: var(--unsure); } .tr-low { background: var(--scam-bg); color: var(--scam); }
.crit { border-top: 1px solid var(--line); padding-top: 14px; }
.cert { border-width: 2px; border-color: var(--top); }
.off { gap: 12px; }
.setup summary { cursor: pointer; font-weight: 700; }
.setup .grid2 { margin-top: 12px; }
.meta { display: grid; grid-template-columns: 160px minmax(0, 1fr); gap: 8px 16px; margin: 0; }
.meta dt { font-weight: 700; } .meta dd { margin: 0; }
@media (max-width: 640px) { .meta { grid-template-columns: minmax(0, 1fr); } }
.gloss { margin: 0; } .gloss dt { font-weight: 700; margin-top: 8px; } .gloss dd { margin: 2px 0 0; color: var(--muted); }
.refs { font-size: 14px; } .refs li { overflow-wrap: anywhere; }

/* ---- kho thư, giảng viên ---- */
.libgrid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 12px; }
.libcard { display: grid; grid-template-columns: auto minmax(0, 1fr); gap: 4px 12px; align-items: center; text-align: left; background: var(--surface); border: 1.5px solid var(--line); border-radius: 12px; padding: 12px 14px; cursor: pointer; }
.libcard:hover { border-color: var(--teal-s); }
.libn { grid-row: span 2; width: 36px; height: 36px; border-radius: 10px; background: var(--top); color: var(--on-top); display: grid; place-items: center; font-weight: 800; }
.libt { display: flex; flex-direction: column; min-width: 0; } .libt small { color: var(--muted); font-family: var(--mono); font-size: 12px; overflow: hidden; text-overflow: ellipsis; }
.clock { font: 800 clamp(3rem, 10vw, 5.5rem)/1 var(--mono); font-variant-numeric: tabular-nums; }
.tallyrow { display: grid; grid-template-columns: repeat(3, minmax(0, 1fr)); gap: 12px; }
@media (max-width: 640px) { .tallyrow { grid-template-columns: minmax(0, 1fr); } }
.tally { border: 2px solid var(--line); border-radius: 12px; padding: 12px; display: flex; flex-direction: column; gap: 6px; }
.tally.v-scam { border-color: var(--scam); } .tally.v-real { border-color: var(--safe); } .tally.v-unsure { border-color: var(--unsure); }
.tn { font: 800 2.2rem/1 var(--mono); }
.tbar { background: var(--line); height: 10px; border-radius: 6px; overflow: hidden; } .tbar > div { height: 100%; background: var(--teal); }

/* ---- hộp thoại, thông báo ---- */
.overlay { position: fixed; inset: 0; z-index: 50; background: rgba(8,18,30,.6); display: grid; place-items: center; padding: max(16px, env(safe-area-inset-top, 0px)) max(16px, env(safe-area-inset-right, 0px)) max(16px, env(safe-area-inset-bottom, 0px)) max(16px, env(safe-area-inset-left, 0px)); overflow-y: auto; }
.modal { width: min(560px, 100%); background: var(--surface); color: var(--fg); border-radius: 16px; padding: 22px; display: flex; flex-direction: column; gap: 14px; box-shadow: 0 20px 60px rgba(0,0,0,.4); max-height: 100%; overflow-y: auto; }
.modal.wide { width: min(860px, 100%); }
.modal-body { display: flex; flex-direction: column; gap: 12px; }
.modal-actions { display: flex; justify-content: flex-end; gap: 10px; }
.toast { position: fixed; left: 50%; bottom: calc(24px + env(safe-area-inset-bottom, 0px)); transform: translate(-50%, 20px); background: var(--top); color: var(--on-top); padding: 10px 18px; border-radius: 10px; font-size: 14px; opacity: 0; pointer-events: none; transition: opacity .2s, transform .2s; z-index: 60; max-width: min(520px, 90vw); }
.toast.on { opacity: 1; transform: translate(-50%, 0); }
@media (prefers-reduced-motion: reduce) { * { transition: none !important; animation: none !important; scroll-behavior: auto !important; } }

@media print {
  body::before, .topbar, .stepper, .foot, .noprint, .toast { display: none !important; }
  body { background: #fff; color: #000; }
  .main > *:not(.cert) { display: none; }
  .card { box-shadow: none; }
}

</style>
</head>
<body>
<div id="app"><p style="padding:24px;font-family:sans-serif">Đang tải học liệu…</p></div>
<noscript><p style="padding:24px;font-family:sans-serif">Học liệu cần bật JavaScript để chạy.</p></noscript>
<script>
const DATA = {"BRAND":{"name":"Thám Tử Hộp Thư","tagline":"Học liệu số nhận diện và xử lý thư điện tử lừa đảo","course":"Công nghệ giáo dục","school":"Trường Đại học Sư phạm Thành phố Hồ Chí Minh","faculty":"Khoa Công nghệ thông tin","version":"1.0","date":"10/2026","license":"CC BY-NC-SA 4.0 (đề xuất, nhóm có thể đổi)","fakeSchool":{"name":"Trường Đại học Mẫu","domain":"dhmau.example"},"palette":{"ink":"#12263F","teal":"#0F8B8D","amber":"#F2A541","scam":"#C8433F","safe":"#2E8B57","unsure":"#B9770E","paper":"#F6F4EE","mist":"#E8EEF4"},"me":"sinhvien@sv.dhmau.example"},"SIGNS":[{"id":"S1","label":"Tên miền người gửi không thuộc tổ chức mà thư tự nhận"},{"id":"S2","label":"Tên miền giả, gần giống tên miền thật"},{"id":"S3","label":"Liên kết dẫn sang tên miền khác"},{"id":"S4","label":"Thúc giục, tạo áp lực thời gian"},{"id":"S5","label":"Đòi mật khẩu, mã OTP hoặc giấy tờ cá nhân"},{"id":"S6","label":"Đòi chuyển tiền trước"},{"id":"S7","label":"Lời hứa quá hời (trúng thưởng, lương cao)"},{"id":"S8","label":"Tệp đính kèm lạ (tệp nén, tệp chạy được)"},{"id":"S9","label":"Dùng thư cá nhân để xưng là người của trường"},{"id":"S10","label":"Kéo sang kênh do người gửi chọn (số điện thoại lạ, liên kết)"},{"id":"S0","label":"Không thấy dấu hiệu bất thường"}],"LAYERS":[{"id":"sender","n":1,"name":"Người gửi","q":"Địa chỉ gửi thật có khớp tên hiển thị và tên miền của tổ chức không?"},{"id":"link","n":2,"name":"Liên kết","q":"Địa chỉ đích (hiện khi rê chuột, chưa bấm) có thuộc tên miền của tổ chức không?"},{"id":"content","n":3,"name":"Nội dung và yêu cầu","q":"Thư có thúc giục hoặc đòi thông tin nhạy cảm (mật khẩu, OTP, giấy tờ, tiền) không?"}],"LAYER_STATES":{"ok":"Đáng tin","bad":"Có vấn đề","warn":"Chưa kiểm chứng được","na":"Không có (không áp dụng)"},"VERDICTS":{"scam":"Lừa đảo","real":"Thật","unsure":"Chưa chắc, cần kiểm chứng"},"EMAILS":[{"id":"1","set":"main","group":1,"time":"Thứ Hai 08:12","from":{"name":"Hỗ trợ tài khoản ĐH Mẫu","addr":"ho-tro@dhmau-support.example"},"subject":"[KHẨN] Tài khoản sinh viên của bạn sẽ bị khóa sau 24 giờ","body":["Kính gửi sinh viên,","Hệ thống phát hiện tài khoản sinh viên của bạn chưa được xác minh theo quy định mới. [[c:Nếu không xác minh trong vòng 24 giờ, tài khoản sẽ bị khóa vĩnh viễn]] và bạn không thể đăng ký học phần hay xem điểm.","Vui lòng bấm vào liên kết dưới đây và [[c:nhập lại mật khẩu]] để xác minh ngay:","[[l:a|Xác minh tài khoản ngay]]","Trân trọng,\nBan Hỗ trợ Tài khoản"],"links":{"a":"https://dhmau-dangnhap.example/xac-minh"},"attachments":[],"verdict":"scam","signs":["S1","S3","S4","S5"],"layers":{"sender":{"s":"bad","note":"Tên miền gửi là dhmau-support.example, không phải dhmau.example của trường."},"link":{"s":"bad","note":"Địa chỉ đích dhmau-dangnhap.example không thuộc dhmau.example."},"content":{"s":"bad","note":"Đe dọa khóa tài khoản sau 24 giờ và đòi nhập mật khẩu qua liên kết."}},"explain":"Thư hội đủ ba dấu hiệu kinh điển: tên miền gửi và tên miền liên kết đều lạ, thời hạn 24 giờ để bạn không kịp nghĩ, và đòi mật khẩu. Trường không xác minh tài khoản bằng cách bắt bạn nhập mật khẩu qua thư.","hints":["Hãy đọc kỹ phần sau dấu @ của địa chỉ gửi, rồi so với tên miền của trường (dhmau.example).","Rê chuột lên nút xác minh (chưa bấm) và nhìn địa chỉ đích hiện ở góc dưới.","Thư có đòi bạn một thứ không bao giờ nên gửi qua thư không? Và có đặt hạn gấp không?"],"action":"Không bấm. Tự gõ địa chỉ cổng thông tin chính thức để kiểm tra tài khoản, hoặc hỏi Phòng Công tác sinh viên. Báo thư cho bộ phận CNTT của trường."},{"id":"2","set":"main","group":1,"time":"Thứ Hai 09:40","from":{"name":"Chương trình Quà tặng Online","addr":"khuyenmai@quatang-online.example"},"subject":"Chúc mừng! Bạn là người may mắn trúng laptop","body":["Chào bạn,","Địa chỉ thư của bạn đã được chọn ngẫu nhiên trong đợt quay số tháng 10 và [[c:trúng 01 laptop trị giá 18.900.000 đồng]].","Để nhận quà, bạn vui lòng [[c:chuyển phí vận chuyển 200.000 đồng]] vào tài khoản dưới đây [[c:trong hôm nay]]:\nNgân hàng Mẫu, STK 0123 456 789, chủ tài khoản: Công ty QT Online.","Sau khi chuyển, hãy trả lời thư này kèm ảnh biên lai."],"links":{},"attachments":[],"verdict":"scam","signs":["S4","S6","S7"],"layers":{"sender":{"s":"bad","note":"Người gửi lạ, không liên quan tới trường hay dịch vụ nào bạn đang dùng."},"link":{"s":"na","note":"Thư không có liên kết, nhưng đòi bạn chuyển tiền thẳng vào tài khoản."},"content":{"s":"bad","note":"Trúng thưởng bạn chưa từng tham gia, đòi tiền trước và hạn trong hôm nay."}},"explain":"Không ai tặng quà mà bắt người nhận trả tiền trước. Phần thưởng lớn kết hợp khoản phí nhỏ là mô típ rất phổ biến: số tiền nhỏ khiến bạn bớt cảnh giác.","hints":["Bạn có nhớ đã tham gia quay số nào không?","Ai là người phải trả tiền trong thư này, và trả trước hay sau khi nhận quà?","Phần thưởng lớn đi kèm một khoản phí nhỏ phải nộp ngay hôm nay là dấu hiệu của loại thư nào?"],"action":"Xóa thư hoặc đánh dấu là thư rác. Tuyệt đối không chuyển tiền. Nếu đã chuyển, báo ngay cho ngân hàng và cơ quan công an."},{"id":"3","set":"main","group":1,"time":"Thứ Hai 11:05","from":{"name":"Bảo mật Ngân hàng Mẫu","addr":"baomat@nganhangmau.example"},"subject":"Cảnh báo giao dịch bất thường trên tài khoản của bạn","body":["Kính gửi Quý khách,","Chúng tôi ghi nhận giao dịch chuyển 12.500.000 đồng từ tài khoản của Quý khách lúc 02:14 sáng nay.","Nếu đây không phải giao dịch của bạn, vui lòng [[c:trả lời thư này kèm mã OTP gồm 6 chữ số]] vừa được gửi tới điện thoại để chúng tôi hủy giao dịch ngay lập tức. [[c:Mã OTP chỉ có hiệu lực trong 5 phút.]]"],"links":{},"attachments":[],"verdict":"scam","signs":["S4","S5"],"layers":{"sender":{"s":"warn","note":"Tên miền khớp tên ngân hàng, nhưng địa chỉ gửi có thể bị giả mạo. Chỉ nhìn địa chỉ là chưa đủ."},"link":{"s":"na","note":"Không có liên kết."},"content":{"s":"bad","note":"Đòi mã OTP qua thư và đặt hạn 5 phút."}},"explain":"Mã OTP chỉ dùng để chính bạn nhập vào trang hoặc ứng dụng chính thức. Không có nhân viên thật nào xin OTP qua thư. Hạn 5 phút khiến bạn hoảng và làm theo.","hints":["Bạn có thể dùng mã OTP để làm gì, và ai cần biết mã đó?","Thư này đòi bạn gửi lại thông tin gì, qua kênh nào?","Đã đòi OTP lại còn đặt hạn 5 phút: hai dấu hiệu đi liền nhau."],"action":"Không trả lời, không đọc hay gửi mã OTP cho bất kỳ ai. Mở ứng dụng ngân hàng chính thức hoặc gọi số tổng đài in trên thẻ để kiểm tra giao dịch."},{"id":"4","set":"main","group":1,"time":"Thứ Hai 14:26","from":{"name":"Tuyển dụng Việc Làm Nhẹ","addr":"tuyendung@vieclamnhe.example"},"subject":"Việc nhẹ lương cao 800k/ngày cho sinh viên, làm tại nhà","body":["Chào bạn,","Công ty cần tuyển 20 cộng tác viên là sinh viên, làm tại nhà 2 giờ mỗi ngày, [[c:thu nhập 800.000 đồng mỗi ngày]], không cần kinh nghiệm.","Để đăng ký, hãy [[c:gửi ngay ảnh chụp hai mặt căn cước công dân]] và số điện thoại vào thư này.","[[c:Chỉ còn 5 suất]], hết suất chúng tôi sẽ đóng đăng ký."],"links":{},"attachments":[],"verdict":"scam","signs":["S4","S5","S7"],"layers":{"sender":{"s":"bad","note":"Công ty không rõ tên, không có địa chỉ hay mã số doanh nghiệp để kiểm chứng."},"link":{"s":"na","note":"Không có liên kết."},"content":{"s":"bad","note":"Lương cao bất thường, đòi ảnh giấy tờ ngay từ đầu, số suất giới hạn."}},"explain":"Việc dễ, lương cao và đòi giấy tờ ngay từ thư đầu tiên là tổ hợp rất đáng ngờ. Ảnh căn cước có thể bị dùng để mở tài khoản hoặc vay tiền mạo danh.","hints":["Mức lương này có hợp lý với công việc 2 giờ mỗi ngày không?","Công ty đã chứng minh mình là ai chưa, trước khi xin giấy tờ của bạn?","Số suất có hạn cũng là một cách thúc giục."],"action":"Không gửi giấy tờ. Nếu thật sự muốn ứng tuyển, tìm công ty qua kênh chính thức, kiểm tra mã số thuế và địa chỉ trước."},{"id":"5","set":"main","group":2,"time":"Thứ Ba 08:03","from":{"name":"Phòng Tài vụ ĐH Mẫu","addr":"phongtaivu@dhrnau.example"},"subject":"Xác nhận học phí học kỳ 1 năm học 2026-2027","body":["Kính gửi sinh viên,","Phòng Tài vụ xác nhận đã nhận học phí học kỳ 1 của bạn. Vui lòng xem biên lai điện tử tại liên kết sau:","[[l:a|Xem biên lai điện tử]]","Nếu có sai sót, bạn có thể đăng nhập để phản ánh.","Trân trọng,\nPhòng Tài vụ"],"links":{"a":"https://dhrnau.example/bien-lai"},"attachments":[],"verdict":"scam","signs":["S2","S3"],"layers":{"sender":{"s":"bad","note":"dhrnau.example giả dhmau.example: chữ r và n đứng cạnh nhau trông giống chữ m."},"link":{"s":"bad","note":"Liên kết dẫn tới chính tên miền giả dhrnau.example."},"content":{"s":"ok","note":"Nội dung rất bình thường, không thúc giục hay đòi thông tin. Đây là lý do không thể chỉ dựa vào giọng văn."}},"explain":"Thư này không có chữ nào đáng sợ, nên chỉ có lớp 1 và lớp 2 lộ ra. Kẻ lừa đảo đăng ký tên miền gần giống tên miền thật, chỉ khác một cặp chữ khó thấy. Khi nghi ngờ, đọc địa chỉ từng chữ một.","hints":["Nội dung thư không có gì lạ. Hãy chuyển sang xem địa chỉ gửi.","So từng chữ của dhrnau.example với dhmau.example.","Chữ r và chữ n đứng sát nhau trông giống chữ nào?"],"action":"Không bấm liên kết. Tự gõ địa chỉ cổng thông tin của trường để xem biên lai và hỏi Phòng Tài vụ nếu cần."},{"id":"6","set":"main","group":2,"time":"Thứ Ba 10:30","from":{"name":"Giáo vụ ĐH Mẫu","addr":"giaovu@dhmau.example"},"subject":"Thay đổi lịch thi giữa kỳ","body":["Thân gửi các bạn sinh viên,","Do điều chỉnh phòng thi, lịch thi giữa kỳ của một số học phần đã thay đổi. Các bạn vui lòng xem lịch thi mới tại:","[[l:a|Xem lịch thi mới]]","[[c:Yêu cầu đăng nhập bằng tài khoản sinh viên.]] Lịch cũ không còn hiệu lực.","Phòng Giáo vụ"],"links":{"a":"https://dhmau-lichthi.example/dang-nhap"},"attachments":[],"verdict":"scam","signs":["S3","S5"],"layers":{"sender":{"s":"ok","note":"Địa chỉ gửi khớp tên miền dhmau.example. Nhưng thư giả mạo người gửi vẫn xảy ra, nên một lớp đạt chưa đủ để kết luận."},"link":{"s":"bad","note":"Liên kết dẫn sang dhmau-lichthi.example, không thuộc dhmau.example."},"content":{"s":"warn","note":"Bắt đăng nhập qua liên kết trong thư để xem lịch thi là đáng ngờ."}},"explain":"Đây là thư dạy bạn một bài học quan trọng: lớp 1 đạt vẫn chưa an toàn. Địa chỉ gửi có thể bị giả mạo, còn liên kết thì dẫn sang tên miền khác và đòi bạn đăng nhập. Luôn kiểm tra đủ ba lớp.","hints":["Địa chỉ gửi trông ổn. Đừng dừng ở đó.","Rê chuột lên liên kết: tên miền đích có phải dhmau.example không?","Thư bảo bạn đăng nhập ở đâu để làm gì?"],"action":"Không đăng nhập qua liên kết trong thư. Tự vào cổng thông tin chính thức xem lịch thi, hoặc hỏi giáo vụ qua kênh bạn đã biết."},{"id":"7","set":"main","group":2,"time":"Thứ Ba 15:18","from":{"name":"Phòng CNTT ĐH Mẫu","addr":"cntt@dhmau.example"},"subject":"Thông báo bảo trì hệ thống tối thứ Bảy","body":["Phòng Công nghệ thông tin thông báo: hệ thống cổng thông tin sinh viên sẽ bảo trì từ 22:00 thứ Bảy đến 02:00 Chủ nhật. Trong thời gian này, các bạn không đăng nhập được.","Xin lỗi vì sự bất tiện. Phòng CNTT sẽ không yêu cầu bạn cung cấp mật khẩu qua thư điện tử."],"links":{},"attachments":[],"verdict":"real","signs":["S0"],"layers":{"sender":{"s":"ok","note":"Tên miền khớp dhmau.example."},"link":{"s":"na","note":"Không có liên kết."},"content":{"s":"ok","note":"Có giọng thông báo nhưng không thúc giục, không đòi thông tin gì."}},"explain":"Thư thông báo thật thường chỉ nói điều sẽ xảy ra và không bắt bạn làm gì ngay. Nếu bạn chọn \"lừa đảo\" vì thấy chữ \"thông báo\", đó là phản xạ chưa phân biệt, và cũng là một thiệt hại: sinh viên bỏ qua thông báo quan trọng.","hints":["Thư có bắt bạn làm điều gì không?","Có liên kết nào để bấm không?","Không có dấu hiệu nào của ba lớp thì có nên nghi ngờ chỉ vì thư mang giọng thông báo?"],"action":"Đọc và ghi nhớ giờ bảo trì. Không cần hành động nào khác."},{"id":"8","set":"main","group":2,"time":"Thứ Tư 07:52","from":{"name":"Nguyễn Văn A (Giảng viên)","addr":"thay.nguyenvana@mailcanhan.example"},"subject":"Tài liệu tuần này","body":["Chào các em,","Thầy gửi tài liệu cho buổi học tuần này trong tệp đính kèm, các em tải về đọc trước nhé.","[[c:Hộp thư của trường đang bị lỗi nên thầy tạm dùng thư này.]]","Thầy A."],"links":{},"attachments":[{"name":"TaiLieu_Tuan7.zip","size":"2,4 MB"}],"verdict":"unsure","signs":["S8","S9"],"layers":{"sender":{"s":"warn","note":"Tên có thể đúng, nhưng địa chỉ không thuộc dhmau.example."},"link":{"s":"na","note":"Không có liên kết, nhưng có tệp nén đính kèm."},"content":{"s":"warn","note":"Có lý do để giải thích vì sao dùng thư cá nhân, nhưng đó cũng là cách kẻ giả danh hay dùng."}},"explain":"Đây là thư không thể kết luận chỉ bằng nhìn. Có thể thầy thật sự dùng thư cá nhân, cũng có thể kẻ gian giả danh. Hành động đúng là kiểm chứng qua kênh khác trước khi mở tệp nén.","hints":["Địa chỉ gửi có thuộc trường không?","Thư có lý do hợp lý, nhưng lý do đó có thể kiểm chứng ở đâu?","Khi không chắc, câu trả lời an toàn không phải \"thật\" hay \"giả\" mà là một hành động kiểm chứng."],"action":"Chưa mở tệp. Hỏi trực tiếp thầy, hỏi nhóm lớp hoặc hỏi giáo vụ để xác nhận thầy có gửi thư này không."},{"id":"9","set":"main","group":3,"time":"Thứ Tư 09:15","from":{"name":"Phòng Đào tạo ĐH Mẫu","addr":"dkhp@dhmau.example"},"subject":"Xác nhận đăng ký học phần học kỳ 1","body":["Bạn đã đăng ký thành công 6 học phần trong học kỳ 1.","Để xem chi tiết, hãy tự đăng nhập cổng thông tin sinh viên bằng địa chỉ bạn vẫn dùng. Thư này không chứa liên kết đăng nhập.","Nếu có sai sót, liên hệ Phòng Đào tạo trong giờ hành chính."],"links":{},"attachments":[],"verdict":"real","signs":["S0"],"layers":{"sender":{"s":"ok","note":"Tên miền khớp dhmau.example."},"link":{"s":"na","note":"Không có liên kết, thư còn hướng dẫn bạn tự mở cổng chính thức."},"content":{"s":"ok","note":"Không thúc giục, không đòi thông tin."}},"explain":"Dấu hiệu tốt: thư không kéo bạn đi đâu, thậm chí dặn bạn tự mở cổng chính thức. Thư càng ít yêu cầu bạn làm theo liên kết của nó thì càng ít rủi ro.","hints":["Thư có đưa liên kết nào không?","Thư bảo bạn làm gì?","Ba lớp có lớp nào đáng ngờ không?"],"action":"Tự đăng nhập cổng thông tin để kiểm tra đăng ký học phần như thư dặn."},{"id":"10","set":"main","group":3,"time":"Thứ Tư 13:40","from":{"name":"Thư viện ĐH Mẫu","addr":"thuvien@dhmau.example"},"subject":"Bản tin thư viện tháng 10: sách mới và giờ mở cửa","body":["Thư viện giới thiệu 30 đầu sách mới về công nghệ giáo dục và lịch mở cửa mùa thi.","Xem danh sách tại:","[[l:a|Danh sách sách mới]]","Chúc các bạn một học kỳ hiệu quả!"],"links":{"a":"https://thuvien.dhmau.example/sach-moi"},"attachments":[],"verdict":"real","signs":["S0"],"layers":{"sender":{"s":"ok","note":"Tên miền khớp dhmau.example."},"link":{"s":"ok","note":"thuvien.dhmau.example là tên miền con của dhmau.example."},"content":{"s":"ok","note":"Bản tin thông thường, không đòi thông tin."}},"explain":"Có liên kết không đồng nghĩa với lừa đảo. Quan trọng là địa chỉ đích thuộc tên miền nào. Ở đây là tên miền con của trường, và thư không đòi bạn đăng nhập hay cung cấp gì.","hints":["Rê chuột lên liên kết và đọc địa chỉ đích.","Tên miền con có thuộc dhmau.example không?","Thư có đòi bạn thông tin gì không?"],"action":"Có thể bấm xem danh sách sách mới. Nếu phân vân, tự gõ địa chỉ trang thư viện."},{"id":"11","set":"main","group":3,"time":"Thứ Tư 16:02","from":{"name":"Dịch vụ Học tập Mẫu","addr":"no-reply@dichvu.example"},"subject":"Mã xác thực đăng nhập của bạn","context":"Tình huống: bạn VỪA tự đăng nhập vào một dịch vụ học tập và đang chờ mã.","body":["Mã xác thực của bạn là 482 917. Mã có hiệu lực trong 10 phút.","Nếu bạn không vừa đăng nhập, hãy bỏ qua thư này và đổi mật khẩu từ trang chính thức. Không chia sẻ mã này với bất kỳ ai, kể cả nhân viên hỗ trợ."],"links":{},"attachments":[],"verdict":"real","signs":["S0"],"layers":{"sender":{"s":"ok","note":"Dịch vụ bạn vừa dùng. Địa chỉ không thuộc dhmau.example nhưng thư cũng không tự nhận là của trường."},"link":{"s":"na","note":"Không có liên kết."},"content":{"s":"ok","note":"Mã do chính bạn yêu cầu và thư còn dặn không chia sẻ."}},"explain":"Bối cảnh quyết định kết luận. Mã bạn vừa yêu cầu là thư thật. Nhưng nếu bạn KHÔNG vừa đăng nhập mà nhận mã, đó là tín hiệu có người đang thử đăng nhập vào tài khoản của bạn. Dù trường hợp nào cũng không đọc mã cho ai.","hints":["Bạn có vừa đăng nhập không?","Thư có đòi bạn gửi mã cho ai không?","Thư tự dặn gì về việc chia sẻ mã?"],"action":"Nhập mã vào đúng trang bạn đang đăng nhập. Không gửi mã cho bất kỳ ai."},{"id":"12","set":"main","group":3,"time":"Thứ Năm 08:30","from":{"name":"Cố vấn học tập K26","addr":"lop@dhmau.example"},"subject":"Nhắc nộp báo cáo trước 23:59 thứ Sáu","body":["Các bạn nhớ nộp báo cáo môn Công nghệ giáo dục [[c:trước 23:59 thứ Sáu này]] trên hệ thống nộp bài của lớp như mọi lần.","Bài nộp trễ sẽ bị trừ điểm theo đề cương. Có thắc mắc, nhắn trong nhóm lớp."],"links":{},"attachments":[],"verdict":"real","signs":["S0"],"layers":{"sender":{"s":"ok","note":"Tên miền khớp dhmau.example."},"link":{"s":"na","note":"Không có liên kết lạ; nộp bài ở nơi bạn vẫn quen dùng."},"content":{"s":"ok","note":"Có hạn chót nhưng không đòi thông tin nhạy cảm."}},"explain":"Có hạn chót không phải lúc nào cũng là dấu hiệu lừa đảo. Điều đáng ngờ là hạn chót đi kèm yêu cầu cung cấp thứ nhạy cảm hoặc làm theo kênh lạ. Thư này thì không.","hints":["Hạn chót đi kèm yêu cầu gì?","Nộp bài ở đâu: kênh quen dùng hay liên kết lạ?","Có đòi mật khẩu hay tiền không?"],"action":"Nộp bài đúng hạn ở hệ thống quen dùng."},{"id":"T","set":"team","group":"T","time":"Thứ Năm 10:12","from":{"name":"Quỹ Học bổng Mẫu","addr":"hocbong@quyhocbongmau.example"},"subject":"Xét học bổng đợt bổ sung","body":["Quỹ Học bổng Mẫu mở đợt xét bổ sung cho sinh viên năm nhất.","Hồ sơ gồm một biểu mẫu trực tuyến ghi họ tên, mã sinh viên và số điện thoại. [[c:Hạn nhận hồ sơ: 3 ngày kể từ hôm nay.]]","[[l:a|Điền biểu mẫu đăng ký]]","Mọi thắc mắc xin liên hệ Quỹ."],"links":{"a":"https://quyhocbongmau.example/dang-ky"},"attachments":[],"verdict":"unsure","signs":["S1","S4"],"layers":{"sender":{"s":"warn","note":"Người gửi ngoài trường. Tên miền khớp tên quỹ nhưng bạn chưa biết quỹ này có thật hay không."},"link":{"s":"warn","note":"Liên kết cùng tên miền với người gửi, nên chưa phát hiện gì sai, nhưng cũng chưa chứng minh được gì."},"content":{"s":"warn","note":"Không đòi mật khẩu hay tiền, chỉ ba thông tin thường gặp. Hạn 3 ngày hơi gấp."}},"explain":"Thư không có dấu hiệu lừa đảo rõ ràng, cũng không có gì chứng minh nó thật. Đây là loại thư cần kiểm chứng ở bên ngoài thư: hỏi Phòng Công tác sinh viên, tìm trang chính thức của quỹ bằng cách tự gõ tên quỹ.","hints":["Ba lớp có lớp nào chắc chắn sai không?","Có lớp nào chắc chắn đúng không?","Thông tin nào cần tìm ở ngoài thư để quyết định?"],"action":"Chưa điền. Hỏi Phòng Công tác sinh viên hoặc tìm trang chính thức của quỹ (tự gõ tên quỹ, không bấm liên kết trong thư) rồi mới quyết định."}],"PRE":[{"id":"P1","set":"pre","time":"Thứ Hai 07:45","from":{"name":"Cổng đăng ký học phần","addr":"dangky@dhmau-hocphan.example"},"subject":"Cổng đăng ký học phần sắp đóng, nhập lại mật khẩu để giữ chỗ","body":["Kính gửi sinh viên,","[[c:Cổng đăng ký học phần sẽ đóng sau 2 giờ nữa.]] Để giữ chỗ cho các học phần đã chọn, vui lòng [[c:nhập lại mật khẩu]] tại liên kết dưới đây.","[[l:a|Giữ chỗ học phần]]"],"links":{"a":"https://dhmau-hocphan.example/giu-cho"},"attachments":[],"verdict":"scam","signs":["S1","S3","S4","S5"],"layers":{"sender":{"s":"bad","note":"dhmau-hocphan.example không phải dhmau.example."},"link":{"s":"bad","note":"Đích đến cũng là tên miền lạ."},"content":{"s":"bad","note":"Hạn 2 giờ và đòi mật khẩu."}},"explain":"Cùng mô típ thư 1: tên miền lạ, hạn gấp, đòi mật khẩu."},{"id":"P2","set":"pre","time":"Thứ Hai 09:10","from":{"name":"Cố vấn học tập K26","addr":"cvht@dhmau.example"},"subject":"Họp lớp đầu kỳ chiều thứ Sáu","body":["Các bạn thân mến,","Lớp sẽ họp đầu kỳ vào 15:00 chiều thứ Sáu tại phòng B.201. Nội dung: phổ biến quy chế học tập và bầu ban cán sự.","Bạn nào bận xin nhắn trước trong nhóm lớp."],"links":{},"attachments":[],"verdict":"real","signs":["S0"],"layers":{"sender":{"s":"ok","note":"Tên miền khớp dhmau.example."},"link":{"s":"na","note":"Không có liên kết."},"content":{"s":"ok","note":"Thông báo bình thường, không đòi thông tin."}},"explain":"Thông báo thật: tên miền khớp, không liên kết, không yêu cầu nhạy cảm."},{"id":"P3","set":"pre","time":"Thứ Ba 10:20","from":{"name":"Ban tổ chức Cuộc thi Lập trình","addr":"sukien@congtytaitro.example"},"subject":"Mời đăng ký Cuộc thi Lập trình sinh viên do Công ty Tài Trợ tổ chức","body":["Công ty Tài Trợ phối hợp cùng một số trường đại học tổ chức cuộc thi lập trình dành cho sinh viên năm nhất và năm hai.","Giải nhất 10.000.000 đồng. Đăng ký tại:","[[l:a|Đăng ký dự thi]]","Hạn đăng ký: hết tuần này."],"links":{"a":"https://congtytaitro.example/cuoc-thi"},"attachments":[],"verdict":"unsure","signs":["S1","S7"],"layers":{"sender":{"s":"warn","note":"Đơn vị ngoài trường, cần kiểm tra có thật không."},"link":{"s":"warn","note":"Cùng tên miền người gửi, chưa chứng minh được gì."},"content":{"s":"warn","note":"Giải thưởng lớn và hạn tuần này, chưa đòi thông tin nhạy cảm."}},"explain":"Chưa đủ căn cứ để kết luận, cần kiểm chứng bên ngoài thư."},{"id":"P4","set":"pre","time":"Thứ Ba 14:05","from":{"name":"Giao hàng nhanh","addr":"giaohang@chuyenphat-nhanh.example"},"subject":"Bưu phẩm của bạn chưa giao được, nộp phí lưu kho 15.000đ","body":["Bưu phẩm mang tên bạn chưa giao được do thiếu thông tin địa chỉ.","Vui lòng [[c:nộp phí lưu kho 15.000 đồng]] và cập nhật địa chỉ trong 24 giờ, nếu không bưu phẩm sẽ bị hoàn về.","[[l:a|Cập nhật địa chỉ và nộp phí]]"],"links":{"a":"https://chuyenphat-nhanh.example/luu-kho"},"attachments":[],"verdict":"scam","signs":["S4","S6"],"layers":{"sender":{"s":"bad","note":"Bạn không nhớ đã đặt hàng nào và đơn vị này không được nhắc tên ở đâu."},"link":{"s":"warn","note":"Cùng tên miền người gửi, nhưng người gửi vốn đã đáng ngờ."},"content":{"s":"bad","note":"Phí nhỏ, hạn 24 giờ, cần nộp qua liên kết."}},"explain":"Phí nhỏ là mồi để lấy thông tin thẻ. Đơn hàng bạn không đặt là dấu hiệu rõ."}],"POST":[{"id":"A1","set":"post","time":"Thứ Sáu 08:00","from":{"name":"Phòng Đào tạo ĐH Mẫu","addr":"daotao@dhmau.example"},"subject":"Lịch học bù tuần 9","body":["Các lớp bị ảnh hưởng bởi đợt nghỉ lễ sẽ học bù vào chiều thứ Bảy tuần 9.","Lịch chi tiết đã được cập nhật trong cổng thông tin sinh viên, các bạn tự đăng nhập để xem. Thư này không chứa liên kết."],"links":{},"attachments":[],"verdict":"real","signs":["S0"],"layers":{"sender":{"s":"ok","note":"Tên miền khớp dhmau.example."},"link":{"s":"na","note":"Không có liên kết, thư dặn tự mở cổng chính thức."},"content":{"s":"ok","note":"Không thúc giục, không đòi thông tin."}},"explain":"Thư thật: tên miền khớp, không liên kết, hướng bạn tự mở cổng chính thức.","action":"Tự đăng nhập cổng thông tin để xem lịch học bù."},{"id":"A2","set":"post","time":"Thứ Sáu 09:25","from":{"name":"Phòng Tài chính ĐH Mẫu","addr":"hoantien@dhmau-taichinh.example"},"subject":"Hoàn tiền học phí do thanh toán dư","body":["Hệ thống ghi nhận bạn đã thanh toán dư 1.250.000 đồng học phí.","Để nhận hoàn tiền [[c:trong hôm nay]], vui lòng [[c:điền số thẻ ngân hàng, ngày hết hạn và mã CVV]] tại liên kết:","[[l:a|Nhận hoàn tiền]]"],"links":{"a":"https://hoantien-dhmau.example/nhan-tien"},"attachments":[],"verdict":"scam","signs":["S1","S3","S4","S5"],"layers":{"sender":{"s":"bad","note":"dhmau-taichinh.example không phải dhmau.example."},"link":{"s":"bad","note":"hoantien-dhmau.example là tên miền lạ, bắt chước tên trường."},"content":{"s":"bad","note":"Đòi số thẻ và mã CVV, hạn trong hôm nay. Nhận tiền hoàn không cần đưa mã CVV."}},"explain":"Muốn hoàn tiền cho bạn thì không cần biết mã bảo mật thẻ của bạn. Tên miền lạ, hạn hôm nay và đòi thông tin thẻ.","action":"Không điền gì. Hỏi Phòng Tài chính qua kênh chính thức về khoản thanh toán dư."},{"id":"A3","set":"post","time":"Thứ Sáu 11:10","from":{"name":"Khoa Công nghệ thông tin","addr":"khaosat@khoacntt.dhmau.example"},"subject":"Mời tham gia khảo sát chất lượng học phần","body":["Khoa mời bạn tham gia khảo sát ẩn danh về chất lượng học phần (khoảng 5 phút).","Khảo sát được thực hiện trên nền tảng của đơn vị đối tác:","[[l:a|Làm khảo sát]]","Hạn: hết tuần này."],"links":{"a":"https://khaosat-giaoduc.example/form/k26"},"attachments":[],"verdict":"unsure","signs":["S3"],"layers":{"sender":{"s":"ok","note":"khoacntt.dhmau.example là tên miền con của dhmau.example."},"link":{"s":"warn","note":"Nền tảng bên thứ ba, không thuộc dhmau.example. Có thể hợp lệ nhưng cần xác nhận."},"content":{"s":"ok","note":"Khảo sát ẩn danh, không đòi thông tin nhạy cảm."}},"explain":"Người gửi hợp lệ, nhưng liên kết dẫn ra bên ngoài. Cần xác nhận với Khoa hoặc cố vấn học tập rằng Khoa có dùng nền tảng này.","action":"Chưa điền. Hỏi cố vấn học tập hoặc xem thông báo khảo sát trên cổng chính thức."},{"id":"A4","set":"post","time":"Thứ Sáu 15:48","from":{"name":"Thanh Toán Nhanh","addr":"no-reply@thanhtoan-nhanh.example"},"subject":"Xác nhận giao dịch 4.990.000đ, hủy trong 30 phút","body":["Giao dịch mua điện thoại trị giá 4.990.000 đồng đã được ghi nhận từ tài khoản của bạn.","Nếu bạn không thực hiện, [[c:hãy hủy trong 30 phút]] bằng cách bấm vào liên kết hoặc [[c:gọi số 1900 0000]] để nói chuyện với nhân viên:","[[l:a|Hủy giao dịch]]"],"links":{"a":"https://thanhtoan-nhanh.example/huy"},"attachments":[],"verdict":"scam","signs":["S4","S10"],"layers":{"sender":{"s":"bad","note":"Dịch vụ bạn không dùng, không có giao dịch nào để xác nhận."},"link":{"s":"bad","note":"Dẫn tới trang do người gửi dựng, để bạn đăng nhập hoặc nhập thông tin."},"content":{"s":"bad","note":"Báo giao dịch bạn không làm để dọa, hạn 30 phút, kéo sang số điện thoại lạ."}},"explain":"Dọa bằng một khoản tiền lớn rồi kéo bạn sang kênh liên lạc do kẻ gửi chọn (liên kết, số điện thoại). Muốn kiểm tra giao dịch, hãy mở ứng dụng ngân hàng của chính bạn.","action":"Không bấm, không gọi số trong thư. Mở ứng dụng ngân hàng chính thức để xem giao dịch."}],"ACTIONS":[{"id":"a1","text":"Không bấm liên kết trong thư","good":true},{"id":"a2","text":"Tự gõ địa chỉ chính thức của tổ chức để kiểm tra","good":true},{"id":"a3","text":"Hỏi qua một kênh khác đã biết (cố vấn, giáo vụ, tổng đài in trên thẻ)","good":true},{"id":"a4","text":"Báo thư cho bộ phận CNTT hoặc tổ chức bị giả mạo","good":true},{"id":"a5","text":"Trả lời thư để hỏi lại người gửi","good":false},{"id":"a6","text":"Gửi mã OTP cho \"nhân viên hỗ trợ\" để được giúp nhanh","good":false}],"ROLES":[{"id":"r1","name":"Người phân tích địa chỉ gửi","layer":"sender","tasks":["Đọc từng chữ phần sau dấu @","So với tên miền thật của tổ chức","Ghi bằng chứng cho lớp 1"]},{"id":"r2","name":"Người phân tích liên kết","layer":"link","tasks":["Rê chuột để xem địa chỉ đích","So tên miền đích với tên miền của tổ chức","Ghi bằng chứng cho lớp 2"]},{"id":"r3","name":"Người phân tích nội dung và yêu cầu","layer":"content","tasks":["Tìm cụm thúc giục hoặc đòi thông tin","Phân biệt thông tin quen dùng với thông tin nhạy cảm","Ghi bằng chứng cho lớp 3"]},{"id":"r4","name":"Người tổng hợp và phản biện","layer":"all","tasks":["Gom ba bằng chứng và đặt câu hỏi ngược","Đề xuất kết luận và hành động","Ghi cách kiểm chứng bên ngoài thư"]}],"CRITIQUE_QUESTIONS":["Bằng chứng đã đủ chưa? Có lớp nào nhóm bỏ qua không?","Có kết luận nào quá chắc chắn so với bằng chứng không?","Hành động đề xuất có khả thi và an toàn không?","Nhóm đã nêu cách kiểm chứng bên ngoài thư chưa?"],"SOURCE_FIELDS":[{"id":"name","label":"Tên nguồn và đường dẫn"},{"id":"issuer","label":"Ai phát hành"},{"id":"date","label":"Ngày đăng"},{"id":"type","label":"Loại nguồn"},{"id":"trust","label":"Mức tin cậy (cao, trung bình, thấp) và lý do"},{"id":"use","label":"Dùng nguồn vào việc gì"}],"SOURCE_SAMPLES":[{"name":"Trang DauHieuLuaDao.com, được giới thiệu qua bài đăng trên Google Vietnam Blog (01/04/2022)","issuer":"Google phối hợp với NCSC, theo bài đăng","date":"Bài giới thiệu đăng ngày 01/04/2022","type":"Trang thông tin phòng chống lừa đảo của tổ chức","trust":"Cao về nguồn gốc, vì được giới thiệu trên blog chính thức của Google Vietnam. Nội dung chi tiết của trang cần sinh viên tự mở và đối chiếu.","use":"Tra cứu các dấu hiệu lừa đảo phổ biến","level":"high"},{"name":"Bài \"Bí kíp để không trở thành nạn nhân của lừa đảo qua mail\", VietNamNet","issuer":"Báo điện tử VietNamNet, tác giả Trọng Đạt","date":"18/10/2021","type":"Bài báo hướng dẫn phổ thông","trust":"Trung bình: có tên tác giả và ngày đăng nhưng là báo chí, không phải tài liệu kỹ thuật. Cần đối chiếu với nguồn của tổ chức chuyên môn.","use":"Lấy ví dụ dấu hiệu dễ hiểu, không dùng làm căn cứ duy nhất","level":"mid"},{"name":"Bài chia sẻ trên mạng xã hội không ghi tác giả (ví dụ về loại nguồn)","issuer":"Không xác định","date":"Không có","type":"Bài đăng mạng xã hội","trust":"Thấp: không xác định được người chịu trách nhiệm hay căn cứ của thông tin.","use":"Chỉ làm manh mối để tìm nguồn gốc, không dùng để kết luận","level":"low"}],"SOURCE_EXERCISES":[{"id":"x1","title":"Bài báo VnEconomy ngày 01/11/2025: \"Việt Nam ghi nhận hơn 1.500 vụ lừa đảo trực tuyến, thiệt hại ước tính 1.660 tỷ đồng\"","facts":["Báo điện tử có tòa soạn, ghi ngày đăng","Dẫn số liệu từ cơ quan công an theo bài báo","Không phải hướng dẫn kỹ thuật"],"level":"mid","why":"Báo điện tử chính thống, có ngày và nêu nguồn số liệu nên đủ dùng để mô tả quy mô vấn đề. Nên đối chiếu với số liệu gốc của cơ quan chức năng nếu dùng trong văn bản chính thức."},{"id":"x2","title":"Bài đăng trên mạng xã hội: \"Cảnh báo khẩn! Ai nhận được thư từ địa chỉ này đừng mở, máy sẽ bị hack ngay!\"","facts":["Không ghi tác giả hay đơn vị","Không có ngày đăng","Giọng điệu thúc giục, không dẫn nguồn"],"level":"low","why":"Không xác định được ai chịu trách nhiệm, không có căn cứ và còn dùng chính thủ đoạn thúc giục. Chỉ dùng như manh mối để tìm nguồn gốc."},{"id":"x3","title":"Blog của một hãng bán phần mềm diệt virus: \"5 dấu hiệu thư lừa đảo, và vì sao bạn cần mua gói bảo vệ của chúng tôi\"","facts":["Có tên công ty và ngày đăng","Bài có mục đích bán hàng","Dấu hiệu nêu trong bài khá chung chung"],"level":"mid","why":"Nguồn xác định được người viết nhưng có lợi ích thương mại, dễ phóng đại rủi ro. Dùng để tham khảo ý tưởng, cần đối chiếu với nguồn trung lập."}],"TRUST_LEVELS":{"high":"Cao","mid":"Trung bình","low":"Thấp"},"REFLECTION":["Ở thư khó nhất, mình đã chọn gì và dựa vào dấu hiệu nào?","Điều gì làm mình bất ngờ hoặc nhầm lẫn?","Mình rút ra quy tắc nào, và quy tắc đó có áp dụng được cho thư thật trong hộp thư của mình không?","Lần tới nhận thư tương tự, mình sẽ làm gì trước khi bấm?"],"KOLB":[{"stage":"Trải nghiệm cụ thể","where":"Chặng 1: phân loại 12 thư"},{"stage":"Quan sát phản ánh","where":"Đọc phản hồi, xem lại thư làm sai"},{"stage":"Khái quát hóa","where":"Chặng 2: rút ra quy tắc ba lớp"},{"stage":"Thử nghiệm tích cực","where":"Chặng 3, 6 và luyện tập ngoài lớp"}],"LESSON":[{"n":1,"name":"Khởi động: phân loại nhanh","min":15,"theory":"Hành vi","tool":"Google Forms, hoặc Chặng 1 của học liệu","samr":"A","tpack":"PK, TPK","mode":"Chặng 1","work":"Sinh viên làm 12 thư, chọn phương án và đánh dấu dấu hiệu, đọc phản hồi ngay sau mỗi thư. Giáo viên theo dõi tỷ lệ chọn từng phương án."},{"n":2,"name":"Phân tích có hướng dẫn","min":15,"theory":"Nhận thức","tool":"Google Slides, hoặc Chặng 2","samr":"S, A","tpack":"TCK, PCK","mode":"Chặng 2","work":"Giáo viên phân tích thư số 1 theo ba lớp trên trang có chú thích. Sinh viên làm lớp người gửi của thư số 5, rồi hai lớp sau của thư số 6."},{"n":3,"name":"Giải quyết thư tình huống","min":25,"theory":"Kiến tạo","tool":"Google Docs, hoặc Chặng 3","samr":"M","tpack":"TPK, TPACK","mode":"Chặng 3","work":"Nhóm bốn người, bốn vai, phân tích thư T theo ba lớp, ghi bằng chứng, thảo luận bất đồng và chọn kết luận kèm hành động."},{"n":4,"name":"Đối chiếu nguồn","min":10,"theory":"Kết nối","tool":"Google Sheets, tìm kiếm, hoặc Chặng 4","samr":"M","tpack":"TK, CK","mode":"Chặng 4","work":"Mỗi nhóm điền một thẻ nguồn cho nguồn giáo viên cung cấp, tìm thêm một nguồn thứ hai để kiểm chứng thư T."},{"n":5,"name":"Phản biện chéo và sửa","min":15,"theory":"Kiến tạo, kết nối","tool":"Google Docs, Forms, hoặc Chặng 5","samr":"M","tpack":"TPACK","mode":"Chặng 5","work":"Hai nhóm đổi tài liệu, bình luận phản biện có trích dẫn, sửa kết luận. Giáo viên tổng kết lỗi phổ biến từ số liệu của hoạt động 1."},{"n":6,"name":"Đánh giá cá nhân và phản ánh","min":10,"theory":"Kolb","tool":"Google Forms, hoặc Chặng 6","samr":"A","tpack":"PCK, TPACK","mode":"Chặng 6","work":"Sinh viên phân loại 4 thư mới, giải thích một thư bằng ba lớp, trả lời bốn câu hỏi phản ánh."},{"n":7,"name":"Ngoài lớp","min":20,"theory":"Kolb, kết nối","tool":"Bảng tự theo dõi, Google Sheets","samr":"A, M","tpack":"XK, TPACK","mode":"Ngoài lớp","work":"Áp dụng ba lớp cho năm thư trong hộp thư của mình, chỉ ghi số thư, kết luận và dấu hiệu, không chép nội dung thư. Một sinh viên khác đối chiếu thẻ nguồn của nhóm."}],"RUBRIC":[{"crit":"Phân loại 4 thư mới","pts":3,"who":"Biểu mẫu hoặc học liệu tự chấm","good":"Đúng ít nhất 3 trong 4 thư, kể cả không nghi nhầm thư thật"},{"crit":"Giải thích một thư bằng ba lớp","pts":3,"who":"Giáo viên (học liệu chỉ chấm sơ bộ phần chọn lớp)","good":"Nêu bằng chứng cho đủ ba lớp, trích đúng chỗ trong thư"},{"crit":"Hành động an toàn","pts":2,"who":"Giáo viên (học liệu chấm sơ bộ phần chọn hành động)","good":"Nêu được ít nhất hai hành động phù hợp với thư vừa phân tích, không chọn hành động nguy hiểm"},{"crit":"Thẻ nguồn","pts":1,"who":"Giáo viên hoặc bạn học","good":"Đủ sáu mục, mức tin cậy có lý do"},{"crit":"Phản ánh","pts":1,"who":"Giáo viên","good":"Trả lời cụ thể ít nhất ba trong bốn câu, dẫn một thư cụ thể"}],"OBJECTIVES":["Dùng ba lớp kiểm tra (người gửi, liên kết, nội dung và yêu cầu) để giải thích vì sao một thư là lừa đảo, thật hay chưa chắc.","Nêu được các hành động an toàn khi nhận thư đáng ngờ: không bấm liên kết, không đọc hay gửi mã OTP, kiểm tra qua kênh chính thức, báo cho nơi có trách nhiệm.","Đánh giá được độ tin cậy của một nguồn thông tin bằng thẻ nguồn sáu mục.","Phản biện được kết luận của nhóm khác bằng bằng chứng trích từ thư."],"THEORY_NOTES":[{"mode":"Chặng 1","theory":"Học thuyết hành vi","why":"Nhiều lượt luyện, phản hồi tức thì sau mỗi câu trả lời, theo ý tưởng máy dạy học của Skinner. Bước này làm lộ quan niệm sai của chính bạn."},{"mode":"Chặng 2","theory":"Học thuyết nhận thức","why":"Gom dấu hiệu rời rạc thành ba lớp dễ nhớ, mỗi trang chỉ một lớp, có chú thích dẫn hướng, ví dụ mẫu rồi giảm dần phần làm mẫu (Sweller, Mayer)."},{"mode":"Chặng 3 và 5","theory":"Học thuyết kiến tạo","why":"Bất đồng trong nhóm thử thách hiểu biết cá nhân (Piaget); bạn cùng nhóm hỗ trợ nhau trong vùng phát triển gần với giàn giáo là vai trò, mẫu và tiêu chí (Vygotsky, Wood)."},{"mode":"Chặng 4","theory":"Học thuyết kết nối","why":"Tri thức nằm trong mạng nguồn. Năng lực then chốt là chọn và đánh giá nguồn, nên thẻ nguồn biến câu hỏi mơ hồ thành sáu câu hỏi cụ thể (Siemens)."},{"mode":"Chặng 6","theory":"Chu trình Kolb","why":"Từ trải nghiệm, ngẫm lại, rút quy tắc đến thử nghiệm mới ở thư chưa từng thấy."}],"META":{"audience":"Sinh viên năm nhất (khoảng 40 người mỗi lớp); mở rộng được cho học sinh trung học phổ thông và người dùng phổ thông","duration":"90 phút trên lớp và 20 phút luyện tập ngoài lớp","kind":"Học liệu số tương tác dạng tình huống mô phỏng (có kèm bản in và tài liệu giảng viên)","tech":"Một tệp HTML chạy offline trên trình duyệt hiện đại (máy tính, điện thoại); không cần cài đặt, không gửi dữ liệu đi đâu; tiến độ lưu ngay trên thiết bị","privacy":"Toàn bộ thư là mô phỏng. Học liệu không thu thập thông tin cá nhân, không có ô nhập mật khẩu. Tên bạn nhập ở giấy chứng nhận chỉ nằm trên thiết bị của bạn.","standards":"Mục tiêu gắn với Khung năng lực số cho người học (Thông tư 02/2025/TT-BGDĐT): nhóm An toàn, nhóm Khai thác dữ liệu và thông tin"},"QUALITY_CHECK":[{"crit":"Mục tiêu rõ và đo được","how":"Bốn mục tiêu viết theo việc sinh viên làm được; rubric 10 điểm gắn với từng mục tiêu."},{"crit":"Nội dung chính xác, cập nhật","how":"Dấu hiệu lừa đảo, hành động an toàn và nguồn đều có trong báo cáo kèm tài liệu tham khảo; số liệu nêu rõ nguồn."},{"crit":"Phương pháp sư phạm phù hợp","how":"Mỗi chặng ứng với một học thuyết đã phân tích ở mục 2.1 và 2.2 của báo cáo; chuỗi từ phản hồi tức thì đến lập luận nhóm."},{"crit":"Tính tương tác và phản hồi","how":"Người học chọn, đánh dấu, rê chuột kiểm tra liên kết, nhận phản hồi cụ thể và gợi ý ba mức."},{"crit":"Thiết kế và khả năng sử dụng","how":"Giao diện hộp thư quen thuộc, chữ rõ, dùng được trên điện thoại, có hướng dẫn ngắn ở mỗi chặng."},{"crit":"Khả năng tiếp cận và công bằng","how":"Chạy offline; có bản in cho lớp thiếu thiết bị; không dựa vào màu sắc duy nhất để truyền đạt."},{"crit":"An toàn và quyền riêng tư","how":"Dữ liệu mô phỏng, tên miền .example, không có ô nhập mật khẩu, không gửi dữ liệu ra ngoài."},{"crit":"Khả năng tái sử dụng và chỉnh sửa","how":"Bộ thư nằm trong một khối dữ liệu riêng, thêm hoặc sửa thư không cần viết lại chương trình; có bản Excel và Word để chỉnh."},{"crit":"Bản quyền và nguồn mở","how":"Nội dung do nhóm biên soạn; giấy phép đề xuất CC BY-NC-SA 4.0; tài liệu tham khảo có trích dẫn đầy đủ."}],"REFS":["B. F. Skinner, “Teaching machines,” *Science*, vol. 128, no. 3330, pp. 969–977, 1958, doi: 10.1126/science.128.3330.969.","J. Sweller, “Cognitive load during problem solving: Effects on learning,” *Cognitive Science*, vol. 12, no. 2, pp. 257–285, 1988, doi: 10.1207/s15516709cog1202_4.","R. E. Mayer, “Cognitive theory of multimedia learning,” in *The Cambridge Handbook of Multimedia Learning*, 2nd ed., R. E. Mayer, Ed. Cambridge, U.K.: Cambridge University Press, 2014, pp. 43–71, doi: 10.1017/CBO9781139547369.005.","J. Piaget, *The Origins of Intelligence in Children*, M. Cook, Trans. New York, NY, USA: International Universities Press, 1952.","L. S. Vygotsky, *Mind in Society: The Development of Higher Psychological Processes*, M. Cole, V. John-Steiner, S. Scribner, and E. Souberman, Eds. Cambridge, MA, USA: Harvard University Press, 1978.","D. Wood, J. S. Bruner, and G. Ross, “The role of tutoring in problem solving,” *Journal of Child Psychology and Psychiatry*, vol. 17, no. 2, pp. 89–100, 1976, doi: 10.1111/j.1469-7610.1976.tb00381.x.","G. Siemens, “Connectivism: A learning theory for the digital age,” *International Journal of Instructional Technology and Distance Learning*, vol. 2, no. 1, Jan. 2005. Truy cập: 17/10/2026. [Trực tuyến]. Có tại: https://www.itdl.org/Journal/Jan_05/article01.htm","D. A. Kolb, *Experiential Learning: Experience as the Source of Learning and Development*. Englewood Cliffs, NJ, USA: Prentice-Hall, 1984.","P. Mishra and M. J. Koehler, “Technological pedagogical content knowledge: A framework for teacher knowledge,” *Teachers College Record*, vol. 108, no. 6, pp. 1017–1054, 2006, doi: 10.1111/j.1467-9620.2006.00684.x.","R. R. Puentedura, “SAMR and TPCK: An introduction,” Mar. 28, 2013. Truy cập: 17/10/2026. [Trực tuyến]. Có tại: https://www.hippasus.com/rrpweblog/archives/2013/03/28/SAMRandTPCK_AnIntroduction.pdf","P. Kumaraguru, Y. Rhee, A. Acquisti, L. F. Cranor, J. Hong, and E. Nunge, “Protecting people from phishing: The design and evaluation of an embedded training email system,” in *Proc. SIGCHI Conf. Human Factors in Computing Systems (CHI ’07)*, San Jose, CA, USA, 2007, pp. 905–914, doi: 10.1145/1240624.1240760.","Bộ Giáo dục và Đào tạo, “Thông tư số 02/2025/TT-BGDĐT ngày 24/01/2025 ban hành Khung năng lực số cho người học,” Hà Nội, Việt Nam, 2025. Truy cập: 16/10/2026. [Trực tuyến]. Có tại: https://thuvienphapluat.vn/van-ban/EN/Giao-duc/Circular-02-2025-TT-BGDDT-Digital-Competence-Framework/646278/tieng-anh.aspx","“Google và NCSC hợp tác ra mắt website DauHieuLuaDao.com giúp người dùng nhận biết về lừa đảo trực tuyến,” Google Vietnam Blog, 01/04/2022. Truy cập: 17/10/2026. [Trực tuyến]. Có tại: https://vietnamese.googleblog.com/2022/04/google-va-ncsc-hop-tac-ra-mat-website.html","Trọng Đạt, “Bí kíp để không trở thành nạn nhân của lừa đảo qua mail,” VietNamNet, 18/10/2021. Truy cập: 17/10/2026. [Trực tuyến]. Có tại: https://vietnamnet.vn/bi-kip-de-khong-tro-thanh-nan-nhan-cua-lua-dao-qua-mail-784009.html","“Việt Nam ghi nhận hơn 1.500 vụ lừa đảo trực tuyến, thiệt hại ước tính 1.660 tỷ đồng,” VnEconomy, 01/11/2025. Truy cập: 17/10/2026. [Trực tuyến]. Có tại: https://vneconomy.vn/viet-nam-ghi-nhan-hon-1500-vu-lua-dao-truc-tuyen-thiet-hai-uoc-tinh-1660-ty-dong.htm"],"TEAMINFO":{"name":"","members":""}};
'use strict';
/* ===== Lõi: dữ liệu, trạng thái, tiện ích, hiển thị thư ===== */
const D = DATA;
const E_MAIN = D.EMAILS.filter(e => e.set === 'main');
const E_T = D.EMAILS.find(e => e.id === 'T');
const BY_ID = {};
[...D.EMAILS, ...D.PRE, ...D.POST].forEach(e => { BY_ID[e.id] = e; });
const MY_DOMAIN = 'dhmau.example';
const QUICK_IDS = ['1', '5', '6', '7', '8'];
const IN_FRAME = (() => { try { return window.self !== window.top; } catch (e) { return true; } })();
const VICON = { scam: '✕', real: '✓', unsure: '?' };
const SICON = { ok: '✓', bad: '✕', warn: '?', na: '–' };
const LAYER_BY = {};
D.LAYERS.forEach(l => { LAYER_BY[l.id] = l; });
const SIGN_BY = {};
D.SIGNS.forEach(s => { SIGN_BY[s.id] = s; });
const SIGN_GROUPS = [
  { name: 'Người gửi', layer: 'sender', ids: ['S1', 'S2', 'S9'] },
  { name: 'Liên kết và tệp đính kèm', layer: 'link', ids: ['S3', 'S8', 'S10'] },
  { name: 'Nội dung và yêu cầu', layer: 'content', ids: ['S4', 'S5', 'S6', 'S7'] },
  { name: 'Khác', layer: null, ids: ['S0'] },
];
const STATUS_IDLE = 'Rê chuột (hoặc nhấn giữ) lên một liên kết để xem địa chỉ đích trước khi bấm.';

/* ---------- DOM ---------- */
function h(tag, attrs, ...kids) {
  const el = document.createElement(tag);
  let val;
  if (attrs) {
    for (const k in attrs) {
      const v = attrs[k];
      if (v == null || v === false) continue;
      if (k === 'class') el.className = v;
      else if (k === 'html') el.innerHTML = v;
      else if (k === 'value') val = v;
      else if (k.slice(0, 2) === 'on') el.addEventListener(k.slice(2), v);
      else if (v === true) el.setAttribute(k, '');
      else el.setAttribute(k, v);
    }
  }
  for (const kid of kids.flat(Infinity)) {
    if (kid == null || kid === false) continue;
    el.append(kid.nodeType ? kid : document.createTextNode(String(kid)));
  }
  if (val !== undefined) el.value = val;
  return el;
}
const $ = (s, r) => (r || document).querySelector(s);
const $$ = (s, r) => [...(r || document).querySelectorAll(s)];
function mount(el, ...kids) {
  while (el.firstChild) el.removeChild(el.firstChild);
  el.append(...kids.flat(Infinity).filter(k => k != null && k !== false).map(k => (k.nodeType ? k : document.createTextNode(String(k)))));
  return el;
}
const rec = (obj, k, init) => (obj[k] || (obj[k] = init));

/* ---------- Trạng thái ---------- */
const KEY = 'tthm.v1';
const defaults = () => ({
  level: 'guided', path: 'full', usePre: false, name: '', teacher: false,
  pre: { a: {}, done: false }, s1: {}, s2: {}, s3: {}, s4: { ex: {}, card: {} }, s5: {}, s6: { test: { a: {}, done: false }, ex: {}, acts: {}, refl: [] },
  off: [], clicks: {}, done: {}, tally: {},
});
function loadState() {
  try {
    const r = localStorage.getItem(KEY);
    if (r) return Object.assign(defaults(), JSON.parse(r));
  } catch (e) { /* bỏ qua */ }
  return defaults();
}
let S = loadState();
let saveTimer;
function save() {
  clearTimeout(saveTimer);
  saveTimer = setTimeout(() => { try { localStorage.setItem(KEY, JSON.stringify(S)); } catch (e) { /* bỏ qua */ } }, 150);
}
function resetAll() {
  S = defaults();
  try { localStorage.removeItem(KEY); } catch (e) { /* bỏ qua */ }
}

/* ---------- Thông báo, hộp thoại, sao chép ---------- */
let toastTimer;
function toast(msg) {
  let t = $('#toast');
  if (!t) { t = h('div', { id: 'toast', class: 'toast', role: 'status', 'aria-live': 'polite' }); document.body.append(t); }
  t.textContent = msg;
  t.classList.add('on');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => t.classList.remove('on'), 2600);
}
function modal(o) {
  const prev = document.activeElement;
  let ov;
  const close = () => { ov.remove(); document.removeEventListener('keydown', onKey); if (prev && prev.focus) prev.focus(); };
  const onKey = ev => { if (ev.key === 'Escape') close(); };
  const ok = h('button', { class: 'btn', type: 'button', onclick: close }, o.okLabel || 'Đã hiểu');
  const actions = o.actions ? o.actions(close) : ok;
  ov = h('div', { class: 'overlay', role: 'dialog', 'aria-modal': 'true', 'aria-label': o.title, onclick: ev => { if (ev.target === ov) close(); } },
    h('div', { class: 'modal' + (o.wide ? ' wide' : '') },
      h('h2', null, o.title),
      h('div', { class: 'modal-body' }, o.body),
      h('div', { class: 'modal-actions' }, actions)));
  document.body.append(ov);
  document.addEventListener('keydown', onKey);
  setTimeout(() => { const f = $('button, textarea, input', ov); if (f) f.focus(); }, 0);
  return { close };
}
async function copyText(text, label) {
  try { await navigator.clipboard.writeText(text); toast(label || 'Đã sao chép'); return true; } catch (e) { /* thử cách khác */ }
  const ta = h('textarea', { class: 'ghost', readonly: true }, text);
  document.body.append(ta);
  ta.select();
  let ok = false;
  try { ok = document.execCommand('copy'); } catch (e) { ok = false; }
  ta.remove();
  toast(ok ? (label || 'Đã sao chép') : 'Chưa sao chép được. Hãy bôi đen văn bản trong ô và sao chép thủ công.');
  return ok;
}
function exportBox(text, filename, rows) {
  const ta = h('textarea', { class: 'in mono-in', readonly: true, rows: rows || 8, 'aria-label': 'Nội dung xuất' }, text);
  const bar = h('div', { class: 'row gap' },
    h('button', { class: 'btn sec', type: 'button', onclick: () => { copyText(text); ta.select(); } }, 'Sao chép'),
    !IN_FRAME && filename ? h('button', {
      class: 'btn sec', type: 'button', onclick: () => {
        const a = h('a', { href: URL.createObjectURL(new Blob([text], { type: 'text/plain;charset=utf-8' })), download: filename });
        document.body.append(a); a.click(); a.remove();
      },
    }, 'Tải về') : null);
  return h('div', { class: 'stack' }, ta, bar);
}
function encodeCode(obj) { return 'TTHT1:' + btoa(unescape(encodeURIComponent(JSON.stringify(obj)))); }
function decodeCode(s) {
  const t = (s || '').trim().replace(/^TTHT1:/, '');
  return JSON.parse(decodeURIComponent(escape(atob(t))));
}

/* ---------- Tên miền ---------- */
const hostOf = u => { try { return new URL(u).hostname; } catch (e) { return ''; } };
const baseDomain = host => host.split('.').slice(-2).join('.');
const isOwn = u => baseDomain(hostOf(u)) === MY_DOMAIN;

/* ---------- Dấu hiệu, chấm điểm ---------- */
function signResult(e, chosen) {
  const truth = e.signs;
  return {
    hit: truth.filter(s => chosen.includes(s)),
    miss: truth.filter(s => !chosen.includes(s)),
    extra: chosen.filter(s => !truth.includes(s)),
  };
}
const pct = (a, b) => (b ? Math.round((100 * a) / b) : 0);
const idsOfS1 = () => (S.path === 'quick' ? QUICK_IDS : E_MAIN.map(e => e.id));

/* ---------- Thành phần giao diện dùng chung ---------- */
function verdictButtons(cur, locked, onPick, truth) {
  return h('div', { class: 'vrow', role: 'group', 'aria-label': 'Kết luận về thư' },
    ['scam', 'real', 'unsure'].map(v => {
      const cls = ['vbtn', 'v-' + v, cur === v ? 'sel' : '', locked && truth === v ? 'truth' : '', locked && truth && cur === v && truth !== v ? 'wrong' : ''].join(' ');
      return h('button', { class: cls, type: 'button', 'aria-pressed': String(cur === v), disabled: locked, onclick: () => onPick(v) },
        h('span', { class: 'vi', 'aria-hidden': 'true' }, VICON[v]),
        h('span', null, D.VERDICTS[v]),
        locked && truth === v ? h('em', null, 'Đáp án') : null);
    }));
}
function verdictTag(v) { return h('span', { class: 'vtag v-' + v }, VICON[v] + ' ' + D.VERDICTS[v]); }
function stateBadge(s) { return h('span', { class: 'stbadge st-' + s }, SICON[s] + ' ' + D.LAYER_STATES[s]); }
function layerCards(e, only) {
  return h('div', { class: 'lcards' }, D.LAYERS.filter(l => !only || only.includes(l.id)).map(l => {
    const x = e.layers[l.id];
    return h('div', { class: 'lcard l-' + l.id },
      h('div', { class: 'lhead' }, h('span', { class: 'lnum' }, l.n), h('b', null, l.name)),
      h('div', { class: 'lbody' }, stateBadge(x.s), h('p', { class: 'lq' }, l.q), h('p', null, x.note)));
  }));
}
function signChip(id, o) {
  return h('button', {
    class: 'chip ' + (o.cls || ''), type: 'button', 'aria-pressed': String(!!o.on), disabled: o.locked, onclick: o.onclick,
  }, o.mark ? h('span', { class: 'cmark', 'aria-hidden': 'true' }, o.mark) : null, SIGN_BY[id].label);
}
function nextBtn(label, fn, disabled) {
  return h('button', { class: 'btn big', type: 'button', disabled: !!disabled, onclick: fn }, label);
}
function field(label, control, hint) {
  return h('label', { class: 'field' }, h('span', { class: 'flabel' }, label), control, hint ? h('span', { class: 'fhint' }, hint) : null);
}
function textarea(id, val, onInput, rows, ph) {
  return h('textarea', {
    class: 'in', id, rows: rows || 3, placeholder: ph || '', value: val || '',
    oninput: ev => { onInput(ev.target.value); save(); },
  });
}
function statePicker(cur, onPick, locked) {
  return h('div', { class: 'spick', role: 'radiogroup', 'aria-label': 'Trạng thái của lớp' },
    ['ok', 'bad', 'warn', 'na'].map(s => h('button', {
      class: 'sbtn st-' + s + (cur === s ? ' sel' : ''), type: 'button', role: 'radio', 'aria-checked': String(cur === s), disabled: locked, onclick: () => onPick(s),
    }, h('span', { 'aria-hidden': 'true' }, SICON[s]), ' ', D.LAYER_STATES[s])));
}

/* ---------- Hiển thị thư ---------- */
function avatarColor(name) {
  const c = ['#0F8B8D', '#A8650A', '#3A5A85', '#6B5B95', '#2E7D57', '#A6455F'];
  let s = 0;
  for (const ch of name) s = (s * 31 + ch.charCodeAt(0)) >>> 0;
  return c[s % c.length];
}
function inlineMarkup(line, o) {
  const out = [];
  const re = /\[\[(c|l):([^\]]+)\]\]/g;
  let last = 0;
  let m;
  o.seen = o.seen || {};
  while ((m = re.exec(line))) {
    if (m.index > last) out.push(line.slice(last, m.index));
    if (m[1] === 'c') {
      out.push(h('span', { class: 'ph', 'data-ev': 'content', 'data-n': o.annot && !o.seen.ph ? '3' : null }, m[2]));
      o.seen.ph = true;
    } else {
      const parts = m[2].split('|');
      out.push(h('a', { class: 'mlink', href: '#', 'data-link': parts[0], 'data-ev': 'link', 'data-n': o.annot && !o.seen.link ? '2' : null }, parts[1]));
      o.seen.link = true;
    }
    last = re.lastIndex;
  }
  if (last < line.length) out.push(line.slice(last));
  return out;
}
function linkTrap(e, id, url) {
  S.clicks[e.id] = (S.clicks[e.id] || 0) + 1;
  save();
  const own = isOwn(url);
  modal({
    title: 'Bạn vừa bấm vào một liên kết',
    body: [
      h('p', null, 'Liên kết này dẫn tới ', h('code', { class: 'mono' }, url), '.'),
      own
        ? h('p', null, 'Tên miền đích thuộc ', h('b', null, MY_DOMAIN), '. Địa chỉ khớp với trường, nhưng bạn vẫn cần xem thư có hợp lý không.')
        : h('p', null, 'Tên miền đích ', h('b', null, baseDomain(hostOf(url))), ' không thuộc tổ chức mà thư nhắc tới. Nếu đây là thư thật gửi cho bạn, trang này có thể đòi mật khẩu, mã OTP hoặc thông tin thẻ.'),
      h('p', { class: 'tip' }, 'Thói quen cần có: rê chuột hoặc nhấn giữ để xem địa chỉ đích trước khi bấm, rồi đọc tên miền từ phải sang trái. Phần đứng ngay trước đuôi (.example, .vn, .com) cho biết ai sở hữu trang.'),
      h('p', { class: 'muted' }, 'Trong học liệu này không có trang nào được mở. Mọi thư và địa chỉ đều là mô phỏng.'),
    ],
  });
}
function attTrap(e, att) {
  S.clicks[e.id] = (S.clicks[e.id] || 0) + 1;
  save();
  modal({
    title: 'Bạn vừa thử mở một tệp đính kèm',
    body: [
      h('p', null, 'Tệp ', h('code', { class: 'mono' }, att.name), ' (', att.size, ') là tệp nén. Tệp nén từ người gửi chưa xác minh có thể chứa chương trình độc hại.'),
      h('p', { class: 'tip' }, 'Thói quen cần có: xác nhận người gửi qua kênh khác trước khi tải hoặc mở tệp.'),
      h('p', { class: 'muted' }, 'Trong học liệu này không có tệp thật nào được tải.'),
    ],
  });
}
function mailView(e, o = {}) {
  const expanded = o.expand != null ? o.expand : S.level === 'guided';
  const card = h('article', { class: 'mail' + (o.annot ? ' annot' : '') + (o.evidence ? ' ev-on' : '') + (o.showPh ? ' show-ph' : ''), 'aria-label': 'Thư: ' + e.subject });
  const status = h('div', { class: 'mstatus', role: 'status', 'aria-live': 'polite' }, STATUS_IDLE);
  const addrRow = h('div', { class: 'addr-row' });
  const drawAddr = open => {
    mount(addrRow, open
      ? h('span', { class: 'addr', 'data-ev': 'sender', 'data-n': o.annot ? '1' : null }, '<' + e.from.addr + '>')
      : h('button', { type: 'button', class: 'linkbtn', onclick: ev => { ev.stopPropagation(); drawAddr(true); } }, 'Xem địa chỉ người gửi'));
  };
  drawAddr(expanded);
  const body = h('div', { class: 'mail-body' }, e.body.map(par => {
    const p = h('p');
    par.split('\n').forEach((line, i) => { if (i) p.append(h('br')); p.append(...inlineMarkup(line, o)); });
    return p;
  }));
  const atts = (e.attachments || []).length
    ? h('div', { class: 'atts' }, e.attachments.map(a => h('button', { type: 'button', class: 'att', 'data-ev': 'link', 'data-att': a.name }, '📎 ', a.name, ' ', h('small', null, a.size))))
    : null;
  card.append(...[
    h('header', { class: 'mail-head' },
      h('div', { class: 'avatar', style: 'background:' + avatarColor(e.from.name), 'aria-hidden': 'true' }, e.from.name.trim().charAt(0).toUpperCase()),
      h('div', { class: 'mail-from' },
        h('div', { class: 'who-row' }, h('b', { class: 'who', 'data-ev': 'sender' }, e.from.name), h('span', { class: 'time' }, e.time)),
        addrRow,
        h('div', { class: 'to' }, 'Đến: tôi (' + D.BRAND.me + ')'))),
    h('h3', { class: 'subject' }, e.subject),
    e.context ? h('p', { class: 'ctx' }, e.context) : null,
    body,
    atts,
    status].filter(Boolean));
  const show = txt => { status.textContent = txt; status.classList.toggle('on', txt !== STATUS_IDLE); };
  const urlOf = el => { const l = e.links[el.dataset.link]; return l || ''; };
  card.addEventListener('mouseover', ev => { const lk = ev.target.closest('.mlink'); if (lk) show('Đích đến: ' + urlOf(lk)); });
  card.addEventListener('mouseout', ev => { if (ev.target.closest('.mlink')) show(STATUS_IDLE); });
  card.addEventListener('focusin', ev => { const lk = ev.target.closest('.mlink'); if (lk) show('Đích đến: ' + urlOf(lk)); });
  card.addEventListener('focusout', ev => { if (ev.target.closest('.mlink')) show(STATUS_IDLE); });
  card.addEventListener('click', ev => {
    const lk = ev.target.closest('.mlink');
    if (lk) ev.preventDefault();
    const t = ev.target.closest('[data-ev]');
    if (!t || !card.contains(t)) return;
    if (o.evidence) {
      $$('[data-ev="' + t.dataset.ev + '"].picked', card).forEach(x => x.classList.remove('picked'));
      t.classList.add('picked');
      if (o.onEv) o.onEv(t.dataset.ev, t.textContent.replace(/^📎\s*/, '').trim(), t);
      return;
    }
    if (lk) { const url = urlOf(lk); show('Đích đến: ' + url); (o.onLink || linkTrap)(e, lk.dataset.link, url); }
    else if (t.dataset.att) { const att = e.attachments.find(a => a.name === t.dataset.att); (o.onAtt || attTrap)(e, att); }
  });
  card.setHighlight = layer => { card.dataset.hl = layer || ''; };
  card.setPhrases = on => card.classList.toggle('show-ph', !!on);
  return card;
}

/* ===== Khung ứng dụng: thanh trên, các chặng, trang chủ, sổ tay ===== */
const ui = {};
let view = 'home';
let viewCleanup = null;
const STAGES = [
  { id: 'chang0', n: '0', name: 'Kiểm tra đầu vào', min: 5, opt: true },
  { id: 'chang1', n: '1', name: 'Phân loại nhanh', min: 15 },
  { id: 'chang2', n: '2', name: 'Phân tích có hướng dẫn', min: 15 },
  { id: 'chang3', n: '3', name: 'Thư tình huống', min: 25, group: true },
  { id: 'chang4', n: '4', name: 'Đối chiếu nguồn', min: 10 },
  { id: 'chang5', n: '5', name: 'Phản biện chéo', min: 15, group: true },
  { id: 'chang6', n: '6', name: 'Đánh giá và phản ánh', min: 10 },
  { id: 'ngoailop', n: '7', name: 'Ngoài lớp', min: 20 },
];
const PATHS = {
  full: { name: 'Cả buổi 90 phút', stages: ['chang1', 'chang2', 'chang3', 'chang4', 'chang5', 'chang6', 'ngoailop'] },
  self: { name: 'Tự học', stages: ['chang1', 'chang2', 'chang4', 'chang6', 'ngoailop'] },
  quick: { name: 'Thử nhanh', stages: ['chang1'] },
};
const stageById = id => STAGES.find(s => s.id === id);
function pathStages() {
  const p = PATHS[S.path] || PATHS.full;
  return (S.usePre && S.path !== 'quick' ? ['chang0'] : []).concat(p.stages);
}
function nextStageId(cur) {
  const list = pathStages();
  const i = list.indexOf(cur);
  if (i >= 0) return list[i + 1] || null;
  const idx = STAGES.findIndex(s => s.id === cur);
  return list.find(id => STAGES.findIndex(s => s.id === id) > idx) || null;
}
function finishBtn(cur) {
  const n = nextStageId(cur);
  const label = n ? 'Sang Chặng ' + stageById(n).n + ': ' + stageById(n).name : 'Về trang chủ';
  return nextBtn(label, () => { S.done[cur] = true; save(); go(n || 'home'); });
}

/* ---------- Điều hướng ---------- */
function go(v) {
  if (viewCleanup) { viewCleanup(); viewCleanup = null; }
  view = v;
  try { if (location.hash.slice(1) !== v) history.replaceState(null, '', '#' + v); } catch (e) { /* khung chặn đổi URL */ }
  render();
  window.scrollTo(0, 0);
}
function render() {
  if (viewCleanup) { viewCleanup(); viewCleanup = null; }
  mount($('#app'), topbar(), stepperNode(), h('main', { class: 'wrap main', id: 'main', tabindex: '-1' }, viewNode()), footer());
}
function viewNode() {
  const fn = VIEWS[view] || VIEWS.home;
  try { return fn(); } catch (err) {
    console.error(err);
    return h('div', { class: 'card' }, 'Có lỗi khi hiển thị mục này. Hãy tải lại trang. Chi tiết: ' + err.message);
  }
}

/* ---------- Thanh trên, các chặng, chân trang ---------- */
function logo() {
  return h('span', {
    class: 'logo', 'aria-hidden': 'true',
    html: '<svg viewBox="0 0 40 40" width="34" height="34"><rect x="3" y="9" width="26" height="19" rx="3" fill="none" stroke="currentColor" stroke-width="2.4"/><path d="M4 11l12 9 12-9" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linejoin="round"/><circle cx="27" cy="26" r="7" style="fill:var(--top)" stroke="#F2A541" stroke-width="2.8"/><path d="M32 31l6 6" stroke="#F2A541" stroke-width="3.2" stroke-linecap="round"/></svg>',
  });
}
function topbar() {
  const nb = (label, fn, on) => h('button', { class: 'tnav' + (on ? ' on' : ''), type: 'button', onclick: fn, 'aria-current': on ? 'page' : null }, label);
  return h('header', { class: 'topbar' }, h('div', { class: 'wrap topbar-in' },
    h('button', { class: 'brand', type: 'button', onclick: () => go('home'), 'aria-label': 'Thám Tử Hộp Thư, về trang chủ' }, logo(),
      h('span', { class: 'brand-t' }, h('b', null, 'Thám Tử Hộp Thư'), h('small', null, 'Học liệu số'))),
    h('nav', { class: 'topnav', 'aria-label': 'Tiện ích' },
      nb('Sổ tay ba lớp', openNotebook),
      nb('Kho thư', () => go('khothu'), view === 'khothu'),
      nb('Giảng viên', () => go('giangvien'), view === 'giangvien'),
      nb('Về học liệu', () => go('gioithieu'), view === 'gioithieu'))));
}
function stepperNode() {
  if (!stageById(view)) return null;
  const rec_ = pathStages();
  return h('nav', { class: 'stepper', 'aria-label': 'Các chặng' }, h('div', { class: 'wrap stepper-in' },
    STAGES.filter(s => !s.opt || (S.usePre && S.path !== 'quick') || view === s.id).map(s => {
      const cls = ['step', view === s.id ? 'cur' : '', S.done[s.id] ? 'done' : '', rec_.includes(s.id) ? 'rec' : 'skip'].join(' ');
      return h('button', { class: cls, type: 'button', 'aria-current': view === s.id ? 'step' : null, onclick: () => go(s.id) },
        h('span', { class: 'num' }, S.done[s.id] ? '✓' : s.n), h('span', null, s.name), h('small', null, s.min + '′'));
    })));
}
function footer() {
  const t = D.TEAMINFO && D.TEAMINFO.name ? ' · Nhóm ' + D.TEAMINFO.name : '';
  return h('footer', { class: 'foot' }, h('div', { class: 'wrap' },
    h('p', null, 'Thám Tử Hộp Thư v' + D.BRAND.version + t + ' · Học phần ' + D.BRAND.course + ', ' + D.BRAND.school),
    h('p', null, 'Mọi thư, tổ chức và tên miền trong học liệu là mô phỏng (đuôi .example). Học liệu không thu thập thông tin cá nhân.')));
}
function stageHead(id, sub) {
  const s = stageById(id);
  const li = s.n >= '1' && s.n <= '6' ? D.LESSON[Number(s.n) - 1] : (id === 'ngoailop' ? D.LESSON[6] : null);
  const note = D.THEORY_NOTES.find(t => new RegExp('Chặng ' + s.n + '\\b').test(t.mode) || t.mode.includes('và ' + s.n));
  return h('header', { class: 'phead' },
    h('p', { class: 'eyebrow' }, (s.n === '7' ? 'Ngoài lớp' : 'Chặng ' + s.n) + ' · ' + s.min + ' phút' + (s.group ? ' · làm việc nhóm' : '')),
    h('h1', null, s.name),
    sub ? h('p', { class: 'lead' }, sub) : null,
    li ? h('p', { class: 'muted small' }, 'Việc của bạn: ' + li.work) : null,
    note ? h('details', { class: 'why' }, h('summary', null, 'Vì sao học thế này: ' + note.theory), h('p', null, note.why)) : null);
}
function pageHead(eyebrow, title, sub) {
  return h('header', { class: 'phead' }, h('p', { class: 'eyebrow' }, eyebrow), h('h1', null, title), sub ? h('p', { class: 'lead' }, sub) : null);
}

/* ---------- Sổ tay ba lớp ---------- */
const GLOSSARY = [
  ['Tên miền', 'Phần địa chỉ sau dấu @ của thư hoặc sau https:// của liên kết, ví dụ dhmau.example. Chủ sở hữu là phần đứng ngay trước đuôi.'],
  ['Tên miền con', 'Phần thêm vào phía trước tên miền, như thuvien.dhmau.example. Tên miền con vẫn thuộc về dhmau.example.'],
  ['Tên hiển thị và địa chỉ gửi', 'Tên hiển thị ai cũng tự đặt được. Địa chỉ gửi và tên miền của nó mới là thứ cần đọc.'],
  ['OTP', 'Mã dùng một lần để chính bạn xác nhận trên trang hoặc ứng dụng chính thức. Không ai có quyền xin mã này qua thư hay điện thoại.'],
  ['Lừa đảo qua thư', 'Thư giả danh một tổ chức hoặc người quen để dụ bạn đưa thông tin hoặc tiền.'],
  ['Kênh chính thức', 'Cách liên hệ bạn tự tìm từ nguồn đáng tin (cổng thông tin, số in trên thẻ), không lấy từ chính thư đang đáng ngờ.'],
];
function notebookNode() {
  return h('div', { class: 'stack' },
    h('p', null, 'Với mọi thư, kiểm tra lần lượt ba lớp. Một lớp đạt vẫn chưa đủ để tin thư.'),
    h('div', { class: 'lcards' }, D.LAYERS.map(l => h('div', { class: 'lcard l-' + l.id },
      h('div', { class: 'lhead' }, h('span', { class: 'lnum' }, l.n), h('b', null, l.name)), h('div', { class: 'lbody' }, h('p', null, l.q))))),
    h('h3', null, 'Mười dấu hiệu thường gặp'),
    h('ul', { class: 'plain' }, D.SIGNS.filter(s => s.id !== 'S0').map(s => h('li', null, h('b', null, s.id), ' ', s.label))),
    h('h3', null, 'Khi nghi ngờ, hãy'),
    h('ul', null, D.ACTIONS.filter(a => a.good).map(a => h('li', null, a.text))),
    h('h3', null, 'Từ cần biết'),
    h('dl', { class: 'gloss' }, GLOSSARY.map(g => [h('dt', null, g[0]), h('dd', null, g[1])])));
}
function openNotebook() { modal({ title: 'Sổ tay ba lớp', wide: true, body: notebookNode(), okLabel: 'Đóng' }); }

/* ---------- Trang chủ ---------- */
function home() {
  const ex = E_MAIN[0];
  const mail = mailView(ex, { expand: true, annot: true, showPh: true, onLink: () => toast('Đây là ví dụ minh họa. Vào Chặng 1 để luyện với 12 thư.') });
  const started = Object.keys(S.s1).length > 0;
  const nextUndone = pathStages().find(id => !S.done[id]);
  const choice = (label, on, fn) => h('button', { class: 'chip big', type: 'button', 'aria-pressed': String(on), onclick: fn }, label);
  const pcard = (k, t, d, meta) => h('button', {
    class: 'pcard', type: 'button',
    onclick: () => { S.path = k; save(); go(pathStages()[0]); },
  }, h('b', null, t), h('span', null, d), h('small', null, meta));
  return h('div', { class: 'stack xl' },
    h('section', { class: 'hero' },
      h('div', { class: 'hero-copy stack' },
        h('p', { class: 'eyebrow' }, 'Học liệu số · ' + D.BRAND.course),
        h('h1', null, 'Thám Tử Hộp Thư'),
        h('p', { class: 'lead' }, 'Luyện nhận diện và xử lý thư điện tử lừa đảo qua 12 thư mô phỏng. Mỗi thư được kiểm tra bằng ba lớp: người gửi, liên kết, nội dung và yêu cầu.'),
        started && nextUndone ? h('div', { class: 'row gap' },
          h('button', { class: 'btn big', type: 'button', onclick: () => go(nextUndone) }, 'Tiếp tục: ' + stageById(nextUndone).name),
          h('span', { class: 'muted small' }, 'Tiến độ lưu ngay trên thiết bị này.')) : null),
      h('div', { class: 'hero-mail stack' }, mail,
        h('ul', { class: 'legend' }, D.LAYERS.map(l => h('li', { class: 'l-' + l.id }, h('span', { class: 'lnum' }, l.n), h('span', null, h('b', null, l.name), ': ' + l.q)))))),
    h('section', { class: 'stack' },
      h('h2', null, 'Chọn cách học'),
      h('div', { class: 'opts' },
        h('div', { class: 'opt' }, h('span', { class: 'olabel' }, 'Mức hỗ trợ'),
          choice('Có hướng dẫn: hiện sẵn địa chỉ người gửi', S.level === 'guided', () => { S.level = 'guided'; save(); render(); }),
          choice('Tự lực: phải bấm mới thấy địa chỉ', S.level === 'solo', () => { S.level = 'solo'; save(); render(); })),
        h('div', { class: 'opt' }, h('span', { class: 'olabel' }, 'Đo tiến bộ'),
          choice('Không đo trước', !S.usePre, () => { S.usePre = false; save(); render(); }),
          choice('Làm 4 thư kiểm tra đầu vào', S.usePre, () => { S.usePre = true; save(); render(); }))),
      h('div', { class: 'pcards' },
        pcard('full', PATHS.full.name, 'Sáu chặng theo đúng giáo án: phân loại, phân tích, thư tình huống của nhóm, đối chiếu nguồn, phản biện chéo, đánh giá. Dùng khi học cùng lớp.', '90 phút + 20 phút ngoài lớp'),
        pcard('self', PATHS.self.name, 'Bỏ hai chặng làm việc nhóm (3 và 5). Hợp để học một mình hoặc ôn trước giờ học.', 'Khoảng 50 phút'),
        pcard('quick', PATHS.quick.name, 'Năm thư chọn lọc kèm quy tắc ba lớp, để biết bài học này có gì.', 'Khoảng 10 phút')),
      h('div', { class: 'row gap wrap-row' },
        h('button', { class: 'btn sec', type: 'button', onclick: () => go('khothu') }, 'Ôn lại trong Kho thư'),
        h('button', { class: 'btn sec', type: 'button', onclick: () => go('giangvien') }, 'Góc giảng viên'),
        h('button', { class: 'btn sec', type: 'button', onclick: openNotebook }, 'Mở Sổ tay ba lớp'))),
    h('section', { class: 'split' },
      h('div', { class: 'card stack' },
        h('h2', null, 'Bạn sẽ làm được gì'),
        h('ul', null, D.OBJECTIVES.map(o => h('li', null, o)))),
      h('div', { class: 'card stack' },
        h('h2', null, 'Đi kèm trong gói'),
        h('ul', null,
          h('li', null, 'Bộ thẻ bài và phiếu in cho lớp thiếu thiết bị hoặc mất mạng.'),
          h('li', null, 'Infographic một trang tóm tắt báo cáo và học liệu.'),
          h('li', null, 'Tài liệu giảng viên: kịch bản 90 phút, đáp án, rubric.'),
          h('li', null, 'Sổ tính Excel để phân tích số liệu từ lần dạy thử thật.')),
        h('p', { class: 'muted small' }, 'An toàn: toàn bộ thư là mô phỏng, không có ô nhập mật khẩu, không có liên kết thật. Tên bạn nhập ở phiếu kết quả chỉ nằm trên thiết bị này.'))));
}

/* ===== Chặng 0 (đầu vào), Chặng 1 (phân loại nhanh), bộ chạy kiểm tra dùng chung ===== */

/* ---------- Bộ chạy kiểm tra: dùng cho Chặng 0 và Chặng 6a ---------- */
function testRunner(set, store, opts) {
  const root = h('div', { class: 'stack lg' });
  const bar = h('div', { class: 'card row gap spread' });
  const holders = {};
  const mails = {};
  const fbHolders = {};
  const n = () => set.filter(e => store.a[e.id] === e.verdict).length;
  const drawVerdict = e => mount(holders[e.id], verdictButtons(store.a[e.id], store.done, v => { store.a[e.id] = v; save(); drawVerdict(e); drawBar(); }, store.done && opts.feedback ? e.verdict : null));
  const drawFb = e => {
    if (!store.done) { mount(fbHolders[e.id]); return; }
    const ok = store.a[e.id] === e.verdict;
    mount(fbHolders[e.id],
      h('p', null, h('span', { class: 'vtag ' + (ok ? 'v-real' : 'v-scam') }, ok ? '✓ Đúng' : '✕ Sai'),
        opts.feedback ? [' Đáp án: ', verdictTag(e.verdict)] : null),
      opts.feedback ? h('div', { class: 'stack' }, h('p', null, h('b', null, 'Giải thích: '), e.explain), layerCards(e)) : null);
  };
  const drawBar = () => {
    const all = set.every(e => store.a[e.id]);
    mount(bar, store.done
      ? [h('div', null, h('b', null, 'Kết quả: ' + n() + '/' + set.length + ' thư đúng.'), h('p', { class: 'muted small' }, opts.feedback ? 'Xem giải thích dưới từng thư.' : 'Chưa hiện đáp án và giải thích ở bước này. Phản hồi chi tiết có ở các chặng sau.'))]
      : [h('span', { class: 'muted' }, 'Đã chọn ' + set.filter(e => store.a[e.id]).length + '/' + set.length + ' thư.'),
        h('button', { class: 'btn', type: 'button', disabled: !all, onclick: () => { store.done = true; save(); set.forEach(e => { drawVerdict(e); drawFb(e); mails[e.id].setPhrases(opts.feedback); }); drawBar(); if (opts.onDone) opts.onDone(); } }, 'Nộp bài')]);
  };
  set.forEach((e, i) => {
    holders[e.id] = h('div');
    fbHolders[e.id] = h('div', { class: 'stack' });
    mails[e.id] = mailView(e, { showPh: false });
    root.append(h('section', { class: 'card tcase stack' }, h('b', null, 'Thư ' + (i + 1) + '/' + set.length), mails[e.id], h('h3', null, 'Kết luận của bạn'), holders[e.id], fbHolders[e.id]));
    drawVerdict(e);
    drawFb(e);
    if (store.done) mails[e.id].setPhrases(opts.feedback);
  });
  root.append(bar);
  drawBar();
  return root;
}
function chang0() {
  return h('div', { class: 'stack lg' },
    stageHead('chang0', 'Bốn thư, mỗi thư một kết luận. Bước này chưa hiện đáp án, để có số đo trước khi học. Bạn có thể bỏ qua nếu không cần đo tiến bộ.'),
    testRunner(D.PRE, S.pre, { feedback: false, onDone: () => { S.done.chang0 = true; save(); } }),
    finishBtn('chang0'));
}

/* ---------- Chặng 1 ---------- */
function verdictMessage(e, v) {
  const t = e.verdict;
  if (v === t) return t === 'unsure' ? 'Chọn "chưa chắc" rồi đi kiểm chứng là cách làm đúng khi các lớp chưa đủ căn cứ.' : null;
  if (t === 'real' && v === 'scam') return 'Bạn nghi nhầm một thư thật. Nghi nhầm cũng có giá: bạn có thể bỏ lỡ thông báo cần thiết, và khi thư nào cũng đáng ngờ thì khó nhận ra thư nguy hiểm thật.';
  if (t === 'scam' && v === 'real') return 'Bạn bỏ sót một thư lừa đảo. Đây là loại sai nguy hiểm hơn, vì bạn có thể làm theo yêu cầu trong thư.';
  if (t === 'unsure') return 'Thư này chưa đủ căn cứ để kết luận chắc chắn theo hướng nào. Câu trả lời an toàn là kiểm chứng qua kênh khác.';
  if (v === 'unsure' && t === 'scam') return 'Bạn chọn "chưa chắc", nhưng các lớp đã cho đủ căn cứ để coi đây là thư lừa đảo.';
  if (v === 'unsure' && t === 'real') return 'Bạn chọn "chưa chắc", nhưng ba lớp đều ổn nên có thể tin thư này, dù vẫn không đưa mật khẩu hay mã OTP cho ai.';
  return null;
}
function signPicker(e, a, redraw) {
  const res = a.done ? signResult(e, a.signs) : null;
  const toggle = id => {
    if (a.done) return;
    const i = a.signs.indexOf(id);
    if (i >= 0) a.signs.splice(i, 1);
    else if (id === 'S0') a.signs = ['S0'];
    else { a.signs = a.signs.filter(s => s !== 'S0'); a.signs.push(id); }
    save();
    redraw();
  };
  const chip = id => {
    let cls = '';
    let mark = '';
    if (res) {
      if (res.hit.includes(id)) { cls = 'hit'; mark = '✓'; } else if (res.extra.includes(id)) { cls = 'extra'; mark = '✕'; } else if (res.miss.includes(id)) { cls = 'miss'; mark = '!'; }
    }
    return signChip(id, { on: a.signs.includes(id), cls, mark, locked: a.done, onclick: () => toggle(id) });
  };
  if (S.level === 'guided') {
    return h('div', { class: 'stack' }, SIGN_GROUPS.map(g => h('div', { class: 'sgroup' + (g.layer ? ' l-' + g.layer : '') },
      g.name ? h('p', { class: 'sg-name' }, g.name) : null, h('div', { class: 'chips' }, g.ids.map(chip)))));
  }
  return h('div', { class: 'chips' }, D.SIGNS.map(s => chip(s.id)));
}
function hintBlock(e, a, redraw) {
  return h('div', { class: 'hints' },
    a.hints > 0 ? h('ol', { class: 'hintlist' }, e.hints.slice(0, a.hints).map(t => h('li', null, t))) : null,
    a.hints < e.hints.length
      ? h('button', { class: 'btn ghost', type: 'button', onclick: () => { a.hints++; save(); redraw(); } }, 'Cho tôi gợi ý (' + a.hints + '/' + e.hints.length + ')')
      : h('span', { class: 'muted small' }, 'Đã dùng hết gợi ý.'));
}
function s1Feedback(e, a, idx, ids, redraw) {
  const ok = a.v === e.verdict;
  const res = signResult(e, a.signs);
  const msg = verdictMessage(e, a.v);
  const allDone = ids.every(id => S.s1[id] && S.s1[id].done);
  const last = idx === ids.length - 1;
  const clicks = S.clicks[e.id] || 0;
  const nextIdx = ids.findIndex((id, i) => i > idx && !(S.s1[id] && S.s1[id].done));
  return h('section', { class: 'card fb stack ' + (ok ? 'ok' : 'bad'), 'aria-live': 'polite' },
    h('div', { class: 'fb-head' },
      h('span', { class: 'fb-ic', 'aria-hidden': 'true' }, ok ? '✓' : '✕'),
      h('div', null, h('h3', null, ok ? 'Đúng rồi.' : 'Chưa đúng.'), h('p', null, 'Đáp án: ', verdictTag(e.verdict)))),
    msg ? h('p', null, msg) : null,
    h('div', null,
      h('p', null, h('b', null, 'Dấu hiệu: '), res.hit.length + '/' + e.signs.length + ' dấu hiệu đúng.'),
      res.miss.length ? h('p', null, 'Bạn bỏ sót: ', res.miss.map(s => SIGN_BY[s].label).join('; '), '.') : null,
      res.extra.length ? h('p', null, 'Không có trong thư này: ', res.extra.map(s => SIGN_BY[s].label).join('; '), '.') : null),
    clicks && e.verdict !== 'real' ? h('p', { class: 'note-warn' }, 'Bạn đã bấm vào liên kết hoặc tệp của thư này ' + clicks + ' lần trước khi kết luận. Ngoài đời, một lần bấm đã có thể đủ để rơi vào bẫy.') : null,
    h('h4', null, 'Ba lớp kiểm tra'),
    layerCards(e),
    h('p', null, h('b', null, 'Vì sao: '), e.explain),
    h('p', null, h('b', null, 'Nên làm gì: '), e.action),
    h('div', { class: 'row gap' },
      !last && nextIdx >= 0 ? nextBtn('Thư tiếp theo', () => { ui.s1i = nextIdx; redraw(); }) : null,
      !last && nextIdx < 0 && !allDone ? nextBtn('Làm thư còn lại', () => { ui.s1i = ids.findIndex(id => !(S.s1[id] && S.s1[id].done)); redraw(); }) : null,
      !last && nextIdx < 0 && allDone ? nextBtn('Xem tổng kết', () => { ui.s1sum = true; redraw(); }) : null,
      last && allDone ? nextBtn('Xem tổng kết', () => { ui.s1sum = true; redraw(); }) : null,
      last && !allDone ? nextBtn('Làm thư còn lại', () => { ui.s1i = ids.findIndex(id => !(S.s1[id] && S.s1[id].done)); redraw(); }) : null));
}
function s1Mailbox(ids, redraw) {
  const idx = Math.min(ui.s1i, ids.length - 1);
  const e = BY_ID[ids[idx]];
  const a = rec(S.s1, e.id, { v: null, signs: [], hints: 0, done: false, ok: false });
  const doneN = ids.filter(id => S.s1[id] && S.s1[id].done).length;
  const mail = mailView(e, { showPh: a.done });
  const panel = h('div', { class: 'stack' });
  const list = h('nav', { class: 'mlist', 'aria-label': 'Danh sách thư' });
  const drawList = () => mount(list, ids.map((id, i) => {
    const x = S.s1[id];
    const em = BY_ID[id];
    const st = x && x.done ? (x.ok ? 'ok' : 'bad') : '';
    return h('button', { class: 'mitem' + (i === idx ? ' cur' : '') + (st ? ' ' + st : ''), type: 'button', 'aria-current': i === idx ? 'true' : null, onclick: () => { ui.s1i = i; redraw(); } },
      h('span', { class: 'mi-n' }, st === 'ok' ? '✓' : st === 'bad' ? '✕' : String(i + 1)),
      h('span', { class: 'mi-t' }, h('b', null, em.from.name), h('small', null, em.subject)));
  }));
  const drawPanel = () => {
    mount(panel,
      h('section', { class: 'card answer stack' },
        h('h3', null, '1. Bạn kết luận thế nào?'),
        verdictButtons(a.v, a.done, v => { a.v = v; save(); drawPanel(); }, a.done ? e.verdict : null),
        h('h3', null, '2. Bạn thấy những dấu hiệu nào?'),
        signPicker(e, a, drawPanel),
        !a.done ? hintBlock(e, a, drawPanel) : null,
        !a.done ? h('div', { class: 'row gap' },
          h('button', {
            class: 'btn', type: 'button', disabled: !a.v,
            onclick: () => { a.done = true; a.ok = a.v === e.verdict; save(); mail.setPhrases(true); drawList(); drawPanel(); },
          }, 'Kiểm tra câu trả lời'),
          !a.v ? h('span', { class: 'muted small' }, 'Chọn một kết luận để kiểm tra.') : null) : null),
      a.done ? s1Feedback(e, a, idx, ids, redraw) : null);
  };
  drawList();
  drawPanel();
  return h('div', { class: 'stack lg' },
    h('div', { class: 'prog', role: 'progressbar', 'aria-valuemin': '0', 'aria-valuemax': String(ids.length), 'aria-valuenow': String(doneN), 'aria-label': 'Tiến độ Chặng 1' },
      h('div', { class: 'bar', style: 'width:' + pct(doneN, ids.length) + '%' }), h('span', null, doneN + '/' + ids.length + ' thư')),
    h('div', { class: 'box' }, list, h('div', { class: 'stack' }, mail, panel)),
    doneN === ids.length ? h('div', { class: 'row' }, h('button', { class: 'btn sec', type: 'button', onclick: () => { ui.s1sum = true; redraw(); } }, 'Xem tổng kết')) : null);
}
function s1Summary(ids, redraw) {
  const rows = ids.map(id => ({ e: BY_ID[id], a: S.s1[id] || {} })).filter(r => r.a.done);
  const ok = rows.filter(r => r.a.ok).length;
  let hit = 0;
  let tot = 0;
  let hints = 0;
  rows.forEach(r => { hit += signResult(r.e, r.a.signs).hit.length; tot += r.e.signs.length; hints += r.a.hints || 0; });
  const cm = { scam: { scam: 0, real: 0, unsure: 0 }, real: { scam: 0, real: 0, unsure: 0 }, unsure: { scam: 0, real: 0, unsure: 0 } };
  rows.forEach(r => { cm[r.e.verdict][r.a.v]++; });
  const picked = (id, v) => { const x = S.s1[id]; return x && x.done && x.v === v; };
  const mis = [];
  if (picked('7', 'scam') || picked('12', 'scam')) mis.push('Thư có giọng thông báo hoặc có hạn chót chưa chắc là lừa đảo. Thư 7 và 12 được đặt vào để kiểm tra phản xạ này: hãy hỏi thư có đòi thông tin nhạy cảm hoặc kéo bạn sang kênh lạ không.');
  if (picked('6', 'real')) mis.push('Địa chỉ gửi trông đúng chưa đủ. Thư 6 chỉ lộ ra ở lớp liên kết: tên miền đích khác dhmau.example.');
  if (picked('5', 'real')) mis.push('Thư 5 không có chữ nào đáng sợ. Lỗi nằm ở tên miền dhrnau.example, giả dhmau.example bằng cặp chữ r và n đứng sát nhau.');
  if (picked('8', 'scam') || picked('8', 'real')) mis.push('Thư 8 không đủ căn cứ để kết luận theo hướng nào. Cách làm đúng là kiểm chứng qua kênh khác trước khi mở tệp nén.');
  if (picked('11', 'scam')) mis.push('Mã xác thực ở thư 11 là thư thật vì bạn vừa tự đăng nhập. Bối cảnh quyết định kết luận. Nếu bạn không vừa đăng nhập mà nhận mã, đó mới là tín hiệu có người đang thử vào tài khoản bạn.');
  if (picked('3', 'real') || picked('4', 'real') || picked('2', 'real')) mis.push('Thư đòi OTP, đòi tiền trước hoặc đòi ảnh giấy tờ là dấu hiệu rõ nhất. Hãy ghi nhớ ba thứ không đưa qua thư: mật khẩu, mã OTP, giấy tờ cá nhân.');
  const wrongRows = rows.filter(r => !r.a.ok);
  const cell = (t, v) => h('td', { class: cm[t][v] ? 'nz' : '' }, String(cm[t][v]));
  const clicksTotal = Object.keys(S.clicks).reduce((s, k) => s + S.clicks[k], 0);
  return h('div', { class: 'stack lg' },
    h('section', { class: 'card stack' },
      h('h2', null, 'Tổng kết Chặng 1'),
      h('div', { class: 'stats' },
        h('div', { class: 'stat' }, h('b', null, ok + '/' + rows.length), h('span', null, 'thư kết luận đúng')),
        h('div', { class: 'stat' }, h('b', null, hit + '/' + tot), h('span', null, 'dấu hiệu bắt đúng')),
        h('div', { class: 'stat' }, h('b', null, String(hints)), h('span', null, 'lần dùng gợi ý')),
        h('div', { class: 'stat' }, h('b', null, String(clicksTotal)), h('span', null, 'lần bấm liên kết hoặc tệp'))),
      h('p', { class: 'muted small' }, 'Các số này chỉ là kết quả của chính bạn trên thiết bị này. Ở lớp, giáo viên tổng hợp tỷ lệ chọn từng phương án để chọn lỗi phổ biến nói ở Chặng 5.')),
    h('section', { class: 'card stack' },
      h('h3', null, 'Bạn nhầm theo hướng nào?'),
      h('div', { class: 'tblwrap' }, h('table', { class: 'tbl cm' },
        h('thead', null, h('tr', null, h('th', null, 'Đáp án đúng \\ Bạn chọn'), h('th', null, 'Lừa đảo'), h('th', null, 'Thật'), h('th', null, 'Chưa chắc'))),
        h('tbody', null,
          h('tr', null, h('th', null, 'Lừa đảo'), cell('scam', 'scam'), cell('scam', 'real'), cell('scam', 'unsure')),
          h('tr', null, h('th', null, 'Thật'), cell('real', 'scam'), cell('real', 'real'), cell('real', 'unsure')),
          h('tr', null, h('th', null, 'Chưa chắc'), cell('unsure', 'scam'), cell('unsure', 'real'), cell('unsure', 'unsure'))))),
      h('p', null, 'Nghi nhầm thư thật: ', h('b', null, String(cm.real.scam)), ' thư. Bỏ sót thư lừa đảo: ', h('b', null, String(cm.scam.real)), ' thư. Hai loại sai này khác bản chất: loại sau nguy hiểm hơn, loại trước làm bạn mất thông tin cần thiết.')),
    mis.length ? h('section', { class: 'card stack' }, h('h3', null, 'Điều nên rút ra'), h('ul', null, mis.map(m => h('li', null, m)))) : null,
    wrongRows.length ? h('section', { class: 'card stack' },
      h('h3', null, 'Xem lại thư làm sai'),
      h('div', { class: 'chips' }, wrongRows.map(r => h('button', { class: 'chip', type: 'button', onclick: () => { ui.s1i = ids.indexOf(r.e.id); ui.s1sum = false; redraw(); } }, 'Thư ' + r.e.id + ': ' + r.e.subject)))) : null,
    h('div', { class: 'row gap' },
      h('button', { class: 'btn sec', type: 'button', onclick: () => { ui.s1sum = false; redraw(); } }, 'Xem lại từng thư'),
      finishBtn('chang1')));
}
function chang1() {
  const ids = idsOfS1();
  const rootEl = h('div', { class: 'stack lg' });
  if (ui.s1i == null || ui.s1i >= ids.length) { const f = ids.findIndex(id => !(S.s1[id] && S.s1[id].done)); ui.s1i = f < 0 ? 0 : f; }
  if (ui.s1sum == null) ui.s1sum = ids.every(id => S.s1[id] && S.s1[id].done);
  const draw = () => mount(rootEl,
    stageHead('chang1', S.path === 'quick' ? 'Năm thư chọn lọc. Đọc thư, kết luận, chọn dấu hiệu rồi xem phản hồi ngay.' : 'Mười hai thư trong một tuần ở hộp thư sinh viên. Đọc thư, kết luận, chọn dấu hiệu rồi xem phản hồi ngay sau mỗi thư.'),
    ui.s1sum ? s1Summary(ids, draw) : s1Mailbox(ids, draw));
  draw();
  return rootEl;
}

/* ===== Chặng 2: phân tích có hướng dẫn (làm mẫu, rồi giảm dần phần làm mẫu) ===== */
const LAYER_HINT = {
  sender: 'Đọc phần sau dấu @ của địa chỉ gửi rồi so với dhmau.example.',
  link: 'Rê chuột lên liên kết (hoặc bấm để xem địa chỉ đích) rồi so tên miền đích với dhmau.example.',
  content: 'Tìm cụm thúc giục hoặc đòi thông tin nhạy cảm. Giọng văn bình thường cũng là một kết quả.',
};
function s2Example(st, redraw) {
  const e = BY_ID['1'];
  const mail = mailView(e, { expand: true, showPh: true });
  st.tab = st.tab || 'sender';
  st.seen = st.seen || {};
  st.seen[st.tab] = true;
  mail.setHighlight(st.tab);
  const layer = LAYER_BY[st.tab];
  const x = e.layers[st.tab];
  const allSeen = D.LAYERS.every(l => st.seen[l.id]);
  return h('div', { class: 'stack lg' },
    h('p', null, 'Giáo viên làm mẫu với thư số 1. Mỗi lần chỉ nhìn một lớp: bấm lần lượt ba lớp và xem phần nào của thư được đánh dấu.'),
    h('div', { class: 'two' },
      mail,
      h('div', { class: 'stack' },
        h('div', { class: 'tabs small', role: 'tablist' }, D.LAYERS.map(l => h('button', {
          class: 'tab l-' + l.id + (st.tab === l.id ? ' cur' : '') + (st.seen[l.id] ? ' seen' : ''), type: 'button', role: 'tab', 'aria-selected': String(st.tab === l.id),
          onclick: () => { st.tab = l.id; redraw(); },
        }, l.n + '. ' + l.name))),
        h('div', { class: 'card stack' },
          h('h3', null, 'Lớp ' + layer.n + ': ' + layer.name),
          h('p', { class: 'lq' }, layer.q),
          h('p', null, stateBadge(x.s)),
          h('p', null, x.note)),
        !allSeen ? h('p', { class: 'muted small' }, 'Xem đủ cả ba lớp để sang bước tiếp.') : h('p', { class: 'note-ok' }, 'Bạn đã xem đủ ba lớp. Thư 1 có vấn đề ở cả ba lớp, nên rất dễ nhận ra.'))));
}
function s2Task(s, st, redraw, onSolved) {
  const e = BY_ID[s.id];
  const evEls = {};
  const mail = mailView(e, {
    expand: true, evidence: true,
    onEv: (layer, text) => { st.ev[s.id + '.' + layer] = text; if (evEls[layer]) evEls[layer](); },
  });
  const cards = D.LAYERS.map(l => {
    const key = s.id + '.' + l.id;
    const x = e.layers[l.id];
    const head = h('div', { class: 'lhead' }, h('span', { class: 'lnum' }, l.n), h('b', null, l.name));
    if (!s.layers.includes(l.id)) {
      return h('div', { class: 'lcard l-' + l.id + ' given' }, head,
        h('div', { class: 'lbody' }, h('span', { class: 'tag' }, 'Đã giải sẵn'), stateBadge(x.s), h('p', null, x.note)));
    }
    const a = rec(S.s2, key, { pick: null, tries: 0, solved: false, revealed: false, msg: '' });
    const body = h('div', { class: 'lbody stack' });
    const drawCard = () => {
      const ev = st.ev[key];
      mount(body,
        h('p', { class: 'lq' }, l.q),
        statePicker(a.pick, p => { a.pick = p; a.msg = ''; save(); drawCard(); }, a.solved),
        x.s === 'na' ? null : h('p', { class: 'evline' }, ev ? ['Bằng chứng bạn chọn: ', h('q', null, ev)] : 'Bấm vào chỗ trong thư là bằng chứng cho lớp này.'),
        a.solved
          ? h('div', { class: 'stack' }, h('p', { class: 'note-ok' }, a.revealed ? 'Đáp án được hiện sau 3 lần thử: ' : 'Đúng. '), stateBadge(x.s), h('p', null, x.note))
          : h('div', { class: 'stack' },
            a.msg ? h('p', { class: 'note-warn' }, a.msg) : null,
            h('div', null, h('button', { class: 'btn', type: 'button', disabled: !a.pick, onclick: () => check() }, 'Kiểm tra lớp này'))));
    };
    const check = () => {
      const hasEv = x.s === 'na' || !!st.ev[key];
      if (a.pick === x.s && hasEv) { a.solved = true; a.msg = ''; } else {
        a.tries++;
        if (a.tries >= 3) { a.solved = true; a.revealed = true; a.pick = x.s; a.msg = ''; } else a.msg = a.pick !== x.s ? 'Trạng thái chưa đúng. ' + LAYER_HINT[l.id] : 'Trạng thái đúng. Hãy chỉ ra bằng chứng của lớp này bằng cách bấm vào chỗ tương ứng trong thư.';
      }
      save();
      drawCard();
      onSolved();
    };
    evEls[l.id] = drawCard;
    drawCard();
    return h('div', { class: 'lcard l-' + l.id + ' mine' }, head, body);
  });
  return h('div', { class: 'two' }, mail, h('div', { class: 'stack' }, h('div', { class: 'lcards one' }, cards)));
}
function chang2() {
  const steps = [
    { kind: 'example', label: 'Xem làm mẫu: thư 1' },
    { kind: 'task', id: '5', layers: ['sender'], label: 'Bạn làm lớp 1: thư 5' },
    { kind: 'task', id: '6', layers: ['link', 'content'], label: 'Bạn làm lớp 2 và 3: thư 6' },
    { kind: 'rule', label: 'Quy tắc ba lớp' },
  ];
  const st = rec(ui, 's2', { step: 0, seen: {}, ev: {}, tab: 'sender' });
  const root = h('div', { class: 'stack lg' });
  const solvedAll = s => s.layers.every(l => (S.s2[s.id + '.' + l] || {}).solved);
  const stepDone = i => {
    const s = steps[i];
    if (s.kind === 'example') return D.LAYERS.every(l => st.seen[l.id]);
    if (s.kind === 'task') return solvedAll(s);
    return false;
  };
  const draw = () => {
    const s = steps[st.step];
    let nextEl;
    const refreshNext = () => { if (nextEl) nextEl.disabled = !stepDone(st.step); };
    const content = s.kind === 'example' ? s2Example(st, draw) : s.kind === 'task' ? s2Task(s, st, draw, refreshNext) : s2Rule();
    nextEl = s.kind === 'rule' ? null : h('button', { class: 'btn big', type: 'button', disabled: !stepDone(st.step), onclick: () => { st.step++; draw(); window.scrollTo(0, 0); } }, 'Tiếp: ' + steps[st.step + 1].label);
    mount(root,
      stageHead('chang2', 'Ba bước giảm dần phần làm mẫu: xem giáo viên làm, bạn làm một lớp, rồi bạn làm hai lớp.'),
      h('div', { class: 'tabs', role: 'tablist' }, steps.map((x, i) => h('button', {
        class: 'tab' + (i === st.step ? ' cur' : '') + (stepDone(i) ? ' done' : ''), type: 'button', role: 'tab', 'aria-selected': String(i === st.step),
        onclick: () => { st.step = i; draw(); },
      }, (i + 1) + '. ' + x.label))),
      content,
      nextEl ? h('div', { class: 'row' }, nextEl) : null);
  };
  draw();
  return root;
}
function s2Rule() {
  return h('div', { class: 'stack lg' },
    h('section', { class: 'card stack' },
      h('h2', null, 'Quy tắc ba lớp'),
      h('div', { class: 'lcards' }, D.LAYERS.map(l => h('div', { class: 'lcard l-' + l.id },
        h('div', { class: 'lhead' }, h('span', { class: 'lnum' }, l.n), h('b', null, l.name)), h('div', { class: 'lbody' }, h('p', null, l.q))))),
      h('ol', null,
        h('li', null, 'Đọc từng chữ của tên miền. Thư 5 chỉ lộ ra ở lớp 1 và lớp 2, vì nội dung hoàn toàn bình thường.'),
        h('li', null, 'Một lớp đạt chưa đủ. Thư 6 có địa chỉ gửi đúng nhưng liên kết sai.'),
        h('li', null, 'Chưa đủ căn cứ thì không kết luận chắc. Hãy kiểm chứng qua kênh chính thức do bạn tự tìm.'))),
    h('section', { class: 'card stack' },
      h('h3', null, 'Bạn vừa đi qua ba mức hỗ trợ'),
      h('p', null, 'Ở chặng này phần làm mẫu giảm dần: xem giáo viên làm cả ba lớp, tự làm một lớp, rồi tự làm hai lớp. Sang Chặng 3, nhóm bạn tự làm cả ba lớp với một thư chưa ai thấy.')),
    h('div', { class: 'row' }, finishBtn('chang2')));
}

/* ===== Chặng 3: giải quyết thư tình huống T (nhóm bốn người, bốn vai) ===== */
function roleOfLayer(layerId) { return D.ROLES.find(r => r.layer === layerId); }
function sheetData(st) {
  return { v: 1, team: st.team || '', layers: st.layers, disagree: st.disagree || '', verdict: st.verdict || '', acts: st.acts || [], act: st.act || '', verify: st.verify || '' };
}
function sheetText(d) {
  const lines = [];
  lines.push('PHIẾU PHÂN TÍCH NHÓM: Thư tình huống T');
  lines.push('Nhóm: ' + (d.team || '(chưa đặt tên)'));
  lines.push('');
  D.LAYERS.forEach(l => {
    const x = d.layers[l.id] || { s: '', t: '' };
    lines.push('Lớp ' + l.n + ' ' + l.name + ' | ' + (x.s ? D.LAYER_STATES[x.s] : '(chưa chọn)') + ' | ' + ((x.t || '').replace(/\n/g, ' / ') || '(chưa ghi)'));
  });
  lines.push('Điểm bất đồng và cách giải quyết: ' + (d.disagree || '(chưa ghi)').replace(/\n/g, ' / '));
  lines.push('Kết luận chung: ' + (d.verdict ? D.VERDICTS[d.verdict] : '(chưa chọn)'));
  const acts = (d.acts || []).map(id => (D.ACTIONS.find(a => a.id === id) || {}).text).filter(Boolean);
  lines.push('Hành động đề xuất: ' + [acts.join('; '), d.act].filter(Boolean).join('. ') );
  lines.push('Cách kiểm chứng ngoài thư: ' + (d.verify || '(chưa ghi)').replace(/\n/g, ' / '));
  return lines.join('\n');
}
function chang3() {
  const st = S.s3;
  st.layers = st.layers || { sender: { s: '', t: '' }, link: { s: '', t: '' }, content: { s: '', t: '' } };
  st.members = st.members || {};
  st.acts = st.acts || [];
  const u = rec(ui, 's3', { role: 0, ta: {} });
  const root = h('div', { class: 'stack lg' });
  const panel = h('div', { class: 'stack' });
  const mail = mailView(E_T, {
    expand: true, evidence: true,
    onEv: (layer, text) => {
      const ta = u.ta[layer];
      if (!ta) { toast('Phần này thuộc vai "' + roleOfLayer(layer).name + '". Chuyển sang vai đó để ghi bằng chứng.'); return; }
      ta.value += (ta.value ? '\n' : '') + '“' + text + '”';
      st.layers[layer].t = ta.value;
      save();
    },
  });
  const tabs = h('div', { class: 'tabs', role: 'tablist' });
  const drawTabs = () => mount(tabs, D.ROLES.map((r, i) => h('button', {
    class: 'tab' + (u.role === i ? ' cur' : ''), type: 'button', role: 'tab', 'aria-selected': String(u.role === i),
    onclick: () => { u.role = i; drawTabs(); drawPanel(); },
  }, 'Vai ' + (i + 1) + ': ' + r.name.replace('Người ', ''))));
  const roleLayerPanel = (r, layerId) => {
    const l = LAYER_BY[layerId];
    const data = st.layers[layerId];
    const ta = textarea('ev-' + layerId, data.t, v => { data.t = v; }, 5, 'Bấm vào chỗ trong thư để trích dẫn, rồi viết thêm nhận xét của bạn.');
    ta.readOnly = !!st.locked;
    u.ta[layerId] = ta;
    return h('div', { class: 'card stack' },
      h('h3', null, r.name),
      h('ul', null, r.tasks.map(t => h('li', null, t))),
      h('p', { class: 'lq' }, 'Lớp ' + l.n + ': ' + l.q),
      statePicker(data.s, s => { data.s = s; save(); drawPanel(); }, st.locked),
      field('Bằng chứng trích từ thư', ta, 'Bấm vào địa chỉ, liên kết hoặc cụm từ trong thư để chèn trích dẫn.'));
  };
  const missing = () => {
    const m = [];
    D.LAYERS.forEach(l => { const x = st.layers[l.id]; if (!x.s) m.push('trạng thái lớp ' + l.n); if ((x.t || '').trim().length < 10) m.push('bằng chứng lớp ' + l.n); });
    if (!st.verdict) m.push('kết luận chung');
    if (!(st.acts.length || (st.act || '').trim().length >= 10)) m.push('hành động đề xuất');
    if ((st.verify || '').trim().length < 10) m.push('cách kiểm chứng ngoài thư');
    return m;
  };
  let refreshLock = () => {};
  const summaryPanel = () => {
    const miss = missing();
    const missEl = h('p', { class: miss.length ? 'muted' : 'note-ok' }, miss.length ? 'Còn thiếu: ' + miss.join(', ') + '.' : 'Phiếu đã đủ các mục.');
    const lockBtn = h('button', { class: 'btn', type: 'button', disabled: miss.length > 0, onclick: () => { st.locked = true; save(); drawPanel(); } }, 'Chốt phiếu của nhóm');
    refreshLock = () => {
      const m = missing();
      missEl.className = m.length ? 'muted' : 'note-ok';
      missEl.textContent = m.length ? 'Còn thiếu: ' + m.join(', ') + '.' : 'Phiếu đã đủ các mục.';
      lockBtn.disabled = m.length > 0;
    };
    return h('div', { class: 'stack' },
      h('div', { class: 'card stack' },
        h('h3', null, D.ROLES[3].name),
        h('ul', null, D.ROLES[3].tasks.map(t => h('li', null, t))),
        h('div', { class: 'tblwrap' }, h('table', { class: 'tbl' },
          h('thead', null, h('tr', null, h('th', null, 'Lớp'), h('th', null, 'Nhận định'), h('th', null, 'Bằng chứng'))),
          h('tbody', null, D.LAYERS.map(l => { const x = st.layers[l.id]; return h('tr', null, h('td', null, l.n + '. ' + l.name), h('td', null, x.s ? stateBadge(x.s) : '(chưa chọn)'), h('td', null, x.t || '(chưa ghi)')); })))),
        field('Điểm bất đồng trong nhóm và cách giải quyết', textarea('s3-dis', st.disagree, v => { st.disagree = v; refreshLock(); }, 3, 'Ai có nhận định khác nhau, vì sao, và nhóm chọn thế nào?')),
        h('h4', null, 'Kết luận chung'),
        verdictButtons(st.verdict, st.locked, v => { st.verdict = v; save(); drawPanel(); }),
        h('h4', null, 'Hành động đề xuất'),
        h('div', { class: 'chips' }, D.ACTIONS.map(a => h('button', {
          class: 'chip' + (st.acts.includes(a.id) ? ' on' : ''), type: 'button', 'aria-pressed': String(st.acts.includes(a.id)), disabled: !!st.locked,
          onclick: () => { const i = st.acts.indexOf(a.id); if (i >= 0) st.acts.splice(i, 1); else st.acts.push(a.id); save(); drawPanel(); },
        }, a.text))),
        field('Ghi thêm hành động cụ thể', textarea('s3-act', st.act, v => { st.act = v; refreshLock(); }, 2, 'Nhóm sẽ làm gì trước khi bấm hoặc trả lời?')),
        field('Cách kiểm chứng ngoài thư', textarea('s3-ver', st.verify, v => { st.verify = v; refreshLock(); }, 2, 'Kênh chính thức nào và nguồn thứ hai nào?'))),
      st.locked ? null : h('div', { class: 'card stack' }, missEl, h('div', null, lockBtn)));
  };
  const closing = () => {
    const d = sheetData(st);
    const text = sheetText(d);
    const code = encodeCode(d);
    const same = st.verdict === E_T.verdict;
    return h('div', { class: 'stack' },
      h('div', { class: 'card stack' },
        h('h3', null, 'Phiếu của nhóm đã chốt'),
        h('p', null, 'Gửi mã phiếu cho nhóm khác để họ phản biện ở Chặng 5, hoặc dán văn bản vào tài liệu nhóm của lớp.'),
        h('h4', null, 'Văn bản phiếu'), exportBox(text, 'phieu-nhom.txt', 9),
        h('h4', null, 'Mã phiếu (dán vào Chặng 5 của nhóm bạn)'), exportBox(code, 'ma-phieu.txt', 3),
        h('div', null, h('button', { class: 'btn sec', type: 'button', onclick: () => { st.locked = false; save(); drawPanel(); } }, 'Mở lại để sửa'))),
      h('div', { class: 'card stack' },
        h('h3', null, 'Gợi ý của giáo viên cho thư T'),
        h('p', null, 'Kết luận gợi ý: ', verdictTag(E_T.verdict), same ? ' Nhóm bạn chọn cùng kết luận.' : ' Nhóm bạn chọn: ' + D.VERDICTS[st.verdict] + '. Hãy xem lại xem bằng chứng của nhóm có đủ để chắc chắn như vậy không.'),
        layerCards(E_T),
        h('p', null, h('b', null, 'Vì sao: '), E_T.explain),
        h('p', null, h('b', null, 'Nên làm gì: '), E_T.action)));
  };
  const drawPanel = () => {
    u.ta = {};
    const r = D.ROLES[u.role];
    mount(panel, u.role < 3 ? roleLayerPanel(r, r.layer) : summaryPanel(), st.locked ? closing() : null);
  };
  drawTabs();
  drawPanel();
  mount(root,
    stageHead('chang3', 'Nhóm bốn người, mỗi người một vai. Thư T chưa ai thấy, không có đáp án cho tới khi nhóm chốt phiếu.'),
    h('details', { class: 'card setup', open: !st.team }, h('summary', null, 'Thiết lập nhóm'),
      h('div', { class: 'grid2' },
        field('Tên nhóm', h('input', { class: 'in', id: 's3-team', type: 'text', value: st.team || '', oninput: ev => { st.team = ev.target.value; save(); } })),
        D.ROLES.map((r, i) => field('Người giữ vai ' + (i + 1), h('input', { class: 'in', id: 's3-m' + i, type: 'text', value: st.members[r.id] || '', placeholder: r.name, oninput: ev => { st.members[r.id] = ev.target.value; save(); } }))))),
    h('div', { class: 'two sticky-left' }, mail, h('div', { class: 'stack' }, tabs, panel)),
    h('div', { class: 'row' }, finishBtn('chang3')));
  return root;
}

/* ===== Chặng 4: đối chiếu nguồn bằng thẻ nguồn sáu mục ===== */
const SRC_TYPES = ['Cơ quan nhà nước hoặc tổ chức chuyên môn', 'Doanh nghiệp hoặc tổ chức thương mại', 'Báo điện tử', 'Bài nghiên cứu hoặc sách', 'Mạng xã hội hoặc diễn đàn', 'Khác'];
function sampleSourceCard(c) {
  return h('article', { class: 'srccard' },
    h('span', { class: 'tr tr-' + c.level }, 'Mức tin cậy: ' + D.TRUST_LEVELS[c.level]),
    h('dl', null, D.SOURCE_FIELDS.map(f => [h('dt', null, f.label), h('dd', null, c[f.id] || '')])));
}
function chang4() {
  const st = S.s4;
  st.ex = st.ex || {};
  st.card = st.card || {};
  const root = h('div', { class: 'stack lg' });
  const exBox = h('div', { class: 'stack' });
  const drawEx = () => mount(exBox, D.SOURCE_EXERCISES.map(x => {
    const a = st.ex[x.id];
    return h('article', { class: 'card stack' },
      h('h4', null, x.title),
      h('ul', null, x.facts.map(f => h('li', null, f))),
      h('div', { class: 'vrow', role: 'group', 'aria-label': 'Mức tin cậy' }, ['high', 'mid', 'low'].map(l => h('button', {
        class: 'vbtn lv-' + l + (a === l ? ' sel' : '') + (a && x.level === l ? ' truth' : '') + (a && a === l && x.level !== l ? ' wrong' : ''),
        type: 'button', 'aria-pressed': String(a === l), onclick: () => { st.ex[x.id] = l; save(); drawEx(); },
      }, h('span', null, 'Tin cậy ' + D.TRUST_LEVELS[l].toLowerCase())))),
      a ? h('p', { class: a === x.level ? 'note-ok' : 'note-warn' }, (a === x.level ? 'Khớp gợi ý. ' : 'Gợi ý của giáo viên là mức ' + D.TRUST_LEVELS[x.level].toLowerCase() + '. ') + x.why) : null);
  }));
  const cardBox = h('div', { class: 'stack' });
  const filled = () => D.SOURCE_FIELDS.filter(f => (st.card[f.id] || '').trim().length >= 3).length;
  const drawCard = () => {
    const statusEl = h('p');
    const expoHolder = h('div');
    const upd = () => {
      const ok = filled() === D.SOURCE_FIELDS.length;
      statusEl.className = ok ? 'note-ok' : 'muted';
      statusEl.textContent = ok ? 'Thẻ đã đủ sáu mục.' : 'Đã điền ' + filled() + '/' + D.SOURCE_FIELDS.length + ' mục.';
      mount(expoHolder, exportBox(D.SOURCE_FIELDS.map(f => (st.card[f.id] || '').replace(/\s+/g, ' ')).join('\t'), 'the-nguon.tsv', 3));
    };
    mount(cardBox,
      h('div', { class: 'grid2' }, D.SOURCE_FIELDS.map(f => f.id === 'type'
        ? field(f.label, h('select', { class: 'in', id: 's4-' + f.id, value: st.card[f.id] || '', onchange: ev => { st.card[f.id] = ev.target.value; save(); upd(); } }, h('option', { value: '' }, 'Chọn loại nguồn'), SRC_TYPES.map(t => h('option', { value: t }, t))))
        : field(f.label, textarea('s4-' + f.id, st.card[f.id], v => { st.card[f.id] = v; upd(); }, f.id === 'trust' ? 3 : 2)))),
      statusEl,
      h('details', null, h('summary', null, 'Sao chép thẻ thành một dòng để dán vào Google Sheets'), expoHolder));
    upd();
  };
  drawEx();
  drawCard();
  mount(root,
    stageHead('chang4', 'Thư nghi ngờ thì cần nguồn thứ hai để kiểm chứng. Thẻ nguồn biến câu hỏi "nguồn này có tin được không" thành sáu câu hỏi cụ thể.'),
    h('section', { class: 'card stack' },
      h('h2', null, 'A. Đọc ba thẻ nguồn mẫu'),
      h('p', null, 'Ba thẻ lấy từ các nguồn trong báo cáo, xếp ba mức tin cậy khác nhau. Chú ý cột lý do: mức tin cậy luôn đi kèm căn cứ.'),
      h('div', { class: 'srcgrid' }, D.SOURCE_SAMPLES.map(sampleSourceCard))),
    h('section', { class: 'stack' },
      h('h2', null, 'B. Bạn xếp mức tin cậy'),
      h('p', null, 'Ba nguồn về chủ đề lừa đảo trực tuyến. Chọn mức bạn thấy hợp lý, rồi xem gợi ý.'),
      exBox),
    h('section', { class: 'card stack' },
      h('h2', null, 'C. Thẻ nguồn của nhóm bạn cho thư T'),
      h('p', null, 'Quỹ Học bổng Mẫu là tổ chức hư cấu, nên không có trang thật để tra cứu. Hãy mô tả nguồn thứ hai mà nhóm sẽ dùng để kiểm chứng thư T nếu nó đến từ một quỹ có thật: đó là nguồn nào, ai phát hành, và vì sao đáng tin. Không bấm liên kết trong thư để tìm nguồn.'),
      cardBox),
    h('div', { class: 'row' }, finishBtn('chang4')));
  return root;
}

/* ===== Chặng 5: phản biện chéo ===== */
const SAMPLE_SHEET = {
  team: 'Phiếu mẫu soạn để luyện phản biện, không phải bài của sinh viên nào',
  layers: {
    sender: { s: 'ok', t: '“quyhocbongmau.example” nghe giống tên một quỹ học bổng nên đáng tin.' },
    link: { s: 'ok', t: 'Liên kết cùng tên miền với người gửi nên an toàn.' },
    content: { s: 'ok', t: 'Thư không đòi mật khẩu hay tiền.' },
  },
  disagree: 'Cả nhóm thống nhất, không có ý kiến khác.',
  verdict: 'real',
  acts: [],
  act: 'Điền biểu mẫu ngay hôm nay để kịp hạn.',
  verify: '',
};
const SAMPLE_FLAWS = [
  'Bằng chứng chưa đủ. Tên quỹ nghe quen chưa chứng minh quỹ tồn tại, và liên kết cùng tên miền với người gửi chỉ cho biết hai thứ đi cùng nhau, không cho biết chúng thật. Phiếu cũng bỏ qua hạn 3 ngày ở lớp nội dung.',
  'Kết luận "Thật" quá chắc so với bằng chứng. Không lớp nào được kiểm chứng ngoài thư, nên kết luận hợp lý là "chưa chắc".',
  'Hành động chưa an toàn: điền họ tên, mã sinh viên, số điện thoại ngay trước khi biết quỹ có thật hay không.',
  'Phiếu để trống cách kiểm chứng ngoài thư. Với thư chưa chắc, đây là phần quan trọng nhất.',
];
function chang5() {
  const st = S.s5;
  st.cmt = st.cmt || {};
  st.rate = st.rate || {};
  const u = rec(ui, 's5', { err: '' });
  const root = h('div', { class: 'stack lg' });
  const body = h('div', { class: 'stack lg' });
  const sheetNode = d => h('section', { class: 'card stack sheet' },
    h('h3', null, 'Phiếu cần phản biện'),
    h('p', { class: 'muted small' }, d.team || '(nhóm chưa đặt tên)'),
    h('div', { class: 'tblwrap' }, h('table', { class: 'tbl' },
      h('thead', null, h('tr', null, h('th', null, 'Lớp'), h('th', null, 'Nhận định'), h('th', null, 'Bằng chứng nhóm ghi'))),
      h('tbody', null, D.LAYERS.map(l => { const x = (d.layers || {})[l.id] || {}; return h('tr', null, h('td', null, l.n + '. ' + l.name), h('td', null, x.s ? stateBadge(x.s) : '(trống)'), h('td', null, x.t || '(trống)')); })))),
    h('p', null, h('b', null, 'Điểm bất đồng: '), d.disagree || '(trống)'),
    h('p', null, h('b', null, 'Kết luận chung: '), d.verdict ? verdictTag(d.verdict) : '(trống)'),
    h('p', null, h('b', null, 'Hành động đề xuất: '), [(d.acts || []).map(id => (D.ACTIONS.find(a => a.id === id) || {}).text).filter(Boolean).join('; '), d.act].filter(Boolean).join('. ') || '(trống)'),
    h('p', null, h('b', null, 'Cách kiểm chứng ngoài thư: '), d.verify || '(trống)'));
  const sourceBox = () => h('section', { class: 'card stack' },
    h('h2', null, 'A. Chọn phiếu để phản biện'),
    h('div', { class: 'row gap wrap-row' },
      h('button', { class: 'btn' + (st.src === 'sample' ? '' : ' sec'), type: 'button', onclick: () => { st.src = 'sample'; st.sheet = SAMPLE_SHEET; save(); drawBody(); } }, 'Dùng phiếu mẫu có sai sót để luyện'),
      st.sheet && st.src === 'import' ? h('span', { class: 'muted' }, 'Đang dùng phiếu của nhóm bạn.') : null),
    h('p', { class: 'muted small' }, 'Hoặc dán mã phiếu mà nhóm khác gửi (mã bắt đầu bằng TTHT1:):'),
    h('textarea', { class: 'in mono-in', id: 's5-code', rows: 2, placeholder: 'TTHT1:...' }),
    u.err ? h('p', { class: 'note-warn' }, u.err) : null,
    h('div', null, h('button', {
      class: 'btn sec', type: 'button', onclick: () => {
        try { const d = decodeCode($('#s5-code').value); if (!d || !d.layers) throw new Error('x'); st.src = 'import'; st.sheet = d; u.err = ''; save(); drawBody(); } catch (e) { u.err = 'Không đọc được mã này. Hãy sao chép lại toàn bộ mã, gồm cả phần TTHT1:.'; drawBody(); }
      },
    }, 'Nạp phiếu của nhóm bạn')));
  const reviewBox = d => {
    const done = !!st.submitted;
    return h('section', { class: 'card stack' },
      h('h2', null, 'B. Phản biện bằng bốn câu hỏi'),
      h('p', null, 'Với mỗi câu hỏi, chọn Đạt hoặc Chưa đạt rồi viết bình luận có trích dẫn đúng chỗ trong phiếu.'),
      D.CRITIQUE_QUESTIONS.map((q, i) => {
        const r = st.rate[i];
        return h('div', { class: 'crit stack' },
          h('b', null, (i + 1) + '. ' + q),
          h('div', { class: 'row gap' }, ['ok', 'no'].map(k => h('button', {
            class: 'chip' + (r === k ? ' on' : ''), type: 'button', 'aria-pressed': String(r === k), disabled: done,
            onclick: () => { st.rate[i] = k; save(); drawBody(); },
          }, k === 'ok' ? '✓ Đạt' : '✕ Chưa đạt'))),
          field('Bình luận có trích dẫn', textarea('s5-c' + i, st.cmt[i], v => { st.cmt[i] = v; }, 2, 'Ví dụ: Ở lớp 2, phiếu ghi “…”. Điều này chưa đủ vì…')));
      }),
      h('h3', null, 'Sửa kết luận sau phản biện'),
      verdictButtons(st.rv, done, v => { st.rv = v; save(); drawBody(); }),
      field('Hành động đề xuất sau khi sửa', textarea('s5-ra', st.ra, v => { st.ra = v; }, 2)),
      !done ? h('div', null, h('button', {
        class: 'btn', type: 'button', disabled: D.CRITIQUE_QUESTIONS.some((q, i) => !st.rate[i]) || !st.rv,
        onclick: () => { st.submitted = true; save(); drawBody(); },
      }, 'Nộp phản biện')) : h('div', null, h('button', { class: 'btn sec', type: 'button', onclick: () => { st.submitted = false; save(); drawBody(); } }, 'Mở lại để sửa')));
  };
  const resultBox = d => {
    const text = ['PHẢN BIỆN CHÉO', 'Nhóm được phản biện: ' + (d.team || '(chưa đặt tên)')]
      .concat(D.CRITIQUE_QUESTIONS.map((q, i) => (i + 1) + '. ' + q + ' | ' + (st.rate[i] === 'ok' ? 'Đạt' : 'Chưa đạt') + ' | ' + ((st.cmt[i] || '').replace(/\n/g, ' / ') || '(không bình luận)')))
      .concat(['Kết luận đề nghị sau phản biện: ' + (st.rv ? D.VERDICTS[st.rv] : ''), 'Hành động đề nghị: ' + (st.ra || '')]).join('\n');
    const isSample = st.src === 'sample';
    const caught = isSample ? D.CRITIQUE_QUESTIONS.filter((q, i) => st.rate[i] === 'no').length : 0;
    return h('section', { class: 'card stack' },
      h('h2', null, 'C. Kết quả'),
      isSample ? h('div', { class: 'stack' },
        h('p', null, 'Phiếu mẫu cố ý có sai sót ở cả bốn câu hỏi. Bạn đã đánh dấu "Chưa đạt" ở ', h('b', null, caught + '/4'), ' câu.'),
        h('ol', null, SAMPLE_FLAWS.map(f => h('li', null, f))),
        h('p', null, 'Kết luận hợp lý cho phiếu này: ', verdictTag('unsure'), st.rv === 'unsure' ? ' Bạn chọn cùng hướng.' : ' Bạn đã chọn: ' + D.VERDICTS[st.rv] + '.')) : null,
      h('p', null, 'Văn bản phản biện để gửi lại cho nhóm bạn:'), exportBox(text, 'phan-bien.txt', 8));
  };
  const commonErrors = () => {
    const wrong = idsOfS1().map(id => ({ e: BY_ID[id], a: S.s1[id] })).filter(r => r.a && r.a.done && !r.a.ok);
    return h('section', { class: 'card stack' },
      h('h2', null, 'D. Lỗi phổ biến để nhìn lại'),
      h('p', null, 'Ở lớp, giáo viên tổng kết lỗi phổ biến từ số liệu Chặng 1. Cùng lúc, đây là các thư bạn đã làm sai trong Chặng 1 trên thiết bị này:'),
      wrong.length ? h('ul', null, wrong.map(r => h('li', null, h('b', null, 'Thư ' + r.e.id + ': '), r.e.subject, '. Đáp án: ' + D.VERDICTS[r.e.verdict] + '. ', r.e.explain.split('. ')[0] + '.'))) : h('p', { class: 'muted' }, S.s1 && Object.keys(S.s1).length ? 'Bạn không có thư nào sai ở Chặng 1, hoặc chưa làm xong chặng này.' : 'Bạn chưa làm Chặng 1 trên thiết bị này.'));
  };
  const drawBody = () => {
    const d = st.sheet;
    mount(body, sourceBox(), d ? sheetNode(d) : null, d ? reviewBox(d) : null, d && st.submitted ? resultBox(d) : null, commonErrors());
  };
  drawBody();
  mount(root, stageHead('chang5', 'Hai nhóm đổi phiếu và phản biện bằng bằng chứng. Nếu học một mình, hãy dùng phiếu mẫu có sai sót.'), body, h('div', { class: 'row' }, finishBtn('chang5')));
  return root;
}

/* ===== Chặng 6: đánh giá cá nhân, phản ánh, kết quả ===== */
function s6Score() {
  const T = S.s6.test;
  const nOk = D.POST.filter(e => T.a[e.id] === e.verdict).length;
  const c1 = T.done ? Math.round(((3 * nOk) / 4) * 2) / 2 : 0;
  const ex = S.s6.ex || {};
  const em = ex.id ? BY_ID[ex.id] : null;
  let c2 = 0;
  if (em && ex.layers) D.LAYERS.forEach(l => { const x = ex.layers[l.id]; if (x && x.s === em.layers[l.id].s && (x.t || '').trim().length >= 10) c2++; });
  const acts = (S.s6.acts && S.s6.acts[ex.id]) || [];
  const good = acts.filter(id => (D.ACTIONS.find(a => a.id === id) || {}).good).length;
  const bad = acts.length - good;
  const c3 = bad > 0 ? 0 : Math.min(2, good);
  const cardFilled = D.SOURCE_FIELDS.filter(f => ((S.s4.card || {})[f.id] || '').trim().length >= 3).length;
  const reflN = (S.s6.refl || []).filter(t => (t || '').trim().length >= 20).length;
  return { nOk, c1, c2, c3, bad, good, cardFilled, reflN, em };
}
function chang6() {
  const st = S.s6;
  st.test = st.test || { a: {}, done: false };
  st.ex = st.ex || {};
  st.acts = st.acts || {};
  st.refl = st.refl || [];
  const u = rec(ui, 's6', { step: 0 });
  const root = h('div', { class: 'stack lg' });
  const labels = ['Phân loại 4 thư mới', 'Giải thích bằng ba lớp', 'Hành động an toàn', 'Phản ánh', 'Kết quả'];
  const body = h('div', { class: 'stack lg' });
  const tabs = h('div', { class: 'tabs', role: 'tablist' });
  const go6 = i => { u.step = i; draw(); window.scrollTo(0, 0); };
  const nav = (i, label) => h('div', { class: 'row gap' },
    i > 0 ? h('button', { class: 'btn sec', type: 'button', onclick: () => go6(i - 1) }, 'Quay lại') : null,
    i < 4 ? h('button', { class: 'btn big', type: 'button', onclick: () => go6(i + 1) }, label || 'Tiếp: ' + labels[i + 1]) : null);
  const pickDefault = () => {
    if (st.ex.id) return;
    const first = D.POST.find(e => st.test.a[e.id] !== e.verdict) || D.POST.find(e => e.verdict !== 'real') || D.POST[1];
    st.ex = { id: first.id, layers: { sender: { s: '', t: '' }, link: { s: '', t: '' }, content: { s: '', t: '' } } };
    save();
  };
  const step0 = () => h('div', { class: 'stack lg' },
    h('p', null, 'Bốn thư mới, chưa từng xuất hiện ở Chặng 1. Chọn kết luận cho từng thư rồi nộp bài. Bước này không có gợi ý.'),
    testRunner(D.POST, st.test, { feedback: true, onDone: () => { save(); } }),
    nav(0));
  const step1 = () => {
    pickDefault();
    const ex = st.ex;
    const e = BY_ID[ex.id];
    const taMap = {};
    const mail = mailView(e, {
      expand: true, evidence: true, showPh: false,
      onEv: (layer, text) => { const ta = taMap[layer]; if (!ta) return; ta.value += (ta.value ? '\n' : '') + '“' + text + '”'; ex.layers[layer].t = ta.value; save(); },
    });
    const form = h('div', { class: 'stack' });
    const drawForm = () => {
      mount(form, D.LAYERS.map(l => {
        const x = ex.layers[l.id];
        const ta = textarea('s6-l-' + l.id, x.t, v => { x.t = v; }, 3, 'Bấm vào chỗ trong thư để trích dẫn, rồi viết một câu giải thích.');
        taMap[l.id] = ta;
        return h('div', { class: 'lcard l-' + l.id },
          h('div', { class: 'lhead' }, h('span', { class: 'lnum' }, l.n), h('b', null, l.name)),
          h('div', { class: 'lbody stack' }, h('p', { class: 'lq' }, l.q), statePicker(x.s, s => { x.s = s; save(); drawForm(); }), field('Bằng chứng và giải thích', ta)));
      }));
    };
    drawForm();
    return h('div', { class: 'stack lg' },
      h('p', null, 'Chọn một thư trong bốn thư vừa làm và giải thích kết luận bằng ba lớp. Nên chọn thư lừa đảo hoặc chưa chắc để có nhiều bằng chứng để nói.'),
      h('div', { class: 'chips' }, D.POST.map(p => h('button', {
        class: 'chip' + (ex.id === p.id ? ' on' : ''), type: 'button', 'aria-pressed': String(ex.id === p.id),
        onclick: () => { if (ex.id !== p.id) { st.ex = { id: p.id, layers: { sender: { s: '', t: '' }, link: { s: '', t: '' }, content: { s: '', t: '' } } }; save(); draw(); } },
      }, p.id + ': ' + p.subject))),
      h('div', { class: 'two' }, mail, form),
      nav(1));
  };
  const step2 = () => {
    pickDefault();
    const e = BY_ID[st.ex.id];
    const sel = rec(st.acts, e.id, []);
    return h('div', { class: 'stack lg' },
      h('p', null, 'Với thư ', h('b', null, e.id + ': ' + e.subject), ', bạn sẽ làm gì? Chọn các hành động bạn thực sự sẽ làm.'),
      h('div', { class: 'chips col' }, D.ACTIONS.map(a => h('button', {
        class: 'chip' + (sel.includes(a.id) ? ' on' : ''), type: 'button', 'aria-pressed': String(sel.includes(a.id)),
        onclick: () => { const i = sel.indexOf(a.id); if (i >= 0) sel.splice(i, 1); else sel.push(a.id); save(); draw(); },
      }, a.text))),
      (() => {
        const r = s6Score();
        if (!sel.length) return null;
        return h('div', { class: 'card stack ' + (r.bad ? 'bad' : 'ok') },
          r.bad ? h('p', { class: 'note-warn' }, 'Có hành động nguy hiểm trong lựa chọn của bạn. Trả lời thư hoặc gửi mã OTP đều đưa thông tin cho chính người có thể là kẻ lừa đảo.') : h('p', { class: 'note-ok' }, 'Không có hành động nguy hiểm nào.'),
          h('p', null, h('b', null, 'Gợi ý cho thư này: '), e.action));
      })(),
      nav(2));
  };
  const step3 = () => h('div', { class: 'stack lg' },
    h('p', null, 'Bốn câu hỏi theo chu trình Kolb. Trả lời cụ thể, dẫn một thư cụ thể (ví dụ "thư 6" hoặc "thư A2").'),
    D.REFLECTION.map((q, i) => field((i + 1) + '. ' + q, textarea('s6-r' + i, st.refl[i], v => { st.refl[i] = v; }, 3))),
    nav(3));
  const step4 = () => {
    const r = s6Score();
    const pre = S.pre;
    const nPre = pre && pre.done ? D.PRE.filter(e => pre.a[e.id] === e.verdict).length : null;
    const hake = nPre != null && st.test.done ? (nPre >= 4 ? null : Math.round(((r.nOk - nPre) / (4 - nPre)) * 100) / 100) : null;
    const row = (crit, max, auto, who, status) => h('tr', null, h('td', null, crit), h('td', null, String(max)), h('td', null, auto), h('td', null, who), h('td', null, status));
    const total = r.c1 + r.c2 + r.c3;
    const lines = [
      'PHIẾU KẾT QUẢ: ' + D.BRAND.name,
      'Họ tên hoặc mã sinh viên: ' + (S.name || '(chưa nhập)'),
      'Ngày: ' + new Date().toLocaleDateString('vi-VN'),
      '1. Phân loại 4 thư mới: ' + r.nOk + '/4 thư đúng, ' + r.c1 + '/3 điểm (tự chấm)',
      '2. Giải thích bằng ba lớp (thư ' + (r.em ? r.em.id : '?') + '): ' + r.c2 + '/3 lớp đạt phần chọn (sơ bộ, giáo viên đọc lập luận)',
      '3. Hành động an toàn: ' + r.c3 + '/2 (sơ bộ)',
      '4. Thẻ nguồn: ' + r.cardFilled + '/6 mục đã điền (chờ giáo viên hoặc bạn học chấm)',
      '5. Phản ánh: ' + r.reflN + '/4 câu đã trả lời (chờ giáo viên chấm)',
      'Điểm tự động sơ bộ: ' + total + '/8',
    ];
    if (nPre != null) lines.push('Tiền kiểm: ' + nPre + '/4. Hậu kiểm: ' + r.nOk + '/4.' + (hake != null ? ' Hake gain: ' + hake : ''));
    return h('div', { class: 'stack lg' },
      h('section', { class: 'card stack cert' },
        h('p', { class: 'eyebrow' }, D.BRAND.name + ' · Phiếu kết quả'),
        field('Họ tên hoặc mã sinh viên (chỉ lưu trên thiết bị này)', h('input', { class: 'in', id: 's6-name', type: 'text', value: S.name || '', oninput: ev => { S.name = ev.target.value; save(); } })),
        h('div', { class: 'tblwrap' }, h('table', { class: 'tbl' },
          h('thead', null, h('tr', null, h('th', null, 'Tiêu chí'), h('th', null, 'Tối đa'), h('th', null, 'Học liệu tính được'), h('th', null, 'Ai chấm chính thức'), h('th', null, 'Trạng thái'))),
          h('tbody', null,
            row('1. Phân loại 4 thư mới', 3, st.test.done ? r.c1 + ' (' + r.nOk + '/4 thư đúng)' : 'Chưa nộp bài', 'Tự động', st.test.done ? (r.nOk >= 3 ? 'Đạt mức tốt' : 'Chưa đạt mức tốt') : 'Quay lại bước 1'),
            row('2. Giải thích bằng ba lớp', 3, r.c2 + '/3 lớp đạt (sơ bộ)', 'Giáo viên đọc lập luận', 'Chờ giáo viên'),
            row('3. Hành động an toàn', 2, r.c3 + '/2 (sơ bộ)', 'Giáo viên', r.bad ? 'Có hành động nguy hiểm' : 'Chờ giáo viên'),
            row('4. Thẻ nguồn', 1, r.cardFilled + '/6 mục đã điền', 'Giáo viên hoặc bạn học', r.cardFilled === 6 ? 'Đủ để chấm' : 'Chưa đủ 6 mục'),
            row('5. Phản ánh', 1, r.reflN + '/4 câu đã trả lời', 'Giáo viên', r.reflN >= 3 ? 'Đủ để chấm' : 'Cần ít nhất 3 câu cụ thể')))),
        h('p', null, h('b', null, 'Điểm tự động sơ bộ: ' + total + '/8.'), ' Hai điểm còn lại và điểm chính thức do giáo viên hoặc bạn học chấm. Ngưỡng đạt 7/10 là giả định của người thiết kế, sẽ chỉnh sau lần dạy thử đầu tiên.'),
        nPre != null && st.test.done ? h('p', null, 'Tiền kiểm ' + nPre + '/4, hậu kiểm ' + r.nOk + '/4' + (hake != null ? ', Hake gain ' + hake : ', không tính được Hake gain vì tiền kiểm đã tối đa') + '. Đây chỉ là số đo của riêng bạn trên 4 thư, không đại diện cho cả lớp.') : null,
        h('div', { class: 'row gap noprint' },
          h('button', { class: 'btn sec', type: 'button', onclick: () => copyText(lines.join('\n'), 'Đã sao chép phiếu kết quả') }, 'Sao chép phiếu kết quả'),
          !IN_FRAME ? h('button', { class: 'btn sec', type: 'button', onclick: () => window.print() }, 'In hoặc lưu PDF') : null)),
      h('section', { class: 'card stack' },
        h('h3', null, 'Bước tiếp theo'),
        h('p', null, 'Phần ngoài lớp (20 phút) giúp bạn dùng ba lớp với thư thật trong hộp thư của mình, chỉ ghi số thư, kết luận và dấu hiệu.')),
      h('div', { class: 'row gap' }, h('button', { class: 'btn sec', type: 'button', onclick: () => go6(3) }, 'Quay lại'), finishBtn('chang6')));
  };
  const draw = () => {
    mount(tabs, labels.map((l, i) => h('button', {
      class: 'tab' + (u.step === i ? ' cur' : ''), type: 'button', role: 'tab', 'aria-selected': String(u.step === i), onclick: () => go6(i),
    }, (i + 1) + '. ' + l)));
    mount(body, [step0, step1, step2, step3, step4][u.step]());
  };
  draw();
  mount(root, stageHead('chang6', 'Bốn thư mới, một thư giải thích bằng ba lớp, hành động an toàn và bốn câu hỏi phản ánh.'), tabs, body);
  return root;
}

/* ===== Ngoài lớp, Kho thư, Góc giảng viên, Về học liệu ===== */
const OFF_ACTIONS = ['Không bấm, tự mở trang chính thức', 'Hỏi qua kênh khác đã biết', 'Báo thư cho nơi có trách nhiệm', 'Xóa thư', 'Đọc và làm theo thư vì thư an toàn', 'Chưa làm gì, đang chờ kiểm chứng'];
function ngoailop() {
  const rows = S.off;
  while (rows.length < 5) rows.push({ n: '', v: '', signs: [], act: '' });
  const root = h('div', { class: 'stack lg' });
  const tbl = h('div', { class: 'stack' });
  const expo = h('div');
  const drawExport = () => {
    const tsv = ['Thư số\tKết luận\tDấu hiệu chính\tHành động'].concat(rows.map(r => [r.n, r.v ? D.VERDICTS[r.v] : '', (r.signs || []).join(', '), r.act].join('\t'))).join('\n');
    mount(expo, exportBox(tsv, 'bang-tu-theo-doi.tsv', 7));
  };
  const drawRows = () => mount(tbl, rows.map((r, i) => h('div', { class: 'card stack off' },
    h('b', null, 'Thư ' + (i + 1)),
    h('div', { class: 'grid2' },
      field('Ký hiệu thư (chỉ số thứ tự hoặc ngày nhận, không chép nội dung)', h('input', { class: 'in', id: 'off-n' + i, type: 'text', value: r.n || '', maxlength: '30', oninput: ev => { r.n = ev.target.value; save(); drawExport(); } })),
      field('Hành động', h('select', { class: 'in', id: 'off-a' + i, value: r.act || '', onchange: ev => { r.act = ev.target.value; save(); drawExport(); } }, h('option', { value: '' }, 'Chọn hành động'), OFF_ACTIONS.map(a => h('option', { value: a }, a))))),
    h('div', null, h('span', { class: 'flabel' }, 'Kết luận'), verdictButtons(r.v, false, v => { r.v = v; save(); drawRows(); drawExport(); })),
    h('div', null, h('span', { class: 'flabel' }, 'Dấu hiệu chính'), h('div', { class: 'chips' }, D.SIGNS.map(s => h('button', {
      class: 'chip small' + ((r.signs || []).includes(s.id) ? ' on' : ''), type: 'button', 'aria-pressed': String((r.signs || []).includes(s.id)),
      onclick: () => { r.signs = r.signs || []; const k = r.signs.indexOf(s.id); if (k >= 0) r.signs.splice(k, 1); else r.signs.push(s.id); save(); drawRows(); drawExport(); },
    }, s.id + ' ' + s.label)))))));
  drawRows();
  drawExport();
  mount(root,
    stageHead('ngoailop', 'Áp dụng ba lớp cho năm thư trong hộp thư của chính bạn. Chỉ ghi số thư, kết luận và dấu hiệu.'),
    h('div', { class: 'card note-warn-box stack' },
      h('b', null, 'Quyền riêng tư'),
      h('p', null, 'Không chép nội dung thư, địa chỉ thư, tên người hay thông tin tài khoản vào bảng này. Bảng chỉ lưu trên thiết bị của bạn, và bạn tự quyết định có nộp hay không.')),
    tbl,
    h('section', { class: 'card stack' }, h('h3', null, 'Xuất bảng tự theo dõi'), h('p', { class: 'muted small' }, 'Sao chép rồi dán vào Google Sheets hoặc Excel (các cột tách bằng dấu tab).'), expo),
    h('section', { class: 'card stack' },
      h('h3', null, 'Đối chiếu thẻ nguồn với một bạn học'),
      h('p', null, 'Một bạn khác kiểm tra thẻ nguồn của nhóm bạn ở Chặng 4: đủ sáu mục chưa, mức tin cậy có lý do chưa. Ghi lại một điều bạn học sửa.')),
    h('div', { class: 'row' }, finishBtn('ngoailop')));
  return root;
}

/* ---------- Kho thư ---------- */
function khothu() {
  const u = rec(ui, 'lib', { f: 'all', id: null });
  const root = h('div', { class: 'stack lg' });
  const draw = () => {
    if (u.id) {
      const e = BY_ID[u.id];
      mount(root,
        pageHead('Kho thư', 'Thư ' + e.id, 'Chế độ ôn: hiện sẵn đáp án, ba lớp và giải thích.'),
        h('button', { class: 'btn sec', type: 'button', onclick: () => { u.id = null; draw(); } }, 'Về danh sách'),
        h('div', { class: 'two' },
          mailView(e, { expand: true, showPh: true }),
          h('div', { class: 'stack' },
            h('div', { class: 'card stack' }, h('p', null, 'Kết luận: ', verdictTag(e.verdict)),
              h('p', null, h('b', null, 'Dấu hiệu: '), e.signs.map(s => SIGN_BY[s].label).join('; '), '.'),
              h('p', null, h('b', null, 'Vì sao: '), e.explain), h('p', null, h('b', null, 'Nên làm gì: '), e.action)),
            layerCards(e))));
      return;
    }
    const list = E_MAIN.concat([E_T]).filter(e => u.f === 'all' || e.verdict === u.f);
    mount(root,
      pageHead('Kho thư', 'Ôn lại 12 thư và thư tình huống', 'Mọi thư đều có đáp án, ba lớp và giải thích. Dùng để ôn trước bài kiểm tra.'),
      h('div', { class: 'chips' }, [['all', 'Tất cả'], ['scam', 'Lừa đảo'], ['real', 'Thật'], ['unsure', 'Chưa chắc']].map(f => h('button', {
        class: 'chip' + (u.f === f[0] ? ' on' : ''), type: 'button', 'aria-pressed': String(u.f === f[0]), onclick: () => { u.f = f[0]; draw(); },
      }, f[1]))),
      h('div', { class: 'libgrid' }, list.map(e => h('button', { class: 'libcard', type: 'button', onclick: () => { u.id = e.id; draw(); window.scrollTo(0, 0); } },
        h('span', { class: 'libn' }, e.id === 'T' ? 'T' : e.id), h('span', { class: 'libt' }, h('b', null, e.subject), h('small', null, e.from.addr)), verdictTag(e.verdict)))));
  };
  draw();
  return root;
}

/* ---------- Góc giảng viên ---------- */
let timerHandle = null;
function stopTimer() { if (timerHandle) { clearInterval(timerHandle); timerHandle = null; } }
function giangvien() {
  const root = h('div', { class: 'stack lg' });
  const t = rec(ui, 'timer', { idx: 0, left: D.LESSON[0].min * 60, run: false });
  const timerBox = h('div', { class: 'card stack' });
  const fmt = s => String(Math.floor(s / 60)).padStart(2, '0') + ':' + String(s % 60).padStart(2, '0');
  const drawTimer = () => {
    const a = D.LESSON[t.idx];
    mount(timerBox,
      h('h2', null, 'Đồng hồ buổi học'),
      h('div', { class: 'chips' }, D.LESSON.map((l, i) => h('button', {
        class: 'chip' + (t.idx === i ? ' on' : ''), type: 'button', 'aria-pressed': String(t.idx === i),
        onclick: () => { t.idx = i; t.left = l.min * 60; t.run = false; stopTimer(); drawTimer(); },
      }, (i < 6 ? 'HĐ' + l.n : 'Ngoài lớp') + ' · ' + l.min + '′'))),
      h('p', null, h('b', null, a.n + '. ' + a.name), ' · ' + a.theory + ' · ' + a.tool),
      h('div', { class: 'clock', role: 'timer', 'aria-live': 'off' }, fmt(t.left)),
      h('div', { class: 'row gap' },
        h('button', { class: 'btn', type: 'button', onclick: () => { t.run = !t.run; if (t.run) startTimer(); else stopTimer(); drawTimer(); } }, t.run ? 'Tạm dừng' : 'Bắt đầu'),
        h('button', { class: 'btn sec', type: 'button', onclick: () => { t.left = a.min * 60; t.run = false; stopTimer(); drawTimer(); } }, 'Đặt lại')));
  };
  const startTimer = () => {
    stopTimer();
    timerHandle = setInterval(() => {
      if (!t.run) return;
      t.left = Math.max(0, t.left - 1);
      const c = $('.clock', timerBox);
      if (c) c.textContent = fmt(t.left);
      if (t.left === 0) { t.run = false; stopTimer(); toast('Hết thời gian hoạt động ' + D.LESSON[t.idx].n); drawTimer(); }
    }, 1000);
  };
  viewCleanup = stopTimer;
  drawTimer();
  /* bộ đếm giơ tay */
  const tallyBox = h('div', { class: 'card stack' });
  const tu = rec(ui, 'tallyId', { id: E_MAIN[0].id });
  const tally = id => rec(S.tally, id, { scam: 0, real: 0, unsure: 0 });
  const drawTally = () => {
    const e = BY_ID[tu.id];
    const c = tally(e.id);
    const n = c.scam + c.real + c.unsure;
    mount(tallyBox,
      h('h2', null, 'Bộ đếm giơ tay cho Chặng 1'),
      h('p', { class: 'muted' }, 'Chiếu thư lên màn hình, cho lớp giơ tay chọn rồi bấm + theo số tay. Bộ đếm lưu trên thiết bị này.'),
      h('div', { class: 'chips' }, E_MAIN.map(x => h('button', { class: 'chip small' + (tu.id === x.id ? ' on' : ''), type: 'button', onclick: () => { tu.id = x.id; drawTally(); } }, 'Thư ' + x.id))),
      h('div', { class: 'tallyrow' }, ['scam', 'real', 'unsure'].map(v => h('div', { class: 'tally v-' + v },
        h('b', null, D.VERDICTS[v]), h('span', { class: 'tn' }, String(c[v])),
        h('div', { class: 'tbar' }, h('div', { style: 'width:' + pct(c[v], n) + '%' })), h('small', null, pct(c[v], n) + '%'),
        h('div', { class: 'row gap' },
          h('button', { class: 'btn sec', type: 'button', 'aria-label': 'Thêm một phiếu ' + D.VERDICTS[v], onclick: () => { c[v]++; save(); drawTally(); } }, '+1'),
          h('button', { class: 'btn sec', type: 'button', 'aria-label': 'Bớt một phiếu ' + D.VERDICTS[v], onclick: () => { c[v] = Math.max(0, c[v] - 1); save(); drawTally(); } }, '−1'))))),
      h('p', null, 'Đáp án thư ' + e.id + ': ', verdictTag(e.verdict), n ? ' Tỷ lệ đúng: ' + pct(c[e.verdict], n) + '%.' : ''),
      h('details', null, h('summary', null, 'Xuất tất cả 12 thư (dán vào sheet DemTay của file Excel)'),
        exportBox(['Thư\tLừa đảo\tThật\tChưa chắc'].concat(E_MAIN.map(x => { const k = tally(x.id); return [x.id, k.scam, k.real, k.unsure].join('\t'); })).join('\n'), 'dem-tay.tsv', 7)),
      h('div', null, h('button', { class: 'btn ghost', type: 'button', onclick: () => { S.tally = {}; save(); drawTally(); } }, 'Xóa bộ đếm')));
  };
  drawTally();
  const keyRows = D.EMAILS.concat(D.PRE, D.POST).map(e => h('tr', null,
    h('td', null, e.id), h('td', { class: 'mono sm' }, e.from.addr), h('td', null, verdictTag(e.verdict)),
    h('td', null, D.LAYERS.map(l => SICON[e.layers[l.id].s]).join(' ')), h('td', null, e.signs.join(', '))));
  mount(root,
    pageHead('Góc giảng viên', 'Điều khiển buổi học', 'Đồng hồ từng hoạt động, bộ đếm giơ tay, bảng đáp án, tiến trình và rubric.'),
    h('div', { class: 'card note-warn-box' }, h('p', null, 'Trang này có đáp án của mọi bộ thư, kể cả bộ kiểm tra đầu vào và cuối bài. Nếu cần giữ kín bộ thư kiểm tra, hãy dùng bản in trong gói và không chia sẻ tệp này cho sinh viên trước giờ học.')),
    timerBox, tallyBox,
    h('section', { class: 'card stack' }, h('h2', null, 'Tiến trình 90 phút và đối chiếu SAMR, TPACK'),
      h('div', { class: 'tblwrap' }, h('table', { class: 'tbl' },
        h('thead', null, h('tr', null, ['Hoạt động', 'Phút', 'Học thuyết', 'Công cụ', 'SAMR', 'TPACK', 'Công việc'].map(x => h('th', null, x)))),
        h('tbody', null, D.LESSON.map(l => h('tr', null, h('td', null, l.n + '. ' + l.name), h('td', null, String(l.min)), h('td', null, l.theory), h('td', null, l.tool), h('td', null, l.samr), h('td', null, l.tpack), h('td', null, l.work))))))),
    h('section', { class: 'card stack' }, h('h2', null, 'Rubric 10 điểm'),
      h('div', { class: 'tblwrap' }, h('table', { class: 'tbl' },
        h('thead', null, h('tr', null, ['Tiêu chí', 'Điểm', 'Người chấm', 'Mức tốt'].map(x => h('th', null, x)))),
        h('tbody', null, D.RUBRIC.map(r => h('tr', null, h('td', null, r.crit), h('td', null, String(r.pts)), h('td', null, r.who), h('td', null, r.good)))))),
      h('p', { class: 'muted small' }, 'Quy ước tiêu chí 1 do nhóm thiết kế đề xuất: điểm = 3 × số thư đúng / 4, làm tròn 0,5; mức tốt khi đúng từ 3/4 thư. Ngưỡng đạt 7/10 là giả định, chỉnh sau lần dạy thử đầu tiên.')),
    h('section', { class: 'card stack' }, h('h2', null, 'Bảng đáp án'),
      h('div', { class: 'tblwrap' }, h('table', { class: 'tbl' },
        h('thead', null, h('tr', null, ['Thư', 'Địa chỉ gửi', 'Kết luận', 'Ba lớp', 'Dấu hiệu'].map(x => h('th', null, x)))),
        h('tbody', null, keyRows))),
      h('p', { class: 'muted small' }, 'Ba lớp theo thứ tự người gửi, liên kết, nội dung: ✓ đáng tin, ✕ có vấn đề, ? chưa kiểm chứng được, – không có.')),
    h('section', { class: 'card stack' }, h('h2', null, 'Các tệp trong gói'),
      h('ul', null,
        h('li', null, h('b', null, 'ThamTuHopThu_HocLieuSo.html'), ': học liệu này, chạy offline.'),
        h('li', null, h('b', null, 'ThamTuHopThu_BoTheBai.pdf'), ' và ', h('b', null, 'ThamTuHopThu_PhieuInSan.pdf'), ': phương án giấy.'),
        h('li', null, h('b', null, 'ThamTuHopThu_Infographic.pdf / .png'), ': tóm tắt báo cáo một trang.'),
        h('li', null, h('b', null, 'ThamTuHopThu_TaiLieuGiangVien.docx'), ': kịch bản, đáp án, rubric.'),
        h('li', null, h('b', null, 'ThamTuHopThu_PhanTichSoLieu.xlsx'), ': nhập số liệu thật từ lần dạy thử và phân tích tự động.'))));
  return root;
}

/* ---------- Về học liệu ---------- */
function gioithieu() {
  const root = h('div', { class: 'stack lg' });
  const reset = h('div');
  const drawReset = armed => mount(reset, armed
    ? h('div', { class: 'row gap' }, h('span', null, 'Xóa toàn bộ tiến độ và dữ liệu đã nhập trên thiết bị này?'),
      h('button', { class: 'btn danger', type: 'button', onclick: () => { resetAll(); go('home'); toast('Đã xóa dữ liệu trên thiết bị này'); } }, 'Xóa hết'),
      h('button', { class: 'btn sec', type: 'button', onclick: () => drawReset(false) }, 'Giữ lại'))
    : h('button', { class: 'btn sec', type: 'button', onclick: () => drawReset(true) }, 'Xóa tiến độ trên thiết bị này'));
  drawReset(false);
  const meta = [['Đối tượng', D.META.audience], ['Thời lượng', D.META.duration], ['Hình thức', D.META.kind], ['Công nghệ', D.META.tech], ['Quyền riêng tư', D.META.privacy], ['Chuẩn năng lực', D.META.standards], ['Giấy phép', D.BRAND.license], ['Phiên bản', 'v' + D.BRAND.version + ', ' + D.BRAND.date]];
  const refs = (D.REFS || []).map(r => h('li', { html: r.replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/\*([^*]+)\*/g, '<em>$1</em>') }));
  mount(root,
    pageHead('Về học liệu', 'Thám Tử Hộp Thư', D.BRAND.tagline),
    h('section', { class: 'card stack' }, h('h2', null, 'Thông tin học liệu'),
      h('dl', { class: 'meta' }, meta.map(m => [h('dt', null, m[0]), h('dd', null, m[1])])),
      D.TEAMINFO && D.TEAMINFO.name ? h('p', null, h('b', null, 'Nhóm thực hiện: '), D.TEAMINFO.name + (D.TEAMINFO.members ? ' (' + D.TEAMINFO.members + ')' : '')) : null),
    h('section', { class: 'card stack' }, h('h2', null, 'Mục tiêu học tập'), h('ol', null, D.OBJECTIVES.map(o => h('li', null, o)))),
    h('section', { class: 'card stack' }, h('h2', null, 'Cơ sở lý luận của từng chặng'),
      h('div', { class: 'tblwrap' }, h('table', { class: 'tbl' }, h('thead', null, h('tr', null, h('th', null, 'Chặng'), h('th', null, 'Học thuyết'), h('th', null, 'Vì sao'))),
        h('tbody', null, D.THEORY_NOTES.map(t => h('tr', null, h('td', null, t.mode), h('td', null, t.theory), h('td', null, t.why)))))),
      h('h3', null, 'Chu trình Kolb trong học liệu'),
      h('ol', null, D.KOLB.map(k => h('li', null, h('b', null, k.stage), ': ' + k.where)))),
    h('section', { class: 'card stack' }, h('h2', null, 'Tự đánh giá học liệu số'),
      h('p', { class: 'muted' }, 'Bảng dưới là cách nhóm thiết kế đối chiếu học liệu với các tiêu chí chung của học liệu số. Nhóm cần đối chiếu thêm với tiêu chí thầy cô đã giảng trên lớp.'),
      h('div', { class: 'tblwrap' }, h('table', { class: 'tbl' }, h('thead', null, h('tr', null, h('th', null, 'Tiêu chí'), h('th', null, 'Học liệu đáp ứng thế nào'))),
        h('tbody', null, D.QUALITY_CHECK.map(q => h('tr', null, h('td', null, q.crit), h('td', null, q.how))))))),
    h('section', { class: 'card stack' }, h('h2', null, 'Giới hạn cần biết'),
      h('ul', null,
        h('li', null, 'Mười hai thư mô phỏng không đại diện hết thủ đoạn thật. Kẻ lừa đảo thay đổi thủ đoạn.'),
        h('li', null, 'Ba lớp kiểm tra giảm rủi ro nhưng không loại bỏ nó. Với thư chưa chắc, hành động đúng là kiểm chứng qua kênh chính thức.'),
        h('li', null, 'Học liệu chưa được dạy thử. Mọi kết quả về hiệu quả cần được thu thập thật ở lần dạy thử.'),
        h('li', null, 'Đáp án nằm trong tệp này. Với bài kiểm tra có điểm, dùng bản in hoặc bộ thư do giáo viên soạn thêm.'))),
    refs.length ? h('section', { class: 'card stack' }, h('h2', null, 'Tài liệu tham khảo chính'), h('ol', { class: 'refs' }, refs), h('p', { class: 'muted small' }, 'Danh mục đầy đủ có trong báo cáo kèm theo.')) : null,
    h('section', { class: 'card stack' }, h('h2', null, 'Dữ liệu trên thiết bị'), h('p', { class: 'muted' }, 'Tiến độ lưu trong bộ nhớ của trình duyệt, không gửi đi đâu.'), reset));
  return root;
}

/* ===== Khởi động ===== */
const VIEWS = { home, chang0, chang1, chang2, chang3, chang4, chang5, chang6, ngoailop, khothu, giangvien, gioithieu };
(function boot() {
  let v = 'home';
  try { const hsh = location.hash.slice(1); if (VIEWS[hsh]) v = hsh; } catch (e) { /* bỏ qua */ }
  view = v;
  window.addEventListener('hashchange', () => {
    let hsh = '';
    try { hsh = location.hash.slice(1); } catch (e) { /* bỏ qua */ }
    if (VIEWS[hsh] && hsh !== view) { if (viewCleanup) { viewCleanup(); viewCleanup = null; } view = hsh; render(); window.scrollTo(0, 0); }
  });
  render();
})();

</script>

</body>
</html>
