<template>
    <div id="profile-container" class="tab active">
        <div id="profile">
            <div class="avatar">
                <img src="../../src/assets/me.png" id="picture" alt="My picture">
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{this.user.firstname}} {{this.user.lastname}}</li>
                    <li id="birthdate">{{this.user.birthdate}}</li>
                    <li id="faculty">{{this.user.faculty}}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>2.75</strong>
            </div>
            <div class="clear-fix"></div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Profile",
        props: {
            user: Object
        }
    }
</script>

<style scoped>

</style>