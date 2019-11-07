<template>
    <main id="app">
        <Header />
        <section id="container">
            <section id="main">
                <div class="content">
                    <Profile v-if="selectedProfile" :user="user" />
                    <Courses v-else :addCourse="addCourse" :courses="courses" />
                </div>
                <div class="controls">
                    <button
                        id="profile-button"
                        :class="{'pill active' : selectedProfile, 'pill' : !selectedProfile}"
                        @click="selectedProfile = true"
                    >Profile</button>
                    <button
                        id="courses-button"
                        :class="{'pill' : selectedProfile, 'pill active' : !selectedProfile}"
                        @click="selectedProfile = false"
                    >Courses</button>
                </div>
            </section>
        </section>
        <Footer />
    </main>
</template>

<script>
import Header from "./components/Header";
import Courses from "./components/Courses";
import Profile from "./components/Profile";
import Footer from "./components/Footer";
import Course from "./models/Course";
import User from "./models/User";

export default {
    name: "app",
    data: () => {
        return {
            selectedProfile: true, //Used for changing styling between controller buttons
            user: new User("John", "Doe", "11/10/1990", "Software Engineering"),
            courses: [
                new Course("Agile software development", 1, 82),
                new Course("System modeling", 1, 85),
                new Course("Object-oriented programming", 2, 99),
                new Course("Estonian language level A2", 2, 65)
            ]
        };
    },
    created: function() {
        this.user.gpa = this.calculateGPA();
    },
    methods: {
        addCourse: function(courseName, semester, grade) {
            if (
                courseName != "" &&
                semester != "" &&
                grade != "" &&
                semester >= 1 &&
                grade >= 0 &&
                grade <= 100 &&
                semester <= 8
            ) {
                this.courses.push(new Course(courseName, semester, grade));
                this.user.gpa = this.calculateGPA();
                return true;
            }
            return false;
        },
        calculateGPA: function() {
            //TODO: GPA calculation
            //return Math.round(..*100)/100;
            return 0;
        }
    },
    components: {
        Header,
        Courses,
        Profile,
        Footer
    }
};
</script>

<style>
* {
    box-sizing: border-box;
    font-family: "Livvic", sans-serif;
}

html,
body {
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
