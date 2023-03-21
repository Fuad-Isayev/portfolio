<template>
    <div class="container text-bg-dark text-center bg-transparent" style="height: 100vh">
        <div class="row align-items-center">
            <div class="col-2">
                <h1 v-if="isMobile" class="hamburger" @click="isMenuOpen = !isMenuOpen">
                    <font-awesome-icon :icon="isMenuOpen ? ['fas', 'times'] : ['fas', 'bars']" :style="{ color: '#bff' }" />
                </h1>
                <div v-if="isMenuOpen" class="menu">
                    <ul>

                        <li @click="goToLink('home')" class="list-button">Home</li>
                        <li @click="goToLink('about')" class="list-button">About</li>
                        <li @click="goToLink('skills')" class="list-button">Skills</li>
                        <li @click="goToLink('projects')" class="list-button">Projects</li>
                        <li @click="goToLink('contact')" class="list-button">Contacts</li>
                    </ul>
                </div>
            </div>
            <div v-if="!isMobile" class="col-3">
                <div class="row">
                    <div :class="active ? '' : 'fixed-top about'" class="col">
                        <div @click="goToLink('about')" class="d-flex align-items-center justify-content-center nav-button">
                            <h5>About</h5>
                        </div>
                    </div>
                    <div :class="active ? '' : 'fixed-top skills'" @click="goToLink('skills')" class="col">
                        <div class="d-flex align-items-center justify-content-center nav-button">
                            <h5>Skills</h5>
                        </div>
                    </div>
                </div>
            </div>
            <div :class="isMobile ? 'col-12 text-start' : active ? 'text-center' : 'fixed-top logo text-start'"
                class="col-2 py-3 ms-n5">
                <img @click="goToLink('home')" class="logo-button" src="../assets/logo1.png" style="width: 100px" alt="">
            </div>
            <div v-if="!isMobile" class="col-3">
                <div class="row h5">
                    <div :class="active ? '' : 'fixed-top projects'" class="col">
                        <div @click="goToLink('projects')"
                            class="d-flex align-items-center justify-content-center nav-button">
                            <h5>Projects</h5>
                        </div>
                    </div>
                    <div :class="active ? '' : 'fixed-top contact'" class="col">
                        <div @click="goToLink('contact')"
                            class="d-flex align-items-center justify-content-center nav-button contact">
                            <h5>Contacts</h5>
                        </div>
                    </div>
                </div>
            </div>
            <div v-if="!isMobile" class="col-2"></div>
        </div>
        <div class="row align-items-center content mx-1">
            <div ref="text" class="col-6 transition text-bg" style="width: auto">
                <p class="h1 text-start d-flex align-items-end">
                    Hi! I'm
                    <Title :class="isMobile ? 'mobile name' : 'name'" title=" Fuad Isayev" />.
                </p>
                <p class="h1 text-start">
                    I'm a Frontend Developer.
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import Title from './Title';

export default {
    name: "Homes",
    data() {
        return {
            isMenuOpen: false
        }
    },
    components: {
        Title,
    },
    props: {
        active: Boolean,
    },
    methods: {
        goToLink(link) {
            window.location.href = '#' + link
        }
    },
    computed: {
        isMobile() {
            return this.$store.getters.isMobile;
        }
    }
}
</script>

<style lang="scss">
.text-bg {
    background-color: rgba(0, 0, 0, 0.5) !important;
    border-radius: 10%;
}

h5 {
    margin-bottom: 0;
}

.logo-button {
    cursor: pointer;
}

.nav-button {
    cursor: pointer;
    width: 120px;
    height: 48px;
    background: rgba(255, 255, 255, 0.16);
    border: 5px solid rgb(255, 255, 255);
    border-radius: 40%;
    clip-path: polygon(19% 0%, 81% 0, 100% 19%, 100% 81%, 81% 100%, 19% 100%, 0 81%, 0 19%);

    &.contact,
    &:hover {
        background: rgba(7, 110, 110, 0.16);
        border: 5px solid rgb(7, 168, 152);
    }
}

.content {
    height: calc(100vh - 150px)
}

.fixed-top {
    animation-fill-mode: forwards;
    width: fit-content;
}

.logo {
    animation-name: slide-logo;
    animation-duration: 0.5s;
}

.about,
.skills,
.projects,
.contact {
    animation-name: slide-buttons;
    animation-timing-function: ease-in;
}

.about {
    top: 150px;
    animation-duration: 0.5s;
}

.skills {
    top: 220px;
    animation-duration: 0.7s;
}

.projects {
    top: 290px;
    animation-duration: 0.9s;

}

.contact {
    top: 360px;
    animation-duration: 1.1s;
}

.name {
    display: flex;
    width: auto;
    align-items: end;

    h1 {
        font-size: 40px;
    }

    &.mobile {
        h1 {
            font-size: 34px;
        }
    }
}

.hamburger {
    cursor: pointer;
    position: fixed;
    right: 20px;
    top: 20px;
    background: #000;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 50px;
    height: 50px;
    z-index: 100;
}

.menu {
    position: fixed;
    top: 0;
    right: 0;
    z-index: 90;
    width: 50vw;
    background: #000;
    text-align: center;
    padding-right: 20px;
    padding-top: 70px;

    li {
        list-style-type: none;
    }
}

.list-button {
    font-family: italic;
    font-weight: 800;
    font-size: 22px;
    margin-bottom: 8px;

    &:hover {
        color: #07bcac;
    }
}

@keyframes slide-logo {
    0% {
        left: -40px;
        padding-left: 0;
    }

    100% {
        padding-left: 24px;
    }
}

@keyframes slide-buttons {
    0% {
        left: -68px;
    }

    100% {
        left: 3.5px;
    }
}
</style>