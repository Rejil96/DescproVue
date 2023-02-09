<template>
  <div class="conatiner" id="contentWrapper">
    <h1 class="main-heading">{{ page.title }}</h1>
    <p>{{ page.content }}</p>
   
  </div>
</template>

<script>
export default {
  props: ["page"],
};
</script>

<style>
#contentWrapper {
  width: 100vw;
  height: calc(100vh - 80px);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  box-sizing: border-box;
}

.main-heading {
  font-size: 48px;
  font-weight: bolder;
  margin-bottom: 60px;
}
</style>
