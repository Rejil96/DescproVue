<template>
  <div class="container mb-3" id="customCss">
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
          <div class="mb-3">
            <div class="form-check">
              <input
                type="checkbox"
                class="form-check-input"
                id="gridCheck1"
                v-model="published"
              />
              <label class="form-check-label" for="gridCheck1">Published</label>
            </div>
          </div>
        </div>
      </div>
      <div class="mb-3">
        <button
          class="btn btn-primary"
          @click.prevent="submitForm"
          :disabled="isFormValid"
        >
          Create Page
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  props: ["pageCreated"],

  computed: {
    isFormValid() {
      return !this.pageTitle || !this.content || !this.linkText || !this.linkUrl;
    },
  },

  data() {
    return {
      pageTitle: "",
      content: "",
      linkText: "",
      linkUrl: "",
      published: true,
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
        published: this.published,
      });

      this.linkText = "";
      this.linkUrl = "";
      this.pageTitle = "";
      this.content = "";
      this.published = true;
    },
  },

  watch: {
    pageTitle(newTitle, oldTitle) {
      if (this.linkText === oldTitle) {
        this.linkText = newTitle;
      }
    },
  },
};
</script>

<style scoped>
#customCss {
  border-top: 1px solid #e9e9e9;
  padding-top: 60px;
}
</style>
