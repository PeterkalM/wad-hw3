<template>
    <div id="profile-container">
        <div id="profile">
            <div class="avatar">
                <img src="../assets/me.png" id="picture" alt="My picture" />
            </div>
            <div class="info">
                <ul>
                    <li id="name">{{this.user.firstname}} {{this.user.lastname}}</li>
                    <li id="birthdate">{{this.user.birthdate}}</li>
                    <li id="faculty">{{this.user.faculty}}</li>
                </ul>
            </div>
            <div id="gpa">
                <strong>{{this.user.gpa}}</strong>
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
};
</script>

<style scoped>
#profile {
    border-bottom: 1px dashed #a7a7a7;
    padding-bottom: 10px;
    margin-bottom: 10px;
}
#profile .avatar {
    width: 35%;
    text-align: center;
}
#profile .info {
    width: 45%;
}

#profile #gpa {
    width: 20%;
}
#profile div:not(.clear-fix) {
    height: 190px;
    float: left;
    position: relative;
}

#profile .avatar img {
    width: 180px;
}

#profile #gpa strong {
    position: absolute;
    width: 100%;
    height: 60px;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto auto;
    font-size: 60px;
    line-height: 60px;
    text-align: center;
}
.clear-fix {
    clear: both;
}
</style>