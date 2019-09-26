<template>
    <div>
        <table class="table">
            <tr>
                <td>Правильные ответы:</td>
                <td>{{correct}}</td>
                </tr>
            </table>
    </div>
</template>

<script>
export default {
        props: ['answered'],
        data(){
            return {
                correct: 0
            }
        },
        created() {
            for (let i = 0; i < this.answered.length; i++) {
                    if (this.answered[i]) {
                        console.log(this.answered)
                        this.correct++
                    }
            }
        }
}
</script>