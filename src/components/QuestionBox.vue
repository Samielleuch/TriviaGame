<template>
    <v-row justify="center">
        <v-col cols="12" xs="8" sm="8">
            <v-card>
                <v-system-bar color="teal darken-2">

                </v-system-bar>
                <v-toolbar color="teal" dark dense>
                    <v-toolbar-title class="headline">{{ questions[index].question }}</v-toolbar-title>
                    <v-spacer></v-spacer>
                    <v-chip color="teal lighten-5" dark outlined ripple>Score: {{score}}/{{questions.length}}</v-chip>
                </v-toolbar>

                <v-card-text>
                    <v-row>
                        <v-col align="start">
                            <v-list rounded>

                                <v-list-item-group v-model="selected" color="primary">
                                    <template
                                            v-for="(answer , index) in answers">
                                        <v-list-item
                                                :key="index" align="center"
                                                :class="
                                            [ answered ? index === currentCorrectAnswerIndex   ?  'green lighten-1'  : 'red lighten-1' : '' ]"
                                        >
                                            <v-list-item-content>
                                                <v-list-item-title class="title"  > {{answer}}</v-list-item-title>
                                            </v-list-item-content>
                                        </v-list-item>
                                        <v-divider></v-divider>
                                    </template>
                                </v-list-item-group>
                            </v-list>
                        </v-col>
                    </v-row>
                </v-card-text>
                <v-divider></v-divider>
                <v-row justify="center" align="center">
                    <v-btn class=" my-5 , light-blue accent-1 "
                           :disabled="selected === undefined || answered " @click="submit" outlined>Submit</v-btn>
                    <v-btn @click="nextQuestion" class="my-5 , ml-5 , teal accent-1"   outlined>Next</v-btn>
                </v-row>


            </v-card>
        </v-col>
    </v-row>
</template>

<script>
    export default {
        name: "Question Box",
        data: () => ({
            questions: [],
            index: 0,
            selected: undefined,
            currentCorrectAnswerIndex: 0,
            score : 0 ,
            answered : false
        }),
        methods: {
            nextQuestion: function () {
                this.index++;
                this.selected = undefined;
                this.answered = false;

            },
            shuffle(array){
                    const length = array == null ? 0 : array.length;
                    if (!length) {
                        return []
                    }
                    let index = -1;
                    const lastIndex = length - 1;
                    const result = [...array];
                    while (++index < length) {
                        const rand = index + Math.floor(Math.random() * (lastIndex - index + 1));
                        const value = result[rand];
                        result[rand] = result[index];
                        result[index] = value;
                    }
                    return result;
            } ,
            submit() {
                if ( this.selected === this.currentCorrectAnswerIndex ) {
                    this.score++;
                }
                this.answered = true;
            }
        },
        computed: {
            answers: function () {
                let answer = [...this.questions[this.index].incorrect_answers];
                answer.push(this.questions[this.index].correct_answer);
                let shuffled = [...answer];
                shuffled = this.shuffle(shuffled);
                this.currentCorrectAnswerIndex = shuffled.indexOf(this.questions[this.index].correct_answer);
                return shuffled;
            }
        },
        mounted: function () {
            //get the questions from API
            fetch('https://opentdb.com/api.php?amount=10&category=17', {
                method: 'get'
            }).then((response) => {
                return (response.json())
            })
                .then((rsp) => {
                    this.questions = rsp.results
                })

        }
    }
</script>

<style scoped>

</style>