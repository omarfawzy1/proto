<template>
  <nav class="h-30 bg-[#393939]  text-2xl flex flex-row px-5  text-white">
    <div class="py-5">
      Omar Fawzy
    </div>
    <section id="menu" class=" flex gap-10 text-lg [&>p]:cursor-pointer [&>p]:py-5 ml-10 relative bg-slate-700 self-center">
      <p @mouseover="oversomething" @mouseleave="leavesomething" @click="changeSection" > Projects </p>
      <p @mouseover="oversomething" @mouseleave="leavesomething" @click="changeSection"> Experiance </p>
      <p @mouseover="oversomething" @mouseleave="leavesomething" @click="changeSection" > Certifications </p> 
      <div class="absolute bottom-[-4px] bg-red-600 dash" 
      :style="{ width: width + 'px', height: height + 'px', left: left + 'px' }"></div>
    </section>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  props: {
    msg: String
  },
  data(){
    return {
      width: 0,
      height: 5,
      left: 0,
      oldwidth: 0,
      oldleft: 0,
      currentSection: "Projects"
    }
  },
  methods: {
    oversomething(event){
      const section = document.getElementById('menu').getBoundingClientRect();
      const rect = event.target.getBoundingClientRect();
      this.oldwidth = this.width;
      this.oldleft = this.left;
      this.width = rect.width;
      this.left = rect.x - section.x;
    },
    leavesomething(event) {
      event
      this.width = this.oldwidth;
      this.left = this.oldleft;
      //const rect = event.target.getBoundingClientRect();
    },
    changeSection(event){
      this.currentSection = event.target.innerText;
      this.$emit("notify", this.currentSection)
      const rect = event.target.getBoundingClientRect();
      const section = document.getElementById('menu').getBoundingClientRect();
      this.width = rect.width;
      this.left = rect.x - section.x;
      this.oldwidth = this.width;
      this.oldleft = this.left;
    }
  }
}
</script>

<style scoped>
  .dash{
    transition: width 0.5s ease-in-out, height 0.5s ease-in-out, left  0.5s ease-in-out;
  }
</style>
