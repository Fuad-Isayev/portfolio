<template>
    <div class="container justify-content-center d-flex flex-column" style="height: 100vh">
        <div class="row mx-1 align-items-center mb-5">
            <div class="col-12 col-sm-6 text-bg-dark text-bg" style="width: auto;">
                <Title title="My projects" />
            </div>
        </div>
        <div class="row mx-2 text-bg-dark bg-transparent " style="width: fit-content">
            <div class="col-6 col-sm-4 justify-content-center px-3 py-2">
                <div class="row align-items-center" style="height: fit-content">
                    <div class="card project-card px-0">
                        <h5 class=" text-center text-black card-title">E-commerce</h5>
                        <img class="card-img" src="/assets/projects/Untitled.png" alt="https://my-e-commerce.vercel.app"
                            width="100%">
                        <div class="card-button-wrapper">
                            <a href="https://my-e-commerce.vercel.app" class="btn card-button" target="_blank">
                                View Project
                            </a>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Title from './Title';

export default {
    name: 'Project',
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

<style lang="scss">
.project-card {
    transition: all 0.5s;
    user-select: none;

    &:hover {
        transform: scale(1.05) !important;
        transition: all 0.5s;
        z-index: 100;

        .card-button {
            transform: scale(1);
            transition: all 0.2s;
            color: #fff;

            &:hover {
                background-color: #072c2c;
            }
        }

        .card-button-wrapper {
            background: none;
        }
    }
}

.card-button-wrapper {
    width: 100%;
    height: 100%;
    display: flex;
    position: absolute;
    justify-content: center;
    align-items: center;
    text-align: center;
    background: rgba(0, 0, 0, 0.2);
    border-radius: calc(0.375rem - 1px);
    border-bottom-right-radius: 0;
}

.card-button {
    width: 75px;
    height: 75px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: cursive;
    transform: scale(0);
    border-radius: 50%;
    transition: all 0.2s;
    background-color: #07bcac;
}

.card-text {
    font-family: cursive !important;
}
</style>