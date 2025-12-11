<template>
  <div>
    <img
      src="https://yesno.wtf/assets/no/8-5e08abbe5aacd2cf531948145b787e9a.gif"
      alt="No puede ver"
    />
    <div class="pregunta-container">
      <input id="id_input" type="text" placeholder="Hazme una pregunta" />
      <p>Recuerda terminar con el signo de interogación (?)</p>
      <h2>Sere millonario?</h2>
      <h1>Yes, No</h1>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
img {
  height: 100vh;
  width: 100vw;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  left: 0px;
  top: 0px;
}
h1 {
  font-size: 80px;
}
</style>