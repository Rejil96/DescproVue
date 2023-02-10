<template>
<div class="custom-container">
  <Navbar
    :pages="pages"
    :activePage="activePage"
    :navLinkClick="(index) => (activePage = index)"
  ></Navbar>
  <PageViewer :page="pages[activePage]" :pages="pages" :activePage="activePage"></PageViewer>
  </div>
</template>

<script>
import Navbar from "./components/Navbar.vue";
import PageViewer from "./components/PageViewer.vue";

export default {
  components: {
    Navbar,
    PageViewer,
  },

  data() {
    return {
      activePage: 0,
      theme: "light",
      pages: [
        {
          link: { text: "Home", url: "index.html" },
          title: "Home Page",
          content: "This is the home content",
        },
        {
          link: { text: "About", url: "about.html" },
          title: "About Page",
          content: "This is the about content",
        },
        {
          link: { text: "Contact", url: "contact.html" },
          title: "Contact Page",
          content: "This is the contact content",
        },
      ],
    };
  },

  
};
</script>

<style scoped>
  .custom-container{
    width: 100vw;
  }
</style>