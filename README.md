
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Brain Quiz</title>
<style>
:root{--bg:#f6f5f1;--card:#fff;--text:#1d1d1f;--muted:#6b6b72;--line:#e4e2da;--accent:#4f46e5;--ok:#15803d;--okbg:#dcfce7;--bad:#b91c1c;--badbg:#fee2e2;color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#15151a;--card:#1f1f27;--text:#f2f2f5;--muted:#a0a0ab;--line:#33333d;--accent:#818cf8;--ok:#4ade80;--okbg:#14351f;--bad:#f87171;--badbg:#3d1a1a;color-scheme:dark}}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--text);font-family:system-ui,-apple-system,"Segoe UI",Roboto,sans-serif;line-height:1.45}
#app{max-width:520px;margin:0 auto;padding:20px 16px 40px}
h1{font-size:28px;margin:8px 0 4px}
p.sub{color:var(--muted);margin:0 0 20px}
.card{background:var(--card);border:1px solid var(--line);border-radius:16px;padding:18px}
button{font:inherit;color:inherit;cursor:pointer}
.lvl{display:block;width:100%;text-align:left;background:var(--card);border:1px solid var(--line);border-radius:14px;padding:16px;margin-bottom:12px}
.lvl b{display:block;font-size:18px}
.lvl span{color:var(--muted);font-size:14px}
.lvl small{float:right;color:var(--muted)}
.top{display:flex;justify-content:space-between;color:var(--muted);font-size:14px;margin-bottom:8px}
.bar{height:8px;background:var(--line);border-radius:99px;overflow:hidden;margin-bottom:16px}
.bar i{display:block;height:100%;background:var(--accent);transition:width .3s}
.tag{display:inline-block;font-size:12px;padding:3px 10px;border-radius:99px;background:var(--line);color:var(--muted);margin-bottom:10px}
.q{font-size:20px;font-weight:600;margin:0 0 16px}
.opt{display:block;width:100%;text-align:left;background:var(--bg);border:2px solid var(--line);border-radius:12px;padding:14px;margin-bottom:10px;font-size:16px}
.opt.ok{border-color:var(--ok);background:var(--okbg)}
.opt.bad{border-color:var(--bad);background:var(--badbg)}
.main{display:block;width:100%;background:var(--accent);color:#fff;border:0;border-radius:12px;padding:14px;font-size:16px;font-weight:600;margin-top:6px}
.ghost{display:block;width:100%;background:transparent;border:1px solid var(--line);border-radius:12px;padding:14px;font-size:16px;margin-top:10px}
.score{font-size:56px;font-weight:700;text-align:center;margin:10px 0 0}
.msg{text-align:center;color:var(--muted);margin:0 0 18px}
</style>
</head>
<body>
<div id="app"></div>
<script>
// Each question: [category, question, correct answer, wrong1, wrong2, wrong3]
var DATA = {
  easy: [
    ["Science","Which planet is known as the Red Planet?","Mars","Venus","Jupiter","Mercury"],
    ["Maths","What is 7 + 8?","15","14","16","13"],
    ["Science","Which gas do plants take in from the air?","Carbon dioxide","Oxygen","Nitrogen","Helium"],
    ["Logic","What comes next? 2, 4, 6, 8, ?","10","9","12","11"],
    ["Geography","What is the capital of France?","Paris","Rome","Madrid","Berlin"],
    ["Science","How many legs does a spider have?","8","6","10","4"],
    ["Maths","What is 10 × 5?","50","15","55","40"],
    ["Logic","Which one is the odd one out?","Carrot","Apple","Banana","Mango"],
    ["Science","At what temperature (°C) does water freeze?","0","10","-10","100"],
    ["Nature","Which is the largest mammal?","Blue whale","Elephant","Giraffe","Hippo"]
  ],
  medium: [