<template>
  <div class="h-screen flex flex-col">
    <Nav @notify="updateSection" />
    <div class ="relative flex-grow">
      <Certifications class="main-section" :style="{ opacity: (section == 'Certifications') * 1 }"  />
      <Projects class="main-section" :style="{ opacity: (section == 'Projects') * 1 }" />
    </div>
  </div>

</template>

<script>
import Nav from './components/Nav.vue'
import Certifications from './components/Certifications.vue'
import Projects from './components/Projects.vue'

export default {
  name: 'App',
  data(){
    return {
      section: "Projects"
    }
  },
  components: {
    Nav,
    Certifications,
    Projects
  },
  methods: {
    updateSection(newSection){
      this.section = newSection
      console.log("App " + newSection)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
.main-section{
  transition: opacity 0.5s ease-in-out ;
  position: absolute;
  width: 100%;
  height: fit-content;
  background-color: aquamarine;
}
</style>
