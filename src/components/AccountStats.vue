<template>
    <section class="account-stats">
        <div class="account-stats__card">
            <strong>{{ stats.posts }}</strong>
            <span>posts</span>
        </div>
        <div class="account-stats__card">
            <strong>{{ stats.followers }}</strong>
            <span>followers</span>
        </div>
        <div class="account-stats__card">
            <strong>{{ stats.following }}</strong>
            <span>following</span>
        </div>
    </section>
</template>

<script setup>
import { stats } from '../mockData'
</script>

<style scoped lang='scss'>
.account-stats {
    display: flex;
    gap: 2rem;
    padding: 1rem 0;
    &__card {
        display: flex;
        gap: 0.5rem;
    }
}
</style>
