<template>
    <div class="field">
        <label class="field__label"><slot></slot></label>
        <textarea class="field__input"></textarea>
    </div>
</template>

<script>
export default {
    name: "vField"
}
</script>

<style lang="scss">
    .field {
        display: flex;
        flex-direction: column;

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
        }
    }
</style>