<template>
  <div class="container">
    CONTAINER
    <div class="background"></div>
    <div id="particles"></div>
    <div class="foreground"></div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  mounted() {
    this.animate();
    window.console.log('HELLO');
  },
  methods: {
    animate() {
      const particleContainer = document.getElementById('particles');
      const Nparticles = 100;
      const particles = [];

      // function to return a random number from a given min and max
      function rand(min, max) {
        return Math.floor(Math.random() * (max - min)) + min;
      }

      function CreateParticle(i) {
        this.id = i;
        this.width = `${rand(1, 20)}px`;
        this.height = this.width;
        this.x = `${rand(10, 90)}%`;
        this.delay = `${rand(1, 60)}s`;
        this.duration = `${rand(10, 60)}s`;
        this.html = `<span style=" width: ${
          this.width
        }; height: ${
          this.height
        }; left: ${
          this.x
        }; animation-delay: ${
          this.duration
        }; animation-duration: ${
          this.duration
        }; "></span>`;
      }

      while (particles.length <= Nparticles) {
        const Particle = new CreateParticle(particles.length);
        particles.push(Particle);
        particleContainer.innerHTML += Particle.html;
      }

      // Hope you liked it and that has inspired you to create something awesome
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
// Colour Variables
$magenta: #a42b52;
$blue: #224154;

@for $i from 1 through 100 {
  @keyframes particle-#{$i} {
    0% {
      transform: translateX(0px) translateY(0vh);
      opacity: 1;
    }
    30% {
      transform: translateX((random(80) - 40) + px) translateY(-10vh);
      opacity: 0.9;
    }
    40% {
      transform: translateX((random(80) - 40) + px) translateY(-20vh);
      opacity: 0.8;
    }
    50% {
      transform: translateX((random(80) - 40) + px) translateY(-30vh);
      opacity: 0.7;
    }
    60% {
      transform: translateX((random(80) - 40) + px) translateY(-40vh);
      opacity: 0.6;
    }
    70% {
      transform: translateX((random(80) - 40) + px) translateY(-50vh);
      opacity: 0.5;
    }
    100% {
      transform: translateX((random(80) - 40) + px) translateY(-100vh);
      opacity: 0;
    }
  }
  .container #particles span:nth-child(#{$i}) {
    animation-name: particle-#{$i};
  }
}

html,
body {
  position: relative;
  height: 100%;
  background-color: $blue;
  text-align: center;
  overflow: hidden;
  min-width: 768px;
}

.container {
  position: relative;
  width: 100vw;
  height: 100vh;
  .background {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;
    background-image: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/751678/my-illustration-background.png");
    background-position: center bottom;
    background-repeat: no-repeat;
    background-size: 100% auto;
    z-index: 0;
  }
  #particles {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    span {
      display: inline-block;
      position: absolute;
      bottom: 0%;
      border-radius: 50%;
      background-color: $magenta;
      opacity: 1;
      box-shadow: 0px 0px 10px 5px rgba(164, 43, 82, 1);
      transform: translateX(0%) translateY(0%);
      animation-iteration-count: infinite;
      animation-timing-function: linear;
    }
  }
  .foreground {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    width: 100%;
    height: 100%;
    background-image: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/751678/my-illustration-foreground.png");
    background-position: center bottom;
    background-repeat: no-repeat;
    background-size: 100% auto;
    z-index: 2;
  }
}
</style>
