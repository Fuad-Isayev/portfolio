<template>
    <div class="container">
        <transition name="fade">
            <div class="row align-items-center mx-1" style="height: 100vh">
                <div class="col-12 col-sm-6 text-bg-dark text-bg">
                    <Title title="About me" />
                    <p class="mt-3">
                        I'm a self-taught frontend engineer with a
                        passion for building beautiful and
                        functional
                        web
                        applications. I've worked on an e-commerce project where I utilized technologies such as HTML, CSS,
                        JavaScript,
                        Vue.js, Vuetify, Vuex, Vue Route, Firebase, REST API and others to create a responsive and
                        user-friendly
                        web
                        application.

                    <p class="mt-3 pt-2 ">
                        As a self-learner, I'm always eager to expand my knowledge and skills in the field of web
                        development. I
                        have a
                        strong work ethic and a commitment to delivering high-quality work on time and on budget.
                    </p>

                    <p class="mt-3 pt-2 ">
                        I believe that my ability to learn quickly and adapt to new technologies, combined with my passion
                        for
                        web
                        development, make me an asset to any development project. I'm excited to continue growing my skills
                        and
                        experience as a frontend engineer and would love to hear about any opportunities that may be a good
                        fit
                        for
                        my
                        background and goals. Thank you for taking the time to visit my portfolio site!
                    </p>
                    </p>
                </div>
            </div>
        </transition>
    </div>
</template>

<script>
import Title from "./Title";

export default {
    name: 'About',
    components: {
        Title,
    },
    computed: {
        isMobile() {
            return this.$store.getters.isMobile;
        }
    }
}
</script>

<style scoped>
p {
    font-size: 1.3rem;
}

.title {
    font-size: 5rem;
    color: #07bcac;
}

.fade-appear-active,
.fade-enter-active {
    transition: opacity 0.5s;
}

.fade-enter {
    opacity: 0;
}

.fade-leave-to {
    opacity: 0;
}
</style>