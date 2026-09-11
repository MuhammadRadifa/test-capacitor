<script setup>
import { ref, onMounted } from "vue";
import { SplashScreen } from "@capacitor/splash-screen";
import { Camera } from "@capacitor/camera";

const imageSrc = ref("");

onMounted(() => {
  SplashScreen.hide();
});

async function takePhoto() {
  try {
    const photo = await Camera.getPhoto({
      resultType: "uri",
    });
    imageSrc.value = photo.webPath;
  } catch (e) {
    console.warn("User cancelled", e);
  }
}

function kirim() {
  alert("Berhasil");
}
</script>

<template>
  <div>
    <header class="titlebar">
      <h1>Tes Praktik - Muhammad Radifa</h1>
    </header>
    <main>
      <p>
        <button class="button" @click="kirim">Kirim</button>
      </p>
    </main>
  </div>
</template>

<style scoped>
.titlebar {
  position: relative;
  display: block;
  padding: 15px;
  text-align: center;
  background-color: #73b5f6;
}
.titlebar h1 {
  margin: 0;
  font-family:
    -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial,
    sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
  font-size: 0.9em;
  font-weight: 600;
  color: #fff;
  text-transform: uppercase;
}
h1,
h2,
h3,
h4,
h5 {
  text-transform: uppercase;
}
.button {
  display: inline-block;
  padding: 10px;
  background-color: #73b5f6;
  color: #fff;
  font-size: 0.9em;
  border: 0;
  border-radius: 3px;
  text-decoration: none;
  cursor: pointer;
}
main {
  padding: 15px;
  font-family:
    -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial,
    sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol";
}
main hr {
  height: 1px;
  background-color: #eee;
  border: 0;
}
main h1 {
  font-size: 1.4em;
  text-transform: uppercase;
  letter-spacing: 1px;
}
main h2 {
  font-size: 1.1em;
}
main h3 {
  font-size: 0.9em;
}
main p {
  color: #333;
}
</style>
