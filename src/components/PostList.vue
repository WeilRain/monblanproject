<template>
    <div :class="viewMode === 'grid' ? 'grid-wrapper' : 'list-wrapper'">
        <PostRow v-for="post in posts" :key="post.id" :post="post" :view-mode="viewMode" />
        <button class="btn-load">Load More</button>
    </div>
</template>
<script setup>
import PostRow from './PostRow.vue';
import { posts } from '../mockData';

defineProps({
    post: { type: Object, required: true },
    viewMode: { type: String, default: 'list' }
});
</script>

<style scoped lang="scss">
.list-wrapper {
    display: flex;
    flex-direction: column;
    border-bottom: none;
    border-radius: 4px;
    width: 100%;
}

.grid-wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 24px;
    width: 100%;
    padding: 16px 0;
    max-width: 700px;
    margin: 0 auto;
}

.btn-load {
    background: transparent;
    border: 1px solid #ccc;
    padding: 8px 16px;
    font-weight: 600;
    color: #666;
    border-radius: 14px;
    cursor: pointer;

    grid-column: 1 / -1;
    justify-self: center;
    width: max-content;

    margin: 20px auto;

    &:hover {
        border-color: #999;
        color: #333;
    }
}
</style>