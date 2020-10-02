<template>
  <div id="app">
    <a href="https://www.mainvest.com/?utm_source=opensource&utm_medium=referral&utm_campaign=vue-simple-icons" target="_blank" class="credit">
      <span>Invest in Main Street</span> 🏘📊🇺🇸
    </a>
    <github
      v-tippy="{ title: 'Star me on GitHub', trigger: 'mouseenter ' }"
      fill="white"
      slug="mainvest/vue-simple-icons"
      id="github"
    >
    </github>
    <header class="header">
      <div class="container">
        <h1 class="hero-heading">vue-simple-icons</h1>
        <h2 class="desc">
          <a href="https://simpleicons.org/" target="_blank">Simple Icons</a> as Vue components.
        </h2>
      </div>
    </header>
    <div class="container">
      <div class="search-bar">
        <input
          type="text"
          class="search-input"
          v-model="keyword"
          :placeholder="`Search ${icons.length} icons...`"
        />
      </div>
      <div class="icons">
        <div
          class="icon"
          v-tippy="{ interactive: true }"
          :title="example"
          v-for="icon in filteredIcons"
          @click="handleClickIcon(icon)"
          :key="icon"
        >
          <component :is="icon" class="icon-svg"></component>
          <span>{{ icon }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import kebab from "lodash.kebabcase";
import Github from "vue-github-badge";
import * as icons from "../src";
import example from "./example.md";

export default {
  data() {
    return {
      icons: Object.keys(icons),
      keyword: "",
      hoverIcon: "",
      hoverSize: "",
      year: new Date().getFullYear(),
      exampleSizes: ["24", "1x", "1.5x", "2x", "3x", "4x"],
    };
  },
  computed: {
    filteredIcons() {
      const keyword = this.keyword.trim().toLowerCase();
      if (!keyword) return this.icons;

      return this.icons.filter((name) => {
        return name.toLowerCase().indexOf(keyword) > -1;
      });
    },
    example() {
      return example
        .replace(/ICON/g, this.hoverIcon)
        .replace(/kebab-icon/g, kebab(this.hoverIcon));
    },
  },
  methods: {
    handleClickIcon(icon) {
      this.hoverIcon = icon;
    },
    handleClickSize(size) {
      this.hoverSize = size;
    },
    sizeExample(size) {
      return example
        .replace("1.5x", size)
        .replace(/ICON/g, "FacaebookIcon")
        .replace(/kebab-icon/g, "facebook-icon");
    },
  },
  components: {
    ...icons,
    Github,
  },
};
</script>

<style src="v-tippy/dist/tippy.css"></style>
<style src="prismjs/themes/prism.css"></style>

<style>
@import url('https://rsms.me/inter/inter.css');

#github {
  position:absolute !important;
  top:40px !important;
  right: 15px !important;
}

a.credit {
  padding: 4px 8px;
  background: #004080;
  text-align: center;
  width:100%;
  display:block;
  position:fixed;
  top:0;
  left:0;
  right:0;
  z-index:10000;
}

a.credit:hover {
  text-decoration: none;
}

a.credit span {
  font-size:80%;
  line-height:0.9;
  color: rgba(255,255,255,0.9);
  display:inline-block;
  transform: translateY(-1px);
  border-bottom: 1px solid rgba(255,255,255,0.75);
}

body {
  margin: 0;
  font: 14px/1.4 "Inter", "Helvetica Neue", Helvetica, Arial, sans-serif;
}

* {
  box-sizing: border-box;
}

a {
  color: #333;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

.container {
  max-width: 1080px;
  margin: 0 auto;
  padding: 0 10px;
}

.tippy-tooltip {
  text-align: left;
}

.tippy-tooltip-content pre {
  margin: 0;
  padding: 16px;
  overflow: auto;
  font-size: 85%;
  line-height: 1.45;
  border-radius: 3px;
}

.tippy-tooltip-content pre code {
  overflow: visible;
  word-wrap: normal;
  font-family: Consolas, Monaco, "Andale Mono", "Ubuntu Mono", monospace;
}

.tippy-popper {
  max-width: 450px;
}

.tippy-popper .tippy-tooltip.light-theme[data-animatefill] {
  background-color: white;
}
</style>

<style scoped>
.header {
  background: #263238;
  padding: 70px 0 40px;
}

.desc {
  color: white;
  font-weight: 400;
}

.desc a {
  color:#ffffff !important;
  text-decoration: underline;
}

.hero-heading {
  color: #ffffff;
  margin: 0;
  font-size: 2rem;
  font-weight: 500;
}

.icons {
  display: flex;
  flex-wrap: wrap;
}

.icon {
  display: flex;
  align-items: center;
  padding: 10px;
  width: 25%;
  border-radius: 3px;
  cursor: pointer;
}

.icon:hover {
  background: #f1f5ff;
}

.icon-svg {
  margin-right: 10px;
}

.search-bar {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100px;
}

.search-input {
  padding: 10px;
  outline: none;
  width: 100%;
  font-size: 1rem;
  border: 1px solid #e2e2e2;
  border-radius: 3px;
}

.search-input:focus {
  border-color: #ccc;
}

@media screen and (max-width: 768px) {
  .icon {
    width: 100%;
  }
}
</style>
