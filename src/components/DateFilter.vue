<template>
    <div class="date-filter">
        <span class="date-filter__title">Date</span>

        <div class="date-filter__inputs">
            <div class="date-input-group">
                <VDatePicker v-model="dateFromValue" mode="date"
                    :popover="{ visibility: 'click', placement: 'bottom-start', width: 230, teleport: 'body' }">
                    <template #default="{ inputValue, inputEvents }">
                        <div class="custom-input" v-on="inputEvents">
                            <input type="text" :value="formatDisplayDate(inputValue)" readonly placeholder="from" />
                            <div class="custom-input__actions">
                                <button type="button" class="btn-clear" v-if="dateTo" @click.stop="clearDate('from')">
                                    <img src="../assets/images/iconX.svg" alt="Clear" />
                                </button>
                                <span class="icon-calendar">
                                    <img src="../assets/images/bx_bx-calendar.svg" alt="Calendar" />
                                </span>
                            </div>
                        </div>
                    </template>
                </VDatePicker>
            </div>
            <div class="date-input-group">
                <VDatePicker v-model="dateToValue" mode="date"
                    :popover="{ visibility: 'click', placement: 'bottom-start', width: 230, teleport: 'body' }">
                    <template #default="{ inputValue, inputEvents }">
                        <div class="custom-input" v-on="inputEvents">
                            <input type="text" :value="formatDisplayDate(inputValue)" readonly placeholder="to" />
                            <div class="custom-input__actions">
                                <button type="button" class="btn-clear" v-if="dateTo" @click.stop="clearDate('to')">
                                    <img src="../assets/images/iconX.svg" alt="Clear" />
                                </button>
                                <span class="icon-calendar">
                                    <img src="../assets/images/bx_bx-calendar.svg" alt="Calendar" />

                                </span>
                            </div>
                        </div>
                    </template>
                </VDatePicker>
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed } from 'vue';

const props = defineProps({
    dateFrom: { type: String, default: '' },
    dateTo: { type: String, default: '' }
});

const emit = defineEmits(['update:dateFrom', 'update:dateTo']);

const parseStringToDate = (dateStr) => {
    if (!dateStr) return null;
    const [day, month, year] = dateStr.split('-');
    return new Date(`${year}-${month}-${day}`);
};

const formatDateToString = (dateObj) => {
    if (!dateObj) return '';
    const day = String(dateObj.getDate()).padStart(2, '0');
    const month = String(dateObj.getMonth() + 1).padStart(2, '0');
    const year = dateObj.getFullYear();
    return `${day}-${month}-${year}`;
};

const dateFromValue = computed({
    get: () => parseStringToDate(props.dateFrom),
    set: (val) => emit('update:dateFrom', formatDateToString(val))
});

const dateToValue = computed({
    get: () => parseStringToDate(props.dateTo),
    set: (val) => emit('update:dateTo', formatDateToString(val))
});

const formatDisplayDate = (val) => {
    return val ? val.replace(/\./g, '_').replace(/-/g, '_') : '';
};

const clearDate = (type) => {
    if (type === 'from') emit('update:dateFrom', '');
    if (type === 'to') emit('update:dateTo', '');
};
</script>

<style scoped lang="scss">
.date-filter {
    display: flex;
    align-items: center;
    gap: 15px;
    font-family: Arial, sans-serif;
    padding: 10px 0;

    &__title {
        font-size: 15px;
        font-weight: normal;
        color: #000;
    }

    &__inputs {
        display: flex;
        gap: 12px;
        flex-wrap: wrap;
        justify-content: center;
    }
}

.date-input-group {
    position: relative;
    z-index: 3;
}

.custom-input {
    display: flex;
    align-items: center;
    border: 1px solid #dcdcdc;
    border-radius: 4px;
    background: #fff;
    height: 28px;
    cursor: pointer;
    overflow: hidden;

    input {
        border: none;
        outline: none;
        font-size: 13px;
        padding: 0 10px;
        width: 95px;
        cursor: pointer;
        color: #333;
        font-weight: 500;
        background: transparent;

        &::placeholder {
            color: #999;
        }
    }

    &__actions {
        display: flex;
        align-items: center;
        height: 100%;
        background: #f0f0f0;
        border-left: 1px solid #dcdcdc;
    }
}

.btn-clear {
    background: transparent;
    border: none;
    border-right: 1px solid #dcdcdc;
    cursor: pointer;
    height: 100%;
    padding: 0 8px;
    display: flex;
    align-items: center;
    justify-content: center;

    &:hover .icon-close {
        fill: #333;
    }
}

.icon-calendar {
    height: 100%;
    padding: 0 8px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.icon-close,
.icon-cal {
    width: 18px;
    height: 18px;
    fill: #666;
}
</style>