<template>
    <div>
        <form>
            {{title}}
            <hr>
            <div v-for="answer in answers">
                <input type="radio" name="radio" @change="sendData(answer.type)">
                <label>{{answer.answer}}</label>
            </div>
            <button :disabled="buttonDisabled" class="btn btn-success" @click.prevent="newQuestion(current)">Send</button>
        </form>
        {{check}}
    </div>
</template>

<script>
export default {
    props: ['title', 'answers', 'current'],
    data() {
        return {
            check: null,
            buttonDisabled: true,
        }
    },
    methods: {
        sendData(data) {
            this.check = data;
            this.buttonDisabled = false;
        },
        newQuestion(x) {
            current++;
            this.$emit('changevalue', this.current)
        }
    }
}
</script>