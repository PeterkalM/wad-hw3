<template>
    <div id="courses-container">
        <h1 class="title">Courses</h1>
        <table id="courses">
            <thead>
                <tr>
                    <th>#</th>
                    <th>Course Title</th>
                    <th>Semester</th>
                    <th>Grade</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(course, index) in courses" :key="index">
                    <td>{{index + 1}}</td>
                    <td>{{course.title}}</td>
                    <td>{{course.semester}}</td>
                    <td>{{course.grade}}</td>
                </tr>
            </tbody>
        </table>
        <br />
        <br />
        <div>
            <button id="add-course-button" class="blue-button" @click="addingCourse=!addingCourse">+</button>
            <span v-if="addingCourse" id="add-course">
                <input
                    class="input"
                    v-model="title"
                    type="text"
                    placeholder="Course title"
                    id="title"
                />
                <input
                    class="input"
                    v-model="semester"
                    type="number"
                    min="1"
                    max="8"
                    placeholder="Semester"
                    id="semester"
                />
                <input
                    class="input"
                    v-model="grade"
                    type="number"
                    min="0"
                    max="100"
                    placeholder="Grade"
                    id="grade"
                />
                <button
                    class="green-button"
                    id="save-course"
                    @click="addCourse(title, semester, grade) ? resetCourseForm() : null"
                >Save</button>
                <button class="grey-button" id="cancel-course" @click="resetCourseForm()">Cancel</button>
            </span>
        </div>
    </div>
</template>

<script>
export default {
    name: "Courses",
    data: () => {
        return {
            title: "",
            semester: "",
            grade: "",
            addingCourse: false //If this is false, then we are currently not adding a course
        };
    },
    methods: {
        resetCourseForm: function() {
            this.title = "";
            this.semester = "";
            this.grade = "";
            this.addingCourse = false;
        }
    },
    props: {
        courses: Array,
        addCourse: Function
    }
};
</script>

<style scoped>
table {
    width: 100%;
    border-collapse: collapse;
}

table th {
    padding: 8px 12px;
    text-align: left;
    border: 1px solid #cbcbcb;
    background-color: #03a9f4;
    color: #ffffff;
}

table td {
    padding: 8px 12px;
    border: 1px solid #cbcbcb;
}

.blue-button {
    background-color: #2196f3;
    color: #ffffff;
    border: none;
    padding: 10px 20px;
}

.green-button {
    background-color: #69f378;
    color: #ffffff;
    border: none;
    padding: 10px 10px;
}

.grey-button {
    background-color: #e1e8e6;
    color: #ffffff;
    border: none;
    padding: 10px 20px;
}

.input {
    border: 1px solid #cccccc;
    padding: 10px 20px;
    min-width: 135px;
}
</style>