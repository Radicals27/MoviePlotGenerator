<template>
    <div class="twist">
        <h4 id="twist">{{ twist }}</h4>
        <button id="getTwist" @click="getTwistData()">Generate Twist</button>
    </div>
</template>

<script>
    export default {
        name: 'Twist',
        props: {
        twist: String
    },
    methods: {
        getTwistData() {
            var twists = [
                ['The final boss is your self.'],
                ['You were dead the whole time.'],
                ['It was all a dream.'],
                ['Enemies copy your moves.'],
                ['When you get to the end you have to go back to the start again.'],
                ['You lose your power as the game goes on.'],
                ['You become the bad guy as time goes on.'],
                ['Your best friend betrays you.'],
                ['You fall in love with the antagonist.'],
                ['You can control time.'],
                ['Set in the 1930\'s.'],
                ['Set in the 60\'s.'],
                ['Set in the 70\'s.'],
                ['Set in the 80\'s.'],
                ['Set in the 90\'s.'],
                ['You play an elderly person.'],
                ['Your character is an outcast.'],
                ['You are an orphan.'],
                ['You are not always in control of your character.'],
            ]
            this.twist = twists[Math.floor(Math.random() * twists.length)][0]
        }
    }     
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
