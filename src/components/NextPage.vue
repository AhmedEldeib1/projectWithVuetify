<template>
<v-container class="text-center">
    <h1>We are here for the expansion panel</h1>

    <v-expansion-panels>
        <v-expansion-panel v-for="project in myProject" :key="project.person">
            <v-expansion-panel-header>
                {{project.title}}
            </v-expansion-panel-header>
            <v-expansion-panel-content>
                <h2>Due to</h2>
                <h4>{{project.due}}</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ipsum cum qui quae ex iste possimus facilis delectus atque ratione iure, repellat dolorum voluptates doloremque asperiores corrupti modi sit veritatis numquam.</p>
            </v-expansion-panel-content>
        </v-expansion-panel>
    </v-expansion-panels>

</v-container>
</template>

<script>
export default {
    name: "NextPage",
    data() {
        return {
            projects: [{
                    title: 'Design a new website',
                    person: 'The Net Ninja',
                    due: '1st Jan 2019',
                    status: 'ongoing',
                    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
                },
                {
                    title: 'Code up the homepage',
                    person: 'Chun Li',
                    due: '10th Jan 2019',
                    status: 'complete',
                    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
                },
                {
                    title: 'Design video thumbnails',
                    person: 'Ryu',
                    due: '20th Dec 2018',
                    status: 'complete',
                    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
                },
                {
                    title: 'Create a community forum',
                    person: 'Gouken',
                    due: '20th Oct 2018',
                    status: 'overdue',
                    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
                },
                {
                    title: 'Design a new website ... again',
                    person: 'The Net Ninja',
                    due: '1st Jan 2019',
                    status: 'ongoing',
                    content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'
                }
            ]
        }
    },
    computed:{
        myProject(){
            return this.projects.filter(v=>v.person=="The Net Ninja");
        }
    }
}
</script>
