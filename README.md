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
