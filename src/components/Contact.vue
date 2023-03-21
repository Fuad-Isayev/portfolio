<template>
    <div class="container text-bg-dark bg-transparent">
        <div class="row align-items-center mx-1" style="height: 100vh">
            <div class="col-12 col-sm-6 text-bg" style="height: auto">
                <Title title="Contact me" />
                <form class="mt-4">
                    <div class="row">
                        <div class="col-12 gap-2 d-flex align-items-center justify-content-center flex-column">
                            <div class="row first">
                                <div class="col-6 ps-0">
                                    <input v-model="name" type="text" name="Name" placeholder="Name" id="name">
                                </div>
                                <div class="col-6 pe-0">
                                    <input type="email" name="Email" placeholder="Email" id="email">
                                </div>
                            </div>
                            <input v-model="subject" type="text" name="Subject" placeholder="Subject" id="subject">
                            <textarea v-model="message" type="text" name="Message" placeholder="Message"
                                id="text"></textarea>
                            <a class="send-mail-button my-3"
                                :href="'mailto:fuad.isayev.1995@gmail.com?subject=' + subject + '&body=' + message + '%0D%0A %0D%0A - from ' + name">
                                Send Message
                            </a>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
import Title from './Title';

export default {
    name: "Contact",
    data() {
        return {
            subject: '',
            message: '',
            name: '',
        }
    },
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
p {
    font-size: 1.5rem;
}

.title {
    font-size: 5rem;
    color: #07bcac;
}

.row {
    &.first {
        width: inherit;
    }
}

input {
    width: 100%;
    border: 0;
    background: #2b2b2be5;
    height: 50px;
    font-size: 16px;
    color: #8d8d8d;
    padding: 0 20px;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    margin-left: auto;
}

.send-mail-button {
    color: #07bcac;
    background-color: #2b2b2be5;
    border: 1px solid #07bcac;
    border-radius: 10px;
    padding: 1.0rem 1.5rem;
    font-size: 18px;
    font-family: sans-serif;
    line-height: 1;
    text-decoration: none;
    cursor: pointer;

    &:hover {
        background-color: #07bcac;
        color: black;
    }
}

textarea {
    width: 100%;
    border: 0;
    background: #2b2b2b;
    height: 50px;
    font-size: 16px;
    color: #8d8d8d;
    padding: 20px;
    -webkit-box-sizing: border-box;
    box-sizing: border-box;
    min-height: 150px;
}
</style>