<template>
  <header class="w-100 grid f7 f6-ns bg-black">
    <div
      class="dn flex-ns flex-wrap justify-around items-center row-1 grid-col-1 mv3"
    >
      <a class="link db grow white no-underline ph2 pv2" href="#about"
        >ABOUT THE FILM</a
      >
      <a class="link db grow white no-underline ph2 pv2" href="#screenings"
        >SCREENINGS</a
      >
    </div>

    <div class="row-span grid-col-2 center z-2 pointer-events-none">
      <div class="bg-black pa2 mw6">
        <MainLogo />
      </div>
    </div>
    <div
      class="dn flex-ns flex-wrap justify-around items-center row-1 grid-col-3 mv3"
    >
      <a class="link db grow white no-underline ph2 pv2" href="#team"
        >MEET THE TEAM</a
      >
      <a class="link db grow white no-underline ph2 pv2" href="#contact"
        >CONTACT</a
      >
    </div>
    <div class="video">
      <div class="mw9 center">
        <vue-plyr id="trailer" :options="{ controls: ['play-large', 'pip'] }">
          <div class="plyr__video-embed">
            <iframe
              class="db w-100"
              :src="
                `https://www.youtube-nocookie.com/embed/${videoid}?controls=0&iv_load_policy=3&modestbranding=1&playsinline=1&showinfo=0&rel=0&enablejsapi=1`
              "
              :data-poster="poster"
              frameborder="0"
              allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
              allowfullscreen
              allowtransparency
            >
              <img class="db w-100" :src="poster" />>
            </iframe>
          </div>
        </vue-plyr>
      </div>
    </div>
  </header>
</template>

<script>
import MainLogo from './MainLogo'

export default {
  components: {
    MainLogo
  },
  props: {
    videoid: {
      required: true,
      type: String
    },
    poster: {
      required: true,
      type: String
    }
  }
}
</script>

<style lang="scss" scoped>
@import '~assets/css/styles.scss';

.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: minmax(50px, auto) 1fr auto;
}
.grid-col-1 {
  grid-column: 2 / span 3;
}
.grid-col-2 {
  grid-column: 5 / span 4;
}
.grid-col-3 {
  grid-column: 9 / span 3;
}
.row-1 {
  grid-row: 1 / 3;
}
.row-span {
  grid-row: 1 / span 3;
}
.video {
  grid-row: 3;
  grid-column: 1 / span 12;
}

@media screen and (min-width: 52em) {
  .video {
    grid-row: 3;
    grid-column: 2 / span 10;
  }
}
</style>
