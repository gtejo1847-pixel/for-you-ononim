<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Untukmu</title>

<style>
body {
  margin: 0;
  font-family: 'Georgia', serif;
  background: linear-gradient(135deg, #f9f6f2, #ffe6f0);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.card {
  background: #fff;
  padding: 32px;
  max-width: 520px;
  border-radius: 20px;
  box-shadow: 0 8px 25px rgba(0,0,0,0.15);
  animation: fadeIn 1.8s ease;
}

h1 {
  text-align: center;
  color: #c94f7c;
  margin-bottom: 24px;
}

.poem {
  text-align: left;
  font-size: 18px;
  line-height: 1.7;
  color: #333;
  white-space: pre-line;
}

#hint {
  margin-top: 18px;
  text-align: center;
  font-size: 14px;
  color: #888;
  cursor: pointer;
  animation: pulse 1.5s infinite;
}

.signature {
  margin-top: 20px;
  text-align: center;
  font-style: italic;
  color: #666;
}

@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.95); }
  to   { opacity: 1; transform: scale(1); }
}

@keyframes pulse {
  0% { opacity: .4 }
  50% { opacity: 1 }
  100% { opacity: .4 }
}

.heart {
  position: fixed;
  top: -10px;
  font-size: 20px;
  color: #e63963;
  animation: fall linear infinite;
}

@keyframes fall {
  to {
    transform: translateY(110vh) rotate(360deg);
    opacity: 0;
  }
}
</style>
</head>

<body>

<div class="card">
  <h1>Untukmu</h1>

  <div class="poem">
Aku sudah sampai di titik
tidak berharap apa-apa dari siapa pun.
Bukan karena kuat,
tapi karena capek jatuh di lubang yang sama.

Aku sudah yakin
tidak ada lagi yang bisa menggeser perhatianku,
lalu kamu datang
dan merusak keyakinan itu dengan cara yang tenang.

Aku tidak minta janji,
tidak juga kepastian.
Kalau pun ini salah,
biarlah salah yang aku pilih dengan sadar.

Kalau kamu mau tinggal sebentar,
ajari aku pelan-pelan
bahwa percaya tidak selalu berakhir
dengan kehilangan.
  </div>

  <div id="hint">Tap di sini untuk memuncukan sesuatu</div>
  <div class="signature">— Djati</div>
</div>

<audio id="music" loop>
  <source src="musik.mp3" type="audio/mpeg">
</audio>

<script>
const music = document.getElementById("music");
const hint = document.getElementById("hint");
let started = false;

hint.addEventListener("click", async () => {
  if (started) return;
  try {
    await music.play();
    started = true;
    hint.style.display = "none";
    startHearts();
  } catch (e) {
    alert("Tap sekali lagi ya");
  }
});

function startHearts() {
  setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = "❤";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (Math.random() * 3 + 3) + "s";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
  }, 600);
}
</script>

</body>
</html>
