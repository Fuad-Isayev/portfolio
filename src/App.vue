<template>
  <div class="bg-dark bg-image align-items-center">
    <div id="home" ref="home">
      <Homes :active="active" />
    </div>
    <div id="about" ref="about">
      <About />
    </div>
    <div id="skills" ref="skills">
      <Skills />
    </div>
    <div id="projects" ref="projects">
      <Projects />
    </div>
    <div id="contact" ref="contact">
      <Contact />
    </div>
  </div>
</template>

<script>
import Homes from "./components/Home"
import About from "./components/About"
import Skills from "./components/Skills"
import Contact from "./components/Contact"
import Projects from "./components/Projects"

export default {
  name: 'App',
  data() {
    return {
      active: true,
    }
  },
  components: {
    Homes,
    About,
    Skills,
    Contact,
    Projects
  },
  mounted() {
    window.onresize = this.getDimensions;

    const observer = new IntersectionObserver(
      (entries, observer) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('transition');
            if (entry.target.id === 'home') {
              this.active = true;
            }
          } else {
            entry.target.classList.remove('transition');
            if (entry.target.id === 'home') {
              this.active = false;
            }
          }
        });
      },
      {
        root: null,
        rootMargin: '0px',
        threshold: 0.1 // when 50% of the component is visible
      }
    );
    observer.observe(this.$refs.home)
    observer.observe(this.$refs.about)
    observer.observe(this.$refs.skills)
    observer.observe(this.$refs.contact)
    observer.observe(this.$refs.projects)
  },
  methods: {
    getDimensions() {
      this.$store.state.screenWidth = window.innerWidth;
    }
  }
}
</script>

<style>
.transition {
  /* opacity: 100% !important;
  padding: 0 !important;
  margin: 0 !important; */
  /* transition: all 2s; */
  animation-name: fadeslide;
  animation-duration: 1s;
  animation-timing-function: linear;
}

.bg-image {
  background-image: url('./assets/background-portfolio.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
}

@keyframes fadeslide {
  0% {
    /* transform: translateX(-300px); */
    opacity: 0.1;
  }

  100% {
    opacity: 1;
  }
}
</style>
