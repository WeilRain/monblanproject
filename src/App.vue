<script setup>
import { ref } from 'vue';
import ProfileHeader from './components/ProfileHeader.vue'
import ViewToggler from './components/ViewToggler.vue'
import PostList from './components/PostList.vue'
const viewMode = ref('list');
</script>

<template>
  <div id="app">
    <span class="app-bg"> <img src="./assets/images/bg-placeholder.svg" alt=""></span>
    <img src="./assets/images/rectangle 20.svg" alt="">
    <img src="./assets/images/rectangle 20-2.svg" alt="">
    <img src="./assets/images/rectangle 20-3.svg" alt="">
    <ProfileHeader />
    <main>
      <div class="toolbar">
        <ViewToggler v-model="viewMode" />
      </div>
      <PostList :view-mode="viewMode" />
    </main>
    <span class="app-bg-bottom"> <img src="./assets/images/bg-placeholder2.svg" alt=""></span>

  </div>

</template>

<style scoped lang="scss">
#app {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
  position: relative;
  min-height: 100vh;
  width: 100%;
  overflow-x: hidden;
}

.app-bg {
  position: absolute;
  top: 0;
  left: 0;
  height: auto;
  pointer-events: none;
  z-index: -1;

  img {
    width: 100%;
    display: block;
  }
}

.app-bg-bottom {
  position: absolute;
  bottom: 0;
  right: 0;
  height: auto;
  pointer-events: none;
  z-index: -1;

  img {
    width: 100%;
    display: block;
  }
}

.toolbar {
  display: flex;
  justify-content: flex-end;
  gap: 1rem;
  align-items: center;
  padding: 0.5rem 0;
  position: relative;
  z-index: 2;
}

main {
  max-width: 880px;
  width: 100%;
  margin: 0 auto;
  position: relative;
  padding: 0 10px;
}
</style>
