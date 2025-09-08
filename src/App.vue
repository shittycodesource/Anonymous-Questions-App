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
                <div class="form">
                    <v-field 
                        :value="question" 
                        @input="data => question = data"
                     >What's your question?
                    </v-field>
                    <v-field 
                        :value="author" 
                        @input="data => author = data"
                    >Who are you?</v-field>
                    <v-button 
                        @click.native="send" 
                        :disabled="(question.trim('').length == false) || (isSending == true)"
                    >Send</v-button>
                </div>
            </div>
        </main>
    </div>
</template>

<script>
import vField from './components/vField.vue';
import vButton from './components/vButton.vue';

import { db } from './firebase/index';
import { doc, setDoc } from 'firebase/firestore';

export default {
    name: 'App',
    components: {
        vField,
        vButton
    },
    data() {
        return {
            question: '',
            author: '',
            isSending: false
        }
    },
    methods: {
        async send() {
            try {
                if (this.question.trim('').length) {
                    this.isSending = true;

                    const obj = {
                        question: this.question,
                        author: this.author || ''
                    }

                    console.log('Send', obj);

                    const docRef = doc(db, 'questions', 'ID');
                    await setDoc(docRef, obj);

                    this.question = '';
                    this.author = '';

                    this.isSending = false;
                }
            } catch(error) {
                console.log('Send error');
                throw error;
            }
        }
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

.form {
    display: flex;
    flex-direction: column;
    // justify-content: start;
    align-items: start;
    gap: 15px;
    width: 100%;
}

</style>
