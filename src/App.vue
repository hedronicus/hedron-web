<template>
  <div
    id="app">
    <div
      id="body"
      :key="componentKey">
      <router-view />
    </div>
    <div
      id="fade" />
  </div>
</template>

<script>
  export default {
    name: "App",
    components: {
    },
    data () {
      return { componentKey: 0 }
    },
    created () {
      setTimeout(this.scrollToTop, 1000)
      if ( !this.isMobile ) {
        this.preLoadImages()
      }
    },
    methods: {
      scrollToTop () {
        window.scrollTo(0,0)
      },
      handleNavigation () {
        this.componentKey += 1
      }
    }
  }
</script>

<style scoped>

#appBlock {
  opacity: 0;
  animation: fadeIn .5s ease-out 1s forwards;
  background: #0b0c0d; 
}

#app {
  opacity: 0;
  animation: fadeIn .5s ease-out .5s forwards;
  background: #0b0c0d;
}

@keyframes fadeIn {
  from {opacity: 0;}
  to {opacity: 1;}
}

#fade {
 background: #0b0c0d;
  position: fixed;
  overflow: hidden;
  height: 100vh;
  right:0;
  top:0;
  width: 100%;
  height: 0%;
  z-index: 1;
  opacity: 0;
  transition: opacity .3s ease-in, height 0s linear .3s;
  cursor: pointer;
}


</style>

<style>

*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

html {
  font-size: 55%;
}

body {
  background: #0b0c0d;
	font-family: 'Roboto Mono', monospace;
  font-weight: 400;
  font-style: normal;
  line-height: initial;
  color: #00ffffdd;
  font-size: 1.8rem;
  opacity: 1;
  overflow-x: hidden;
  overflow-y: scroll;
}

h1, h2, h3, h4, h5, h6 {
	font-family: 'Roboto Mono', monospace;
  color: #00ffffdd;
}


a, .box {
  background: #00ffffaa;
  border: solid 1px #00ffff99;
  color: #0b0b0b;
  font-weight: 900;
  border-radius: 6px;
  height: 100px;
  min-height: 80px;
  margin: 2rem 0;

  text-decoration: none;

  display: flex;
  align-items: center;
  text-align: center;
  justify-content: center;
}

.box:hover {
  background: #00ffffdd;
}

.box:active {
  background: #00ffff;
}

@media only screen and (max-width: 700px) {
  html {
    font-size: 55%;
  }
}

/* width */
::-webkit-scrollbar {
  width: 2px;
  height: 2px;
}

/* Track */
::-webkit-scrollbar-track {
  background: #0b0b0b;
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: #00ffff;
}

</style>

<style>

.loader {
	color: #f0f0f025;
  font-size: 12px;
  margin: 100px auto;
  width: 1em;
  height: 1em;
  border-radius: 50%;
  position: relative;
  text-indent: -9999em;
  -webkit-animation: load4 1.3s infinite linear;
  animation: load4 1.3s infinite linear;
  -webkit-transform: translateZ(0);
  -ms-transform: translateZ(0);
  transform: translateZ(0);
}

.loader.loader--centered {
  text-align: center;
  margin-top: calc(50vh - .5em);
}

