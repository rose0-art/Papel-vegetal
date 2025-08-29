<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Meu PWA</title>

  <!-- Manifest -->
  <link rel="manifest" href="manifest.json">

  <!-- Cor da barra de status em mobile -->
  <meta name="theme-color" content="#ffffff">

  <!-- Ícone de fallback -->
  <link rel="icon" href="icon-192.png" type="image/png">
</head>
<body>
  <h1>🚀 Meu PWA está funcionando!</h1>
  <p>Esse app pode ser instalado e usado offline.</p>

  <!-- Registrar o service worker -->
  <script>
    if ("serviceWorker" in navigator) {
      navigator.serviceWorker.register("service-worker.js")
        .then(() => console.log("✅ Service Worker registrado!"))
        .catch(err => console.log("❌ Erro ao registrar:", err));
    }
  </script>
</body>
</html>
{
  "name": "Meu PWA Exemplo",
  "short_name": "MeuPWA",
  "start_url": ".",
  "display": "standalone",
  "background_color": "#ffffff",
  "theme_color": "#ffffff",
  "icons": [
    {
      "src": "icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    },
    {
      "src": "icon-512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ]
}
self.addEventListener("install", (event) => {
  console.log("📥 Service Worker: Instalando...");

  event.waitUntil(
    caches.open("meu-pwa-cache").then((cache) => {
      return cache.addAll([
        "./",          // raiz
        "./index.html",
        "./icon-192.png",
        "./icon-512.png"
      ]);
    })
  );
});

self.addEventListener("fetch", (event) => {
  event.respondWith(
    caches.match(event.request).then((res) => {
      return res || fetch(event.request);
    })
  );
});
