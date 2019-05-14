<template>
    <div>
        <h3>Personal Information</h3>
        <hr>
        <div class="row">
            <div class="col-sm-3">
                <div class="row">
                    <label>Firstname:</label>
                    Jarek
                </div>

                <div class="row">
                    <label>Surname:</label>
                    Jannait
                </div>

                <div class="row">
                    <label>Birthdate:</label>
                    14. aug 1998
                </div>
                <div class="row">
                    <label>City:</label>
                    Tallinn
                </div>
                <div class="row">
                    <label>Telephone:</label>
                    +37253339358
                </div>
                <div class="row">
                    <label>E-mail:</label>
                    jarekx.j@gmail.com
                </div>
                <div class="row">
                    <label>LinkedIn: </label>
                    <a href="https://www.linkedin.com/in/jarek-jannait-773668163">https://www.linkedin.com/in/jarek-jannait-773668163/</a>
                </div>
            </div>
            <div class="col-sm-3">
                <pieChart :chartdata="chartData"></pieChart>
            </div>
        </div>
        <h3>Work Experience</h3>
        <hr>
        <div>
            <div class="row">
                <span class="lighter">07.2018</span> Data Handler @MYJar (Non-IT job)
            </div>
        </div>
        <h3>Education</h3>
        <hr>
        <div>
            <div class="row">
                <span class="lighter">2017 - ... </span>Tallinn University Of Technology, Bacherlor, Informatics
            </div>
            <div class="row">
                <span class="lighter">2005 - 2017 </span>Vändra Gymnasium, Secondary Education
            </div>
        </div>
        <h3>Computer Skills</h3>
        <hr>
        <div>
            <table>
                <th>Program/Language</th>
                <th>level</th>
                <tr v-for="skill in skills" v-bind:key="skill.id" v-bind:class="{greyBackground: skill.id%2===0}">
                    <td>{{skill.name}}</td>
                    <td>{{skill.level}}</td>
                </tr>
            </table>
        </div>
    </div>
</template>

<script>
    import pieChart from "../components/PieChart.vue"
    import chdata from "../assets/data.json"

    export default {
        name: "cv",
        components: {
            pieChart
        },
        data() {
            return {
                skills: [
                    {id: 1, name: 'Java', level: 'Intermediate'},
                    {id: 2, name: 'Python', level: 'Average'},
                    {id: 3, name: 'Javascript', level: 'Average'},
                    {id: 4, name: 'HTML', level: 'Average'},
                    {id: 5, name: 'SQL', level: 'Average'},
                    {id: 6, name: 'MS Excel', level: 'Average'},
                    {id: 7, name: 'MS Word', level: 'Average'},
                ],
                chartData: chdata
            }
        }
    }
</script>

<style scoped>
    .row {
        padding-bottom: 10px;
    }

    hr {
        color: rgba(230, 230, 230, 0.8);
    }

    label {
        font-weight: bold;
    }

    div {
        margin-left: 10px;
    }

    .lighter {
        color: darkgrey;
    }

    .greyBackground {
        background: lightgray;
    }

    table {
        height: 50%;
        width: 50%;
        padding-bottom: 50px;
    }

    tr {
        height: 30px;
    }
</style>