@-webkit-keyframes load4 {
  0%,
  100% {
    box-shadow: 0 -3em 0 0.2em, 2em -2em 0 0em, 3em 0 0 -1em, 2em 2em 0 -1em, 0 3em 0 -1em, -2em 2em 0 -1em, -3em 0 0 -1em, -2em -2em 0 0;
  }
  12.5% {
    box-shadow: 0 -3em 0 0, 2em -2em 0 0.2em, 3em 0 0 0, 2em 2em 0 -1em, 0 3em 0 -1em, -2em 2em 0 -1em, -3em 0 0 -1em, -2em -2em 0 -1em;
  }
  25% {
    box-shadow: 0 -3em 0 -0.5em, 2em -2em 0 0, 3em 0 0 0.2em, 2em 2em 0 0, 0 3em 0 -1em, -2em 2em 0 -1em, -3em 0 0 -1em, -2em -2em 0 -1em;
  }
  37.5% {
    box-shadow: 0 -3em 0 -1em, 2em -2em 0 -1em, 3em 0em 0 0, 2em 2em 0 0.2em, 0 3em 0 0em, -2em 2em 0 -1em, -3em 0em 0 -1em, -2em -2em 0 -1em;
  }
  50% {
    box-shadow: 0 -3em 0 -1em, 2em -2em 0 -1em, 3em 0 0 -1em, 2em 2em 0 0em, 0 3em 0 0.2em, -2em 2em 0 0, -3em 0em 0 -1em, -2em -2em 0 -1em;
  }
  62.5% {
    box-shadow: 0 -3em 0 -1em, 2em -2em 0 -1em, 3em 0 0 -1em, 2em 2em 0 -1em, 0 3em 0 0, -2em 2em 0 0.2em, -3em 0 0 0, -2em -2em 0 -1em;
  }
  75% {
    box-shadow: 0em -3em 0 -1em, 2em -2em 0 -1em, 3em 0em 0 -1em, 2em 2em 0 -1em, 0 3em 0 -1em, -2em 2em 0 0, -3em 0em 0 0.2em, -2em -2em 0 0;
  }
  87.5% {
    box-shadow: 0em -3em 0 0, 2em -2em 0 -1em, 3em 0 0 -1em, 2em 2em 0 -1em, 0 3em 0 -1em, -2em 2em 0 0, -3em 0em 0 0, -2em -2em 0 0.2em;
  }
}
@keyframes load4 {
  0%,
  100% {
    box-shadow: 0 -3em 0 0.2em, 2em -2em 0 0em, 3em 0 0 -1em, 2em 2em 0 -1em, 0 3em 0 -1em, -2em 2em 0 -1em, -3em 0 0 -1em, -2em -2em 0 0;
  }
  12.5% {
    box-shadow: 0 -3em 0 0, 2em -2em 0 0.2em, 3em 0 0 0, 2em 2em 0 -1em, 0 3em 0 -1em, -2em 2em 0 -1em, -3em 0 0 -1em, -2em -2em 0 -1em;
  }
  25% {
    box-shadow: 0 -3em 0 -0.5em, 2em -2em 0 0, 3em 0 0 0.2em, 2em 2em 0 0, 0 3em 0 -1em, -2em 2em 0 -1em, -3em 0 0 -1em, -2em -2em 0 -1em;
  }
  37.5% {
    box-shadow: 0 -3em 0 -1em, 2em -2em 0 -1em, 3em 0em 0 0, 2em 2em 0 0.2em, 0 3em 0 0em, -2em 2em 0 -1em, -3em 0em 0 -1em, -2em -2em 0 -1em;
  }
  50% {
    box-shadow: 0 -3em 0 -1em, 2em -2em 0 -1em, 3em 0 0 -1em, 2em 2em 0 0em, 0 3em 0 0.2em, -2em 2em 0 0, -3em 0em 0 -1em, -2em -2em 0 -1em;
  }
  62.5% {
    box-shadow: 0 -3em 0 -1em, 2em -2em 0 -1em, 3em 0 0 -1em, 2em 2em 0 -1em, 0 3em 0 0, -2em 2em 0 0.2em, -3em 0 0 0, -2em -2em 0 -1em;
  }
  75% {
    box-shadow: 0em -3em 0 -1em, 2em -2em 0 -1em, 3em 0em 0 -1em, 2em 2em 0 -1em, 0 3em 0 -1em, -2em 2em 0 0, -3em 0em 0 0.2em, -2em -2em 0 0;
  }
  87.5% {
    box-shadow: 0em -3em 0 0, 2em -2em 0 -1em, 3em 0 0 -1em, 2em 2em 0 -1em, 0 3em 0 -1em, -2em 2em 0 0, -3em 0em 0 0, -2em -2em 0 0.2em;
  }
}
</style>
