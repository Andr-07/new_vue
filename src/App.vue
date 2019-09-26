<template>
    <div class="sample">
        <app-question
        :title="questions[current].title"
        :answers="questions[current].answers"
        :current="current">
        </app-question>
    </div>
</template>

<script>
import AppQuestion from './components/Question'
export default {
    components: {
        AppQuestion
    },
    data() {
        return {
            questions: getData(),
            current: 0
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
}
]
}
</script>
