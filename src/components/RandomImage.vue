<!-- src/components/RandomImage.vue -->
<template>
  <div>
    <img :src="randomImageUrl" alt="Random Image" />
    <button @click="getRandomImage">Get Random Image</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      randomImageUrl: "",
    };
  },
  methods: {
    getRandomImage() {
      // Lorem Picsumのランダム画像APIを使用
      fetch("https://picsum.photos/200/300?random")
        .then((response) => response.url)
        .then((url) => {
          this.randomImageUrl = url;
        })
        .catch((error) => {
          console.error("Error fetching random image:", error);
        });
    },
  },
};
</script>

<style scoped>
/* スタイリングを追加（任意） */
img {
  max-width: 100%;
  height: auto;
}
</style>
