<template>
    <main id="app">
        <header>
            <strong>Welcome to your dashboard!</strong>
        </header>
        <section id="container">
            <section id="main">
                <div class="content">
                    <Profile v-if="selectedProfile" :user="user"/>
                    <Courses v-else :courses="courses" :add-course="addCourse"/>
                </div>
                <div class="controls">
                    <button id="profile-button" :class="{'pill active' : selectedProfile, 'pill' : !selectedProfile}"
                            @click="selectedProfile = true">Profile
                    </button>
                    <button id="courses-button" :class="{'pill' : selectedProfile, 'pill active' : !selectedProfile}"
                            @click="selectedProfile = false">Courses
                    </button>
                </div>
            </section>
        </section>
      <footer> <!--  Maybe this should be made into another vue component, as we need 4 in total-->
            <ul class="links">
                <li>
                    <a href="https://ois2.ut.ee/" target="_blank">OIS</a>
                </li>
                <li>
                    <a href="https://courses.cs.ut.ee/" target="_blank">Courses</a>
                </li>
            </ul>
        </footer>
    </main>
</template>

<script>
    import Courses from "./components/Courses";
    import Profile from "./components/Profile";
    import Course from "./models/Course";
    import User from "./models/User";

    export default {
        name: 'app',
        data: () => {
            return {
                selectedProfile: true, //Used for changing styling between controller buttons
                user: new User("John", "Doe", "11/10/1990", "Software Engineering"),
                courses: [new Course("Agile software development", 1, 82),
                    new Course("System modeling", 1, 85),
                    new Course("Object-oriented programming", 2, 99),
                    new Course("Estonian language level A2", 2, 65)]
            }
        },
        methods:{
            addCourse: function(courseName,semester,grade){ //Used so that Courses.vue doesn't need to import Course.js
                this.courses.push(new Course(courseName,semester,grade));
            }
        },
        components: {Courses, Profile}
    }
</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }

    .clear-fix {
        clear: both;
    }

    header {
        padding: 20px;
        background-color: #2196F3;
        color: #ffffff;
        text-align: center;
        margin-bottom: 10px;
        height: 60px;
    }

    footer {
        padding: 30px 0;
        background-color: #607D8B;
        margin-top: 10px;
        height: 100px;
        position: absolute;
        bottom: 0;
        width: 100%;
    }

    footer .links {
        display: block;
        width: 100%;
        max-width: 200px;
        margin: 0 auto;
        color: #acd7ff;
        font-size: 11px;
    }

    footer .links a {
        text-decoration: none;
        color: #acd7ff;
    }

    footer .links a:hover {
        text-decoration: underline;
    }

    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }


    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
    }

    .controls .pill {
        border: 1px solid #cbcbcb;
        background-color: #eaeaea;
        padding: 10px;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: none;
        margin-top: -1px;
        outline: none !important;
    }

    .controls .pill.active {
        background-color: #ffffff;
        border-top: 1px solid #ffffff;
    }

    .controls .pill:hover {
        cursor: pointer;
    }




</style>
