<template>
    <article v-if="viewMode === 'list'" class="post-row-list">
        <div class="post-row-list__image-wrapper">
            <img :src="post.imageUrl" alt="Post preview" class="post-row-list__image" />
        </div>

        <div class="post-row-list__columns">
            <div class="post-column">
                <span class="post-column__title">Today</span>
                <div class="post-column__stats">
                    <span class="stat-item">

                        <img src="../assets/images/iconHeart.svg" alt="heart" />
                        {{ post.metricsToday.likes }}
                    </span>
                    <span class="stat-item">

                        <img src="../assets/images/iconMessage.svg" alt="message" />
                        {{ post.metricsToday.comments }}
                    </span>
                </div>
            </div>

            <div class="post-column">
                <span class="post-column__title">{{ post.metricsHistory.date }}</span>
                <div class="post-column__stats">
                    <span class="stat-item">
                        <img src="../assets/images/iconHeart.svg" alt="heart" />
                        {{ post.metricsHistory.likes }}
                    </span>
                    <span class="stat-item">
                        <img src="../assets/images/iconMessage.svg" alt="message" />
                        {{ post.metricsHistory.comments }}
                    </span>
                </div>
            </div>

            <div class="post-column">
                <span class="post-column__title">Image upload</span>
                <span class="post-column__date">{{ post.uploadDate }}</span>
            </div>
        </div>
    </article>

    <article v-else class="post-grid-card">
        <div class="post-grid-card__image-wrapper">
            <img :src="post.imageUrl" alt="Grid preview" class="post-grid-card__image" />
        </div>

        <div class="post-grid-card__content">
            <div class="grid-meta-row">
                <span class="grid-meta-row__title">Today</span>
                <span class="grid-meta-row__title">{{ post.metricsHistory.date }}</span>

            </div>
            
            <div class="grid-meta-row">
                <div class="grid-meta-row__stats">
                    <span> <img src="../assets/images/iconHeart.svg" alt="heart" /> {{ post.metricsToday.likes
                        }}</span>
                    <span> <img src="../assets/images/iconMessage.svg" alt="message" /> {{
                        post.metricsToday.comments
                        }}</span>
                </div>
                <div class="grid-meta-row__stats">
                    <span> <img src="../assets/images/iconHeart.svg" alt="heart" /> {{ post.metricsHistory.likes
                        }} </span>
                    <span> <img src="../assets/images/iconMessage.svg" alt="message" /> {{
                        post.metricsHistory.comments
                        }}</span>
                </div>
            </div>

            <div class="grid-meta-row grid-meta-row--upload">
                <span class="grid-meta-row__title">Image upload</span>
                <span class="grid-meta-row__date">{{ post.uploadDate }}</span>
            </div>
        </div>
    </article>
</template>

<script setup>
defineProps({
    post: { type: Object, required: true },
    viewMode: { type: String, default: 'list' }
});
</script>

<style scoped lang="scss">
.post-row-list {
    display: flex;
    align-items: center;
    background: #fff;
    border-bottom: 1px solid #f2f4f6;
    width: 100%;
    margin: 8px 0;

    &__image-wrapper {
        width: 86px;
        height: 86px;
        flex-shrink: 0;
    }

    &__image {
        width: 100%;
        height: 100%;
        object-fit: cover;
        border-radius: 4px;
    }

    &__columns {
        display: grid;
        grid-template-columns: 2fr 2fr 1.5fr;
        flex-grow: 1;
        padding: 0 1.5rem;
        align-items: center;
        gap: 16px;
    }
}

.post-column {
    display: flex;
    flex-direction: column;
    gap: 6px;

    &__title {
        font-size: 14px;
        font-weight: 600;
        color: #1a1a1a;
    }

    &__stats {
        display: flex;
        gap: 12px;
    }

    &__date {
        font-size: 13px;
        color: #666;
    }
}

.stat-item {
    display: flex;
    align-items: center;
    gap: 4px;
    font-size: 13px;
    font-weight: 700;
    color: #1a1a1a;
}

.icon {
    width: 14px;
    height: 14px;
    fill: #000000;
    display: inline-block;

    &--small {
        width: 12px;
        height: 12px;
    }
}

@media (max-width: 450px) {
    .post-row-list {
        &__columns {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            padding: 0 1rem;
        }
    }
}


.post-grid-card {
    display: flex;
    flex-direction: column;
    background: #ffffff;
    border: 1px solid #eef2f5;
    border-radius: 6px;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.02);

    width: 100%;
    max-width: 240px;
    margin: 0 auto;
    flex-shrink: 0;

    &__image-wrapper {
        width: 100%;
        aspect-ratio: 1 / 1;
        overflow: hidden;
        background: #f9f9f9;
        flex-shrink: 0;
    }

    &__image {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    &__content {
        padding: 16px 14px;
        display: flex;
        flex-direction: column;
        flex-grow: 1;
    }
}

.grid-meta-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 8px;

    &__title {
        font-size: 13px;
        font-weight: 600;
        color: #1a1a1a;
    }

    &__stats {
        display: flex;
        align-items: center;
        gap: 10px;

        & span {
            display: flex;
            align-items: center;
            gap: 4px;
            font-size: 13px;
            font-weight: 700;
            color: #1a1a1a;
        }
    }

    &__date {
        font-size: 12px;
        color: #666;
    }

    &--upload {
        margin-top: auto;
        margin-bottom: 0;
        border-top: 1px dashed #f0f0f0;
        padding-top: 8px;
    }
}

.stat-item-grid {
    display: flex;
    align-items: center;
    gap: 4px;
    font-size: 12px;
    font-weight: 700;
    color: #1a1a1a;
}

.icon {
    width: 14px;
    height: 14px;
    fill: #000000;
    display: inline-block;
}

.post-grid-card {
    display: flex;
    flex-direction: column;
    background: #ffffff;
    border: 1px solid #eef2f5;
    border-radius: 6px;
    overflow: hidden;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.02);
    width: 100%;

    &__image-wrapper {
        width: 100%;
        aspect-ratio: 12 / 12;
        overflow: hidden;
        background: #f9f9f9;
    }

    &__image {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    &__content {
        padding: 14px;
        display: flex;
        flex-direction: column;
        gap: 10px;
    }
}

.grid-meta-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 13px;

    &__title {
        font-weight: 600;
        color: #1a1a1a;
    }

    &__stats {
        display: flex;
        align-items: center;
        gap: 10px;
        font-weight: 700;
    }

    &__date {
        color: #666;
    }



    &--upload {
        margin-top: 2px;
        border-top: 1px dashed #f0f0f0;
        padding-top: 8px;
    }
}
</style>