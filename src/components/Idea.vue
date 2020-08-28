<template>
    <div class="plot">
        <h3>Movie Idea:</h3>
        <h4 id="act1">Act 1: {{ act1 }}</h4>
        <h4 id="act2">Act 2: {{ act2 }}</h4>
        <h4 id="act3">Act 3: {{ act3 }}</h4>
        <button id="getPlot" @click="getPlotData()">Generate Plot</button>
    </div>
</template>

<script>
    export default {
        name: 'Plot',
        props: {
        act1: String,
        act2: String,
        act3: String
    },
    methods: {
        getPlotData() {
            var actTemplates = [
                // Act 1
                [
                    [['We meet a '],['protagonistGender'],[' called '],['protagonistName'],[' who is quite '],['adjective'],[' and wants more '],['itemsPlural'],[' in '],['protagonistPronounOwn'], [' life.']],
                    [['protagonistName'],[' is a '],['profession'],[' but really wants to be a '],['profession'],[' so '],['protagonistPronoun'], [' can '],['verb'],[' like '],['protagonistPronoun'], [' always wanted to.']],
                    [['We are introduced to '],['protagonistName'],[' who is extremely '],['adjective'],['...']],
                    [['protagonistName'],[' has had enough of '],['protagonistPronounOwn'],[' small town and wants out, but '],['event'],[' is preventing this.']],

                ],
                // Act 2
                [
                    [['One day '],['protagonistPronoun'],[' meets '],['antagonistName'],[' who introduces '],['protagonistPronounOwn'],[' to the world of '],['itemsPlural'],[' but it is a very '],['adjective'],[' world to '],['protagonistName'],['.']],
                    [['The situation worsens until one day '],['protagonistName'],[' teams up with '],['antagonistName'],[' who takes '],['antagonistPronoun'],[' to a '],['location'],[' but it is a very '],['adjective'],[' place... ']],
                    [['Suddenly there is an invasion of '],['nounsPlural'],[' armed with '],['itemsPlural'],[', lead by '],['antagonistName'],[' who intends to take over '],['location'],[' in a very '],['adjective'],[' way... ']],

                ],
                // Act 3
                [
                    [['Finally '],['protagonistName'],[' learns to overcome '],['protagonistPronounOwn'],[' fears and stands up to '],['antagonistName'],['.']],
                    [['In the end, '],['protagonistName'],[' understands the true power of friendship and realises that '],['antagonistName'],[' was just what '],['protagonistPronoun'],[' needed.']],

                    
                ]
            ]

            var namesFemale = [['Jane'],['Olivia'],['Tanya'],['Sarah'],['Ellen'],['Lauren'],['Linda'],['Jess'],['Claire']]
            var namesMale = [['Tom'],['Dave'],['Dale'],['Glen'],['Matt'],['Conrad'],['Luke'],['Aaron'],['Dwayne']]
            var professions = [['bouncer'],['baker'],['security guard'],['escort'],['programmer'],['architect'],['actor'],['writer'],['assassin'],]
            var styles = [['noir'],['biopic'],['scifi'],['horror'],['action'],['drama'], ['comedy'], ['slasher'], ['western']]
            var nouns = [['fairy'],['bear'],['alien'],['programmer'],['used car salesman'],['politician'],['bird'],['druglord'],['exotic dancer'],['mobster'],['astronaut'], ['scientist'],['actor'],['totally normal person'],['woman'],['man'],['inventor'],['celebrity']]
            var nounsPlural = [['fairies'],['bears'],['aliens'],['programmers'],['used car salesmen'],['politicians'],['birds'],['druglords'],['exotic dancers'],['mobsters'],['astronauts'], ['scientists'],['actors'],['totally normal people'],['women'],['men'],['inventors'],['celebrities']]
            var verbs = [['jump'],['crawl'],['roll'],['climb'],['teleport'],['program'],['shout'],['paint'],['attack'],['die'],['laugh'],['punch'],['kick'],['fly'],['sing'],['think'],['pray'],['swim'],['cheat'],['train'],['drive'],['turn invisible'],['act'],['perform']]
            var events = [['a movie'],['a storm'],['a dream'],['a breakup'],['a work meeting'],['a car race'],['a battle'],['a confrontation'],['a fight'],['a holiday'],['a workday'],['a very cold day'],['Christmas'],['Thanksgiving'],['Easter'],['a snowstorm'],['a solar flare'],['a hospital visit'],['an accident'],['a plane trip'],['a road trip'],['a recession'],['a pandemic']]
            var locations = [['bedroom'],['podcast'],['kitchen'],['library'],['school'],['graveyard'],['space station'],['spaceship'],['cinema'],['body'],['city'],['country town'],['desert'],['plate of food'],['brain'],['dream'],['fantasy world'],['scifi world'],['future time'],['past time'],['pool'],['prison']]
            var adjectives = [['scary'],['thrilling'],['anxiety-provoking'],['hilarious'],['wacky'],['stupid'],['religious'],['psychedelic'],['sloppy'],['dark'],['cheerful'],['speedy'],['calming'],['cooperative'],['silly'],['sassy'],['somber'],['clumsy'],['animated'],['sexy']]
            var feelings = [['sad'],['happy'],['angry'],['lost'],['anxious'],['scared'],['nostalgic'],['confused'],['smart'],['dumb'],['awesome'],['weird']]
            var itemsSingular = [['magic wand'],['hand'],['sadness'],['car'],['gun'],['baseball bat'],['yo-yo'],['fist']]
            var itemsPlural = [['hands'],['stamps'],['feelings'],['rubber bands'],['pencils'],['guns'],['plants'],['teeth'],['siblings']]
            var verbing = [['sabotaging'],['creating'],['analyzing'],['eating'],['humiliating'],['challenging'],['cooking'],['annoying']]

            var moviePlot = ""
            var protagonistGender
            var protagonistPronoun
            var protagonistPronounOwn
            var protagonistName

            var antagonistGender
            var antagonistPronoun
            var antagonistPronounOwn
            var antagonistName

            var p = Math.round((Math.random() * 1) + 1)
            if(p == 0) {
                protagonistGender = "man"
            }
            else {
                protagonistGender = "woman"
            }

            protagonistGender == "man" ? protagonistPronoun = "he" : protagonistPronoun = "she"
            protagonistGender == "man" ? protagonistPronounOwn = "his" : protagonistPronounOwn = "her"
            protagonistGender == "man" ? protagonistName = namesMale[Math.floor(Math.random() * namesMale.length)] : protagonistName = namesFemale[Math.floor(Math.random() * namesFemale.length)]

            var a = Math.round((Math.random() * 1) + 1)
            if(a == 0) {
                antagonistGender = "man"
            }
            else {
                antagonistGender = "woman"
            }

            antagonistGender == "man" ? antagonistPronoun = "he" : antagonistPronoun = "she"
            antagonistGender == "man" ? antagonistPronounOwn = "his" : antagonistPronounOwn = "her"
            antagonistGender == "woman" ? antagonistName = namesMale[Math.floor(Math.random() * namesMale.length)] : antagonistName = namesFemale[Math.floor(Math.random() * namesFemale.length)]

            var i
            var r
            // Act 0 is actually act1
            var act = 0
            var words

            while (act < 3) {
                moviePlot = ""
                formattedPlot = ""
                r = Math.floor(Math.random() * Math.floor(actTemplates[act].length))

                for (i = 0; i < actTemplates[act][r].length; i++) {
                    words = actTemplates[act][r][i]

                    if(actTemplates[act][r][i].includes("style")){
                        words = styles[Math.floor(Math.random() * styles.length)]
                    }
                    if(actTemplates[act][r][i].includes("noun")){
                        words = nouns[Math.floor(Math.random() * nouns.length)]
                    }
                    if(actTemplates[act][r][i].includes("verb")){           
                        words = verbs[Math.floor(Math.random() * verbs.length)]
                    }
                    if(actTemplates[act][r][i].includes("event")){
                        words = events[Math.floor(Math.random() * events.length)]
                    }
                    if(actTemplates[act][r][i].includes("location")){
                        words = locations[Math.floor(Math.random() * locations.length)]
                    }
                    if(actTemplates[act][r][i].includes("adjective")){
                        words = adjectives[Math.floor(Math.random() * adjectives.length)]
                    }
                    if(actTemplates[act][r][i].includes("feeling")){
                        words = feelings[Math.floor(Math.random() * feelings.length)]
                    }
                    if(actTemplates[act][r][i].includes("itemsSingular")){
                        words = itemsSingular[Math.floor(Math.random() * itemsSingular.length)]
                    }
                    if(actTemplates[act][r][i].includes("itemsPlural")){
                        words = itemsPlural[Math.floor(Math.random() * itemsPlural.length)]
                    }
                    if(actTemplates[act][r][i].includes("verbing")){
                        words = verbing[Math.floor(Math.random() * verbing.length)]
                    }
                    if(actTemplates[act][r][i].includes("profession")){
                        words = professions[Math.floor(Math.random() * professions.length)]
                    }
                    if(actTemplates[act][r][i].includes("nounsPlural")){
                        words = nounsPlural[Math.floor(Math.random() * nounsPlural.length)]
                    }
                    if(actTemplates[act][r][i].includes("protagonistName")){
                        words = protagonistName
                    }
                    if(actTemplates[act][r][i].includes("protagonistPronoun")){
                        words = protagonistPronoun
                    }
                    if(actTemplates[act][r][i].includes("protagonistPronounOwn")){
                        words = protagonistPronounOwn
                    }
                    if(actTemplates[act][r][i].includes("protagonistGender")){
                        words = protagonistGender
                    }
                    if(actTemplates[act][r][i].includes("antagonistName")){
                        words = antagonistName
                    }
                    if(actTemplates[act][r][i].includes("antagonistPronoun")){
                        words = antagonistPronoun
                    }
                    if(actTemplates[act][r][i].includes("antagonistPronounOwn")){
                        words = antagonistPronounOwn
                    }
                    moviePlot += words
                }

                var formattedPlot = ""

                // Format the "a" and "an" words
                for(i = 0; i < moviePlot.length; i++) {
                    if(moviePlot[i] == "a" & moviePlot[i-1] == " " & moviePlot[i+1] == " ") {
                        if(moviePlot[i+2] == "a" || moviePlot[i+2] == "e" || moviePlot[i+2] == "i" || moviePlot[i+2] == "o"){
                            formattedPlot += "an "
                            i += 1
                        }
                        else {
                            formattedPlot += moviePlot[i]
                        }
                    }
                    else {
                        formattedPlot += moviePlot[i]
                    }
                }
                switch(act) {
                    case 0:
                        this.act1 = formattedPlot
                        break;
                    case 1:
                        this.act2 = formattedPlot
                        break;
                    case 2:
                        this.act3 = formattedPlot
                        break;
                }

                act += 1
            }
        }
    }     
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
