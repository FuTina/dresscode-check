<script setup>
import { ref, onMounted } from "vue";

const dressCodeInput = ref("");
const validDressCodes = [
  "black & gold",
  "black and gold",
  "gold & black",
  "gold and black",
  "wild & gold",
  "wild and gold",
  "gold & wild",
  "gold and wild",
];

const checkDressCode = () => {
  if (validDressCodes.includes(dressCodeInput.value.toLowerCase().trim())) {
    window.location.href = "https://dress-code-wizard.vercel.app/";
  } else {
    alert("❌ Falscher Dress Code! Versuch es nochmal.");
  }
};

// Enter-Taste erlauben
onMounted(() => {
  window.addEventListener("keydown", (e) => {
    if (e.key === "Enter") {
      checkDressCode();
    }
  });
});
</script>

<template>
  <div class="background">
    <div class="glass-card">
      <h1 class="title">🎩 Dress Code Check</h1>
      <p class="subtitle">✨ Gib den richtigen Code ein, um Zugang zu erhalten! ✨</p>

      <input
        v-model="dressCodeInput"
        placeholder="🔑 Dein Dress Code..."
        class="input-field"
      />
      <button @click="checkDressCode" class="btn-check">✅ Überprüfen</button>
    </div>
  </div>
</template>

<style>
/* 🌟 Weißer, cleaner Hintergrund */
.background {
  background: white;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

/* 💎 Glas-Optik */
.glass-card {
  background: rgba(255, 255, 255, 0.9);
  backdrop-filter: blur(12px);
  border-radius: 16px;
  padding: 40px;
  text-align: center;
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12);
  max-width: 420px;
  width: 90%;
  border: 1px solid rgba(0, 0, 0, 0.05);
  animation: fadeIn 0.8s ease-in-out;
}

/* 🎩 Titel in edlem Lila */
.title {
  font-size: 28px;
  color: #5a189a;
  font-weight: bold;
  margin-bottom: 12px;
  text-shadow: 0px 0px 6px rgba(90, 24, 154, 0.3);
}

/* ✨ Untertitel */
.subtitle {
  color: #4b0082;
  font-size: 14px;
  margin-bottom: 20px;
  font-weight: 500;
}

/* 🔑 Eingabefeld mit mehr Abstand */
.input-field {
  width: 100%;
  max-width: 350px;
  padding: 14px;
  border-radius: 10px;
  border: 2px solid #b197fc;
  text-align: center;
  font-size: 18px;
  background: white;
  color: #4b0082;
  outline: none;
  font-weight: bold;
  transition: all 0.3s ease-in-out;
  display: block;
  margin: 0 auto 24px auto; /* Abstand nach unten vergrößert */
}

/* Platzhalter */
.input-field::placeholder {
  color: #6c757d;
  font-size: 16px;
}

/* Hover- und Fokus-Effekt */
.input-field:focus {
  border-color: #5a189a;
  box-shadow: 0 0 12px #b197fc;
}

/* 🔘 Button mit mehr Abstand */
.btn-check {
  width: 100%;
  max-width: 350px;
  padding: 14px;
  background: #b197fc;
  color: white;
  font-size: 18px;
  font-weight: bold;
  border: none;
  border-radius: 10px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
  box-shadow: 0px 5px 15px rgba(177, 151, 252, 0.5);
  display: block;
  margin: 0 auto;
}

.btn-check:hover {
  background: #5a189a;
  color: white;
  transform: scale(1.05);
  box-shadow: 0px 8px 20px rgba(90, 24, 154, 0.8);
}

/* 📱 Responsiveness */
@media (max-width: 600px) {
  .glass-card {
    padding: 30px;
  }

  .title {
    font-size: 26px;
  }

  .subtitle {
    font-size: 13px;
  }

  .input-field,
  .btn-check {
    font-size: 16px;
    max-width: 100%;
  }
}

/* 🎬 Sanfte Einblend-Animation */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(-15px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
