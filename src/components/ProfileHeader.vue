<template>
    <header class="profile-header">
        <div class="profile-header__content">
            <div class="profile-header__avatar-wrapper">
                <img class="profile-header__avatar" :src="profile.avatar" alt="Avatar" />
            </div>

            <div class="profile-header__main">
                <div class="profile-header__top-row">
                    <h1 class="profile-header__name">{{ profile.name }}</h1>
                    <div class="profile-header__start">
                        <span>Start on 17-02-2016</span>
                    </div>
                </div>

                <AccountStats />
                <DateFilter v-model:dateTo="toDate" />
            </div>
        </div>
    </header>
</template>

<script setup>
import { ref } from 'vue';
import { profile } from '../mockData'
import AccountStats from './AccountStats.vue'
import DateFilter from './DateFilter.vue'
const toDate = ref('09-12-2016');
</script>

<style scoped lang="scss">
.profile-header {
    padding: 2rem 0;
    position: relative;
    z-index: 2;
    background: rgba($light-color, 0.6);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    min-height: 200px;

    &__content {
        display: flex;
        align-items: flex-start;
        gap: 40px;
        max-width: 800px;
        margin: 0 auto;
        padding: 0 1.25rem;
    }

    &__avatar-wrapper {
        position: relative;
        width: 140px;
        height: 140px;
        flex-shrink: 0;
    }

    &__avatar {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }

    &__main {
        display: flex;
        flex-direction: column;
        gap: 16px;
        flex-grow: 1;
        padding-top: 10px;
    }

    &__top-row {
        display: flex;
        align-items: center;
        gap: 15px;
    }

    &__name {
        margin: 0;
        font-size: 1.75rem;
        font-weight: 400;
        color: #000;
        line-height: 1.2;
        font-family: 'Montserrat', sans-serif;
    }

    &__start {
        font-size: 13px;
        border: 1px solid $blue-color;
        color: $blue-color;
        border-radius: 2px;
        padding: 6px 12px;
        display: inline-flex;
        align-items: center;
        justify-content: center;
        white-space: nowrap;
    }
}


@media (max-width: 768px) {
    .profile-header {
        padding: 1.5rem 0;

        &__content {
            flex-direction: column;
            align-items: center;
            gap: 20px;
        }

        &__avatar-wrapper {
            width: 110px;
            height: 110px;
        }

        &__main {
            width: 100%;
            align-items: center;
            padding-top: 0;
            text-align: center;
            gap: 20px;
        }

        &__top-row {
            flex-direction: column;
            gap: 10px;
        }

        &__name {
            font-size: 1.5rem;
        }
    }
}

@media (max-width: 580px) {
    .date-filter {
        flex-direction: column;
        align-items: center;
        gap: 10px;

        &__inputs {
            flex-direction: column;
            gap: 10px;
        }
    }
}
@media (max-width: 480px) {
    .stats-container {
        gap: 15px;
        justify-content: center;
    }
}
</style>