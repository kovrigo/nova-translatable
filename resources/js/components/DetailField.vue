<template>
    <panel-item :field="field">
        <template slot="value">

            <a 
                class="inline-block cursor-pointer mr-4 animate-text-color select-none  mini-tab" 
                :class="{ 'active': localeKey === currentLocale }"
                :key="`a-${localeKey}`" 
                v-for="(locale, localeKey) in field.locales"
                @click="changeTab(localeKey)"
            >
                {{ locale }}
            </a>

            <div class="mt-4">
                <div v-if="field.asHtml" v-html="value"></div>
                <div v-else :class="{ 'truncate': field.truncate }">{{ value }}</div>
            </div>

        </template>
    </panel-item>
</template>

<script>
export default {
    props: ['resource', 'resourceName', 'resourceId', 'field'],

    data() {
        return {
            currentLocale: this.field.currentLocale
        }
    },

    methods: {
        changeTab(locale) {
            this.currentLocale = locale
        }
    },

    computed: {
        value() {
            return this.field.value[this.currentLocale] || '—'
        }
    },
}
</script>
