<template>
    <div class="field">
        <label class="field__label"><slot></slot></label>
        <textarea 
            class="field__input"
            :class="{ 'field__input--focused': isFocused }" 
            :value="value" 
            v-on:input="handler" 
            @focusin="isFocused = true"
            @focusout="isFocused = false"
        ></textarea>
    </div>
</template>

<script>
export default {
    name: "vField",
    data() {
        return {
            isFocused: false
        }
    },
    props: {
        value: {
            type: String,
            default: ''
        }
    },
    methods: {
        handler(data) {
            this.$emit('input', data.target.value);
        }
    }
}
</script>

<style lang="scss">
    .field {
        display: flex;
        flex-direction: column;

        width: 100%;

        &__label {
            margin-bottom: 15px;

            font-family: inherit;
            font-weight: 900;
            font-size: 30px;
            color: #000;
        }

        &__input {
            background: #F3F3F3;
            border: 1px solid #E4E4E4;
            
            resize: none;

            font-family: inherit;
            font-size: 30px;
            font-weight: 900;

            height: auto;

            transition: border-color .2s linear;

            outline: none;
            
            &:focus {
                border-color: #000;
            }
        }

    }
</style>