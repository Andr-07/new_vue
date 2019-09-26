<template>
    <div class="sample">
        <div v-if="showQuestion">
        <app-question
        :title="questions[current].title"
        :answers="questions[current].answers"
        :current="current" @nextQ="nextQuestion"
        @showA="showAnswers"
        :answered="answered">
        </app-question>
        </div>
        <div v-else>
        <app-results
        :answered="answered">
        </app-results>
        </div>
    </div>
</template>

<script>
import AppQuestion from './components/Question';
import AppResults from './components/Results';

export default {
    components: {
        AppQuestion, AppResults
    },
    data() {
        return {
            questions: getData(),
            current: 0,
            showQuestion: true,
            answered: []
        }
    },
    methods: {
        nextQuestion(){
            if (this.current < this.questions.length-1){
            this.current++
            } else {
                this.endQuestions();
            }
        },
        endQuestions(){
            this.showQuestion = false;
        },
        showAnswers(data){
            this.answered = data
        }

    }
    
}
function getData() {
    return [{
        title: "How old are you?",
        answers: [{
                answer: 15,
                type: true
            },
            {
                answer: 16,
                type: false
            }]
},
{
        title: "What is your name?",
        answers: [{
                answer: "Andrey",
                type: true
            },
            {
                answer: "Oleg",
                type: false
            }]
},
{
        title: "What is city?",
        answers: [{
                answer: "Moscow",
                type: true
            },
            {
                answer: "Samara",
                type: false
            }]
}
]
}
</script>