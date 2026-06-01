<template>
    <div class="view-toggler">
        <button type="button" :class="{ 'active': modelValue === 'grid' }" @click="setViewMode('grid')"
            title="Grid view">
            <svg class="icon" viewBox="0 0 24 24">
                <path
                    d="M4 4h4v4H4zm6 0h4v4h-4zm6 0h4v4h-4zM4 10h4v4H4zm6 0h4v4h-4zm6 0h4v4h-4zM4 16h4v4H4zm6 0h4v4h-4zm6 0h4v4h-4z" />
            </svg>
        </button>

        <button type="button" :class="{ 'active': modelValue === 'list' }" @click="setViewMode('list')"
            title="List view">
            <svg class="icon" viewBox="0 0 24 24">
                <path
                    d="M4 10.5c-.83 0-1.5.67-1.5 1.5s.67 1.5 1.5 1.5 1.5-.67 1.5-1.5-.67-1.5-1.5-1.5zm0-6c-.83 0-1.5.67-1.5 1.5s.67 1.5 1.5 1.5 1.5-.67 1.5-1.5-.67-1.5-1.5-1.5zm0 12c-.83 0-1.5.68-1.5 1.5s.68 1.5 1.5 1.5 1.5-.68 1.5-1.5-.67-1.5-1.5-1.5zm5-11.5v2h12v-2H9zm0 14h12v-2H9v2zm0-5h12v-2H9v2z" />
            </svg>
        </button>
    </div>
</template>

<script setup>
defineProps({
    modelValue: {
        type: String,
        default: 'list'
    }
});

const emit = defineEmits(['update:modelValue']);

const setViewMode = (mode) => {
    emit('update:modelValue', mode);
};
</script>

<style scoped lang="scss">
.view-toggler {
    display: inline-flex;
    gap: 4px;
}

.view-toggler button {
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s ease;

    .icon {
        width: 20px;
        height: 20px;
        fill: #b3b3b3;
    }

    &:hover .icon {
        fill: #666;
    }

    &.active {
        .icon {
            fill: $blue-color;
        }
    }
}
</style>