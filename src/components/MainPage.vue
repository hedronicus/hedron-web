<template>
  <div
    class="main">
    <three-cubes
      class="
    three" />
    <span id="fade">
      <landing-page
        v-if="page=='hedron'"
        class="body" 
        :class="{show:handleShowMain()}" />
      <membership-page
        v-if="page=='membership'"
        class="body"
        :class="{show:handleShowMain()}" />
      <gallery-page
        v-if="page=='gallery'"
        class="body"
        :class="{show:handleShowMain()}" />
    </span>
  </div>
</template>

<script>
  import { mapActions, mapGetters } from "vuex"
  import ThreeCubes from "./ThreeCubes"
  import LandingPage from "./LandingPage"
  import MembershipPage from "./MembershipPage"
  import GalleryPage from "./GalleryPage"

  export default {
    name: "HomePage",
    components: {
      ThreeCubes,
      LandingPage,
      MembershipPage,
      GalleryPage
    },
    computed: {
      ...mapGetters(["page","showMain"])
    },
    methods: {
      ...mapActions([]),
      handleShowMain () {
        return this.showMain ? true : false
      }
    }
  }
</script>

<style scoped>
.main {
  max-height: 100%;
  max-width: 100%;
  overflow: hidden;

  transition: height ease-in .8s 1s, width ease-in .8s;
}

.three {
  position: absolute;
  height: 100%;
  width: 100%;
  top: 0;
  left: 0;
  border-left: #1b1c1d solid 1px;
}

.body {
  position: absolute;
  height: 87%;
  width: 80%;
  max-width: 800px;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-53%);
  padding: 6rem 8rem;
  background: #0b0c0d80;
  border: solid 1px #00ffff99;
  border-radius: 6px;

  overflow-y: auto;
  overflow-x: hidden;

  opacity: 0;
  
}

.body.show {
  transition: opacity ease 2.5s 4.5s;
  opacity: 1;
}




@media only screen and (max-width: 1000px) {
}

@media only screen and (max-width: 800px) {

  .body {
    padding: 2rem;
    height: calc(100% - 8rem - 4px);
    width: calc(100% - 2rem);
    top: 1rem;
    transform: translate(-50%,0);
    border-radius: 0;
  }

  .menu__row {
    color: red;
  }

  .menu {
    width: 100vw;
  }
}
</style>
