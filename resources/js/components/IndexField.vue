<template>
    <div v-if="field.asHtml" v-html="value" class="py-1" :class="`text-${field.textAlign}`"></div>
    <div v-else class="" :class="`text-${field.textAlign}`">{{ value }}</div>
</template>

<script>
export default {
    props: ['resourceName', 'field'],
    computed: {
        value() {
            return this.field.value[this.field.indexLocale] || '—'
        }
    }
}
</script>
