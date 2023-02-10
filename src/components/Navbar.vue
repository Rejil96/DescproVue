<template>
  <nav :class="`navbar navbar-expand-lg navbar-${theme} bg-${theme}`" id="custom-class">
    <a class="navbar-brand" href="#" id="logoName">Vue Js</a>
    <ul class="navbar-nav me-auto mb-2 mb-lg-0">
      <li v-for="(page, index) in publishedPages" class="nav-item" :key="index">
        <a
          class="nav-link"
          id="navLinkText"
          :class="{ active: activePage === index }"
          aria-curret="page"
          :href="page.link.url"
          :title="`This link goes to the ${page.link.text}`"
          @click.prevent="navLinkClick(index)"
        >
          {{ page.link.text }}
        </a>
      </li>
    </ul>
    <button class="btn btn-primary" @click.prevent="changeTheme()">Toggle Theme</button>
  </nav>
</template>

<script>
export default {
  created() {
    this.getThemeSetting();
  },

  computed: {
    publishedPages() {
      return this.pages.filter((p) => p.published);
    },
  },

  props: ["pages", "navLinkClick", "activePage"],

  data() {
    return {
      theme: "light",
    };
  },

  methods: {
    changeTheme() {
      if (this.theme === "light") {
        this.theme = "dark";
        this.storeTheme();
      } else {
        this.theme = "light";
        this.storeTheme();
      }
    },

    storeTheme() {
      localStorage.setItem("theme", this.theme);
    },

    getThemeSetting() {
      let theme = localStorage.getItem("theme");
      if (theme) {
        this.theme = theme;
      }
    },
  },
};
</script>

<style>
#custom-class {
  padding: 0px 40px !important;
  height: 80px;
}

#navLinkText {
  font-size: 20px;
  font-weight: 600;
}

#logoName {
  font-size: 24px;
  font-weight: 600;
  color: #1d861d;

  font-family: sans-serif;
  font-style: italic;
  background-color: yellow;
  padding: 10px;
}
</style>
