<template>
    <div v-if="field.asHtml" v-html="value" class="py-1"></div>
    <span v-else class="whitespace-no-wrap">{{ value }}</span>
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
