<template>
  <div class="conatiner pt-3" id="contentWrapper">
    <h1 class="main-heading" v-if="activePage !== 0">{{ page.title }}</h1>
    <p v-if="activePage !== 0">{{ page.content }}</p>
    <p class="h1" v-if="activePage === 0" id="formHeading">Create Pages</p>
    <CreatePage v-if="activePage === 0" :pageCreated = "pageCreated" :activePage= "activePage"></CreatePage>
  </div>
</template>

<script>
import CreatePage from './CreatePage.vue'

export default {
  props: ["page", "pages", "activePage"],
  components: {
    CreatePage,
  },

  methods: {
    pageCreated(objectData) {
      console.log(objectData)
      this.pages.push(objectData)
    }
  }

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
}

.main-heading {
  font-size: 48px;
  font-weight: bolder;
  margin-bottom: 60px;
  
}

#formHeading{
  margin-top: -240px !important;
  align-self: flex-start;
  margin-bottom: 20px;
  margin-left: 310px;
}
</style>
