<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no" />
  <title>TraceAR – Traçar com a Câmera</title>
  <link rel="manifest" href="manifest.json">
  <meta name="theme-color" content="#000000">
  <style>
    :root{
      --panel-bg: rgba(15,15,20,.6);
      --panel-border: rgba(255,255,255,.12);
      --text: #fff;
      --accent: #7dd3fc;
      --danger: #fb7185;
      --ok: #34d399;
    }
    *{ box-sizing: border-box }
    html, body{ height: 100%; background:#000; margin:0; }
    body{ font-family: system-ui, sans-serif; color:var(--text); }
    #camera{ position:fixed; inset:0; width:100%; height:100%; object-fit:cover; background:#000; }
    #grid{ position:fixed; inset:0; pointer-events:none; display:none;
      background-image:
        linear-gradient(to right, rgba(255,255,255,.08) 1px, transparent 1px),
        linear-gradient(to bottom, rgba(255,255,255,.08) 1px, transparent 1px);
      background-size: 10vw 10vw;
    }
    #overlay{
      position:fixed; inset:0; margin:auto; max-width:90vmin; max-height:90vmin;
      transform-origin:center center;
      transform: translate3d(var(--tx,0px), var(--ty,0px), 0) scale(var(--scale,1)) rotate(var(--rot,0deg));
      opacity: var(--opacity, .5);
      filter: var(--filter, none);
      touch-action:none;
      display:none;
    }
    #panel{
      position:fixed; left:0; right:0; bottom:0; padding:12px; display:flex; gap:10px; flex-wrap:wrap; align-items:center; justify-content:center;
      background: var(--panel-bg); backdrop-filter: blur(6px); border-top:1px solid var(--panel-border);
    }
    #panel .group{ display:flex; align-items:center; gap:8px; }
    label{ font-size:.85rem; opacity:.9 }
    input[type="range"]{ width: 140px; }
    .btn{
      appearance:none; border:1px solid var(--panel-border); background:rgba(255,255,255,.04); color:var(--text); padding:8px 10px; border-radius:12px; font-size:.9rem; cursor:pointer;
    }
    .btn:active{ transform: translateY(1px) }
    .btn.ok{ border-color: rgba(52,211,153,.4) }
    #toast{ position:fixed; top:12px; left:50%; transform:translateX(-50%); background:var(--panel-bg); padding:8px 12px; border-radius:10px; border:1px solid var(--panel-border); display:none }
  </style>
</head>
<body>
  <video id="camera" autoplay playsinline></video>
  <div id="grid"></div>
  <img id="overlay" alt="Overlay para traço" />

  <div id="panel">
    <div class="group">
      <label class="btn" for="file">Carregar</label>
      <input id="file" type="file" accept="image/*" hidden />
    </div>
    <div class="group">
      <label for="opacity">Opacidade</label>
      <input id="opacity" type="range" min="0" max="1" step="0.02" value="0.5" />
    </div>
    <div class="group">
      <button id="toggleGrid" class="btn">Grade</button>
      <button id="mirror" class="btn">Espelho</button>
      <button id="edge" class="btn">Contornos</button>
      <button id="torch" class="btn">Luz</button>
      <button id="reset" class="btn">Reset</button>
    </div>
  </div>
  <div id="toast"></div>

  <script>
    const $ = s => document.querySelector(s);
    const toast = (m, ms=1200) => {const t=$('#toast');t.textContent=m;t.style.display='block';clearTimeout(t._h);t._h=setTimeout(()=>t.style.display='none',ms)};

    async function startCamera(){
      try{
        const stream = await navigator.mediaDevices.getUserMedia({ video:{ facingMode:{ideal:'environment'} } });
        $('#camera').srcObject = stream;
      }catch(e){ toast('Erro câmera'); }
    }
    startCamera();

    const state={tx:0,ty:0,scale:1,rot:0,mirror:1,filter:'none',opacity:0.5};
    const overlay=$('#overlay');
    function apply(){
      overlay.style.transform=`translate3d(${state.tx}px,${state.ty}px,0) scale(${state.scale}) rotate(${state.rot}deg) ${state.mirror===-1?'scaleX(-1)':''}`;
      overlay.style.filter=state.filter;
      overlay.style.opacity=state.opacity;
    }

    $('#file').addEventListener('change',e=>{const f=e.target.files[0];if(!f)return;overlay.src=URL.createObjectURL(f);overlay.onload=()=>{overlay.style.display='block';apply();toast('Imagem carregada')};});
    $('#opacity').addEventListener('input',e=>{state.opacity=parseFloat(e.target.value);apply();});
    $('#toggleGrid').addEventListener('click',()=>{$('#grid').style.display=$('#grid').style.display==='block'?'none':'block'});
    $('#mirror').addEventListener('click',()=>{state.mirror*=-1;apply();});
    $('#edge').addEventListener('click',()=>{state.filter=state.filter==='none'?'grayscale(1) contrast(2) brightness(1.1)':'none';apply();});
    $('#reset').addEventListener('click',()=>{state.tx=0;state.ty=0;state.scale=1;state.rot=0;state.mirror=1;state.filter='none';state.opacity=0.5;$('#opacity').value=0.5;apply();});

    // Torch (lanterna)
    let torchOn=false;
    $('#torch').addEventListener('click',async()=>{
      try{
        const stream=$('#camera').srcObject;
        if(!stream) return;
        const track=stream.getVideoTracks()[0];
        const caps=track.getCapabilities();
        if(caps.torch){
          torchOn=!torchOn;
          await track.applyConstraints({advanced:[{torch:torchOn}]});
          toast(torchOn?"Lanterna ligada":"Lanterna desligada");
        } else toast("Sem suporte a lanterna");
      }catch(err){toast("Erro lanterna")}
    });

    // PWA service worker
    if('serviceWorker' in navigator){
      navigator.serviceWorker.register('service-worker.js');
    }
  </script>
</body>
</html>
