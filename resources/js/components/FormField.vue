<template>
    <default-field :field="field" :errors="errors">
        <template slot="field">
            <el-select 
                class="w-full" 
                :class="errorClasses"
                :placeholder="field.name"
                v-model="value" 
                multiple
            >
                <el-option v-for="option in field.options"
                    :key="option.value"
                    :label="option.label"
                    :value="option.value">
                </el-option>
            </el-select>
        </template>
    </default-field>
</template>

<script>
import { FormField, HandlesValidationErrors } from 'laravel-nova'

export default {
    mixins: [FormField, HandlesValidationErrors],

    props: ['resourceName', 'resourceId', 'field'],

    methods: {
        /*
         * Set the initial, internal value for the field.
         */
        setInitialValue() {
            this.value = this.field.value.map(value  => value.id) || []
        },

        /**
         * Fill the given FormData object with the field's internal value.
         */
        fill(formData) {
            formData.append(this.field.attribute, this.value || [])
        },

        /**
         * Update the field's internal value.
         */
        handleChange(value) {
            this.value = value
        },
    },
}
</script>
