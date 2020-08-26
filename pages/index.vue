<template>
  <div>
    <main class="mw8 center">
      <vue-plyr :options="{ controls: ['play-large', 'pip'] }">
        <div class="plyr__video-embed">
          <iframe
            class="db w-100"
            :src="
              `https://www.youtube-nocookie.com/embed/${articleData.trailervideoid}?controls=0&iv_load_policy=3&modestbranding=1&playsinline=1&showinfo=0&rel=0&enablejsapi=1`
            "
            :data-poster="articleData.trailerposter"
            frameborder="0"
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
            allowtransparency
          ></iframe>
        </div>
      </vue-plyr>
      <article class="measure-wide center ph3">
        <h2 class="lh-title ttu londrina-solid red">About</h2>
        <div class="lh-copy" v-html="articleData.about.text" />
        <h2 class="lh-title ttu londrina-solid red">Screenings</h2>
        <ul class="list mh0 pl0">
          <template v-for="(screening, i) in articleData.screenings">
            <li
              :key="`${i}-${screening.title}`"
              class="flex flex-row-ns justify-around-ns items-center flex-column justify-center lh-copy pv3 ba bl-0 bt-0 br-0 b--solid b--red"
            >
              <span class="db"> {{ screening.location }} </span
              ><span class="db"> {{ screening.event }}</span>
              <span class="db"> {{ toLocaleDate(screening.date) }}</span>
            </li>
          </template>
        </ul>
        <h2 class="lh-title ttu londrina-solid red">Meet the Team</h2>
        <template v-for="(team, i) in articleData.team">
          <article :key="`${i}-${team.name}`">
            <div class="flex flex-column flex-row-ns">
              <div class="pr3-ns mb4 mb0-ns w-100 w-40-ns">
                <img
                  :data-src="team.photo"
                  class="db lazyload"
                  :alt="`${team.name} Photo`"
                />
              </div>
              <div class="w-100 w-60-ns pl3-ns">
                <h2 class="mt0 lh-title londrina-solid red">
                  {{ team.name }}
                </h2>
                <div class="f6 f5-l lh-copy" v-html="team.text"></div>
              </div>
            </div>
          </article>
        </template>
      </article>
      <ShareContainer
        :title="postData.title"
        :description="postData.summary"
        class="mv3"
      />
    </main>
  </div>
</template>

<script>
import POSTCONFIG from '../post.config'
import CommonUtils from '../mixins/CommonUtils'
import ArticleData from '../data/data.json'
import ShareContainer from '~/components/Custom/ShareContainer'

export default {
  components: {
    ShareContainer
  },
  mixins: [CommonUtils],
  asyncData(ctx) {
    return {
      articleData: ArticleData.content[0],
      postData: POSTCONFIG
    }
  },
  data() {
    return {}
  },
  computed: {},
  watch: {},
  mounted() {},
  methods: {
    toLocaleDate(date) {
      return new Date(date).toLocaleDateString(undefined, {
        year: 'numeric',
        month: 'long',
        day: 'numeric'
      })
    }
  }
}
</script>

<style lang="scss">
@import '~@/node_modules/plyr/dist/plyr.css';
@import '~@/assets/css/variables';
.plyr--full-ui input[type='range'] {
  // -webkit-appearance: none;
  // background: 0 0;
  // border: 0;
  // border-radius: 26px;
  color: $red;
  // display: block;
  // height: 19px;
  // margin: 0;
  // padding: 0;
  // transition: box-shadow .3s ease;
  // width: 100%;
}
.plyr--audio .plyr__control.plyr__tab-focus,
.plyr--audio,
.plyr--video,
.plyr--audio .plyr__control:hover,
.plyr--audio .plyr__control[aria-expanded='true'],
.plyr--video .plyr__control:hover,
.plyr--video .plyr__control[aria-expanded='true'],
.plyr__control--overlaid {
  background: $red;
}
.plyr__poster {
  background-size: cover;
}
</style>
