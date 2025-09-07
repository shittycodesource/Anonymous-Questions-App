<template>
    <div id="app">
        <aside class="sidebar">
            <div class="sidebar__inner">
                <header class="sidebar__header">
                    <h1 class="sidebar__title">
                        ANONYMOUS QUESTIONS
                    </h1>
                </header>
            </div>
        </aside>

        <main class="main">
            <div class="container">
                <v-field>What's your question?</v-field>
            </div>
        </main>
    </div>
</template>

<script>
import vField from './components/vField.vue';

export default {
    name: 'App',
    components: {
        vField
    }
}
</script>

<style lang="scss">

body {
    --sidebar-width: 340px;
    --sidebar-bg: #050505;

    --container-width: 1050px;
    --container-padding: 15px;


    font-family: "Inter", sans-serif;
    font-weight: 400;
    color: #000;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

    padding: 0;
    margin: 0;
}

*,*::before,*::after {
    box-sizing: border-box;
}

h1,h2,h3,h4,h5,h6 {
    padding: 0;
    margin: 0;
}

.sidebar {
    width: var(--sidebar-width);

    background: var(--sidebar-bg);

    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;

    &__header {
        padding: 8px 8px 0;
    }

    &__title {
        color: #fff;
        font-size: 34px;
        font-weight: 900;

        line-height: .8;
    }
}

.main {
    padding-left: var(--sidebar-width);
}

.container {
    max-width: var(--container-width);
    padding: 0 var(--container-padding);
    margin: 0 auto;
    width: 100%;
}

</style>
