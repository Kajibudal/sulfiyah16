<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Uus Ngisingan Simulator v3</title>
  <style>
    body {
      font-family: "Comic Sans MS", cursive;
      text-align: center;
      padding: 40px;
      background-color: #f5f5f5;
    }
    h1 {
      font-size: 2.3em;
      color: #795548;
    }
    img {
      max-width: 240px;
      margin: 20px auto;
      display: block;
      border-radius: 16px;
      transition: transform 0.3s ease-in-out;
    }
    .shake {
      animation: shake 0.4s;
    }
    @keyframes shake {
      0% { transform: rotate(0deg); }
      25% { transform: rotate(3deg); }
      50% { transform: rotate(-3deg); }
      75% { transform: rotate(2deg); }
      100% { transform: rotate(0deg); }
    }
    button {
      padding: 12px 20px;
      font-size: 1em;
      background: #8bc34a;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      margin: 10px;
    }
    .output {
      font-size: 1.3em;
      margin-top: 30px;
      color: #444;
    }
  </style>
</head>
<body>

  <h1>💩 UUS NGISINGAN SIMULATOR v3 💩</h1>

  <img id="uusFace" src="https://i.imgur.com/kO0RxjH.jpeg" alt="Wajah Uus Asli Lagi Nahan" />

  <button onclick="progresNgising()">Lihat Progres Ngising</button>
  <button onclick="bagikan()">Share Hasil Ngising</button>

  <div class="output" id="output"></div>

  <audio id="kentutSound">
    <source src="https://www.myinstants.com/media/sounds/fart-with-reverb.mp3" type="audio/mpeg">
  </audio>

  <script>
    const statusNgising = [
      "💨 Baru duduk, masih scroll TikTok...",
      "😤 Ngejan pelan-pelan...",
      "💀 Mules banget tapi sinyal ilang...",
      "💦 Keluar suara efek surround...",
      "✅ Alhamdulillah... sukses!",
      "🚿 Sekarang waktunya cebok 2 jam..."
    ];

    let step = 0;

    function progresNgising() {
      const output = document.getElementById("output");
      const fart = document.getElementById("kentutSound");
      const face = document.getElementById("uusFace");

      const teks = statusNgising[step];
      output.innerText = teks;
      step = (step + 1) % statusNgising.length;

      // Mainkan kentut
      fart.currentTime = 0;
      fart.play();

      // Guncangkan wajah
      face.classList.add("shake");
      setTimeout(() => {
        face.classList.remove("shake");
      }, 500);
    }

    function bagikan() {
      const teks = document.getElementById("output").innerText;
      const shareText = `💩 Uus lagi ngising:\n"${teks}"\nCoba juga: Ngisingan Simulator 😆`;

      if (navigator.share) {
        navigator.share({
          title: "Uus Ngisingan",
          text: shareText,
          url: window.location.href
        });
      } else {
        // fallback: copy ke clipboard
        navigator.clipboard.writeText(shareText);
        alert("Hasil ngising sudah disalin! Tempel di WhatsApp/DM sekarang 💩");
      }
    }
  </script>

</body>
</html>
