<template>
    <div class="container">
        <div class="row align-items-center mx-1" style="height: 100vh">
            <div class="col-12 col-sm-6 text-bg-dark text-bg">
                <Title title="Skills" />
                <p class="mt-3">
                    I have skills like HTML, CSS, SCSS, Javascript, Bootstrap, Vue.js, Vuex, Vuetify, Firebase, REST API
                </p>
            </div>
        </div>
    </div>
</template>

<script>
import Title from './Title';

export default {
    name: 'Skills',
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
    font-size: 1.5rem;
}
</style>