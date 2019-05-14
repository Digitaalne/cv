<template>
    <div>
        <div style="text-align: center">
            <vue-p5 v-on="{preload, setup, draw}"></vue-p5>
        </div>
        <h3>Personal Information</h3>
        <hr>
        <div class="row">
            <div class="col-md-3">
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
            <!-- Reference: Remember the Name - Fort Minor -->
            <div class="col-md-4" style="text-align: center">
                <h3>This CV Consist Of: </h3>
                <pieChart :chartdata="chartData"></pieChart>
            </div>
            <div class="col-md-4 justify-content-center" style="text-align: center">
                <h3>You Have:</h3>
                <pieChart :chartdata="nameChart"></pieChart>
            </div>
        </div>
        <h3>Work Experience</h3>
        <hr>
        <div>
            <div class="row">
                <span class="lighter">07.2018 </span>Data Handler @MYJar (Non-IT job)
            </div>
        </div>
        <h3>Education</h3>
        <hr>
        <div>
            <div class="row">
                <span class="lighter">2017 - ... </span> Tallinn University Of Technology, Bacherlor, Informatics
            </div>
            <div class="row">
                <span class="lighter">2005 - 2017 </span> Vändra Gymnasium, Secondary Education
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
        <div class="footer"></div>
    </div>
</template>

<script>
    import pieChart from "../components/PieChart.vue"
    import chdata from "../assets/data.json"
    import name from "../assets/name.json"
    import VueP5 from 'vue-p5';


    export default {
        name: "cv",
        methods: {
            preload(sk) {
                this.img = sk.loadImage('cv.png');
            },
            setup(sk) {
                sk.createCanvas(this.img.width, this.img.height);
                sk.imageMode(sk.CENTER);
                sk.noStroke();
                this.img.loadPixels();
            },
            draw(sk) {

                this.y++;
                let randx = sk.floor(sk.random(this.img.width));
                let randy = sk.floor(sk.random(this.img.height));
                let pix2 = this.img.get(randx, randy);
                sk.fill(pix2, 128);
                sk.ellipse(randx, randy, 15, 15);
            }
        },
        render(h) {
            return h(VueP5, {on: this});
        },
        components: {
            pieChart, VueP5
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
                chartData: chdata,
                nameChart: name,
                img: '',
                x: 0,
                y: 0
            }
        },
    }
</script>

<style scoped>
    .row {
        padding-bottom: 10px;
        text-shadow: 1px 1px lightgray;
    }

    hr {
        color: rgba(230, 230, 230, 0.8);
    }

    label {
        font-weight: bold;
        margin-right: 6px;
    }

    div {
        margin-left: 10px;
        font-size: 18px;
    }

    .lighter {
        color: white;
        text-shadow: 1px 1px black;
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

    span {
        margin-right: 10px;
    }

    .footer {
        padding-bottom: 60px;
    }
</style>