<template>
  <div class="container mb-3" v-if="activePage === 0">
    <form action="">
      <div class="row">
        <div class="col">
          <div class="mb-3">
            <label for="" class="form-label">Page Title</label>
            <input
              type="text"
              class="form-control"
              placeholder="Title"
              v-model="pageTitle"
            />
          </div>
          <div class="mb-3">
            <label for="" class="form-label">Content</label>
            <textarea
              type="text"
              class="form-control"
              rows="5"
              placeholder="Page Content"
              v-model="content"
            ></textarea>
          </div>
        </div>
        <div class="col">
          <div class="mb-3">
            <label for="" class="form-label">Link Text</label>
            <input
              type="text"
              class="form-control"
              placeholder="Link Text"
              v-model="linkText"
            />
          </div>
          <div class="mb-3">
            <label for="" class="form-label">Link URL</label>
            <input
              type="text"
              class="form-control"
              placeholder="Link URL"
              v-model="linkUrl"
            />
          </div>
        </div>
      </div>
      <div class="mb-3">
        <button class="btn btn-primary" @click.prevent="submitForm" :disabled="isFormValid">Create Page</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ["pageCreated", "activePage"],

  computed: {
    isFormValid(){
      return !this.pageTitle || !this.content || !this.linkText || !this.linkUrl
    }
  },

  data() {
    return {
      pageTitle: "",
      content: "",
      linkText: "",
      linkUrl: "",
    };
  },

  methods: {
    submitForm() {
      if (!this.pageTitle || !this.content || !this.linkText || !this.linkUrl) {
        alert("Please fill the all fields!");
        return;
      }
      this.pageCreated({
        link: {
          text: this.linkText,
          url: this.linkUrl,
        },
        title: this.pageTitle,
        content: this.content,
      });
    },

    
  },
};
</script>
