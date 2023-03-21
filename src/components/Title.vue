<template>
    <div>
        <span class="d-flex" :class="isMobile ? 'mobile' : ''">
            <h1 @mouseover="rubberBand(i)" :id="$parent._uid + 'letter-' + i" class="title"
                :class="letter === ' ' ? 'mx-1' : ''" v-for="letter, i in title" :key="i">
                {{ letter }}
            </h1>
        </span>
    </div>
</template>


<script>
export default {
    name: 'Title',
    props: {
        title: String,
    },
    methods: {
        rubberBand(i) {
            let letter = document.getElementById(`${this.$parent._uid}letter-${i}`);
            if (!letter.classList.contains('animate')) {
                letter.classList.add('animate');
                setTimeout(() => {
                    letter.classList.remove('animate');
                }, 1000)
            }
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
.mobile {
    .title {
        font-size: 48px;
    }
}

.title {
    font-size: 5rem;
    color: #07bcac;
    margin-bottom: 0;
}

.animate {
    animation-name: rubberBand;
    animation-duration: 1s;
    animation-fill-mode: both;
}

@keyframes rubberBand {
    0% {
        transform: scale3d(1, 1, 1);
    }

    30% {
        transform: scale3d(1.25, 0.75, 1);
    }

    40% {
        transform: scale3d(0.75, 1.25, 1);
    }

    50% {
        transform: scale3d(1.15, 0.85, 1);
    }

    65% {
        transform: scale3d(0.95, 1.05, 1);
    }

    75% {
        transform: scale3d(1.05, 0.95, 1);
    }

    100% {
        transform: scale3d(1, 1, 1);
    }
}
</style>