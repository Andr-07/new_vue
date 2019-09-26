  
<template>
    <div>
        <form>
            {{title}}
            <hr>
            <div v-for="(answer, index) in answers" :key="index">
                <input type="radio" name="radio" @change="sendData(answer.type)">
                <label>{{answer.answer}}</label>
            </div>
            <button :disabled="buttonDisabled" class="btn btn-success" @click.prevent="nextQuestion" @click="showAnswers">Send</button>
        </form>
        {{check}}
    </div>
</template>

<script>
export default {
    props: ['title', 'answers', 'current', 'answered'],
    data() {
        return {
            check: null,
            buttonDisabled: true, 
            actual: this.current,
            answeredArr: this.answered,      }
    },
    methods: {
        sendData(data) {
            this.check = data;
            this.buttonDisabled = false;
            console.log(this.check)

        },
        nextQuestion() {
            this.answeredArr = [...this.answeredArr,this.check]
            this.$emit('nextQ', this.actual)
        },
        showAnswers() {
            this.$emit('showA', this.answeredArr )
        }
    }
}
</script>