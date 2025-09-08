<template>
    <button type="button" class="button" :disabled="disabled">
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: "vButton",
    props: {
        disabled: {
            type: Boolean,
            default: false
        }
    }
}
</script>

<style lang="scss">
    .button {
        padding: 8px 28px;

        font-weight: 900;
        font-size: 25px;
        font-family: inherit;
        color: #fff;

        background: #000;
        border: none;
        border-radius: 3px;
        cursor: pointer;

        &:disabled {
            cursor: not-allowed;
            background: #BCBCBC;
            color: #8B8B8B;
        }
    }
</style>