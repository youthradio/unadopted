<template>
  <div>
    <Header
      :videoid="articleData.trailervideoid"
      :poster="articleData.trailerposter"
    />
    <main class="mw8 center">
      <article class="measure-wide center ph3">
        <h2 id="about" class="lh-title ttu londrina-solid red pt4">About</h2>
        <div class="f6 f5-ns lh-copy" v-html="articleData.about.text" />

        <h2 id="screenings" class="lh-title ttu londrina-solid red pt4">
          Screenings
        </h2>
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

        <h2 id="team" class="lh-title ttu londrina-solid red pt4">
          Meet the Team
        </h2>
        <template v-for="(team, i) in articleData.team">
          <article :key="`${i}-${team.name}`">
            <div class="flex flex-column flex-row-ns pb4">
              <div class="pr3-ns mb4 mb0-ns w-100 w-40-ns">
                <img
                  :data-src="team.photo"
                  class="db lazyload w-100 mw5"
                  :alt="`${team.name} Photo`"
                />
              </div>
              <div class="w-100 w-60-ns pl3-ns">
                <h2 class="mt0 lh-title londrina-solid red">
                  {{ team.name }}
                </h2>
                <div class="f6 f5-ns lh-copy" v-html="team.text"></div>
              </div>
            </div>
          </article>
        </template>

        <h2 id="contact" class="lh-title ttu londrina-solid red pt4">
          Contact
        </h2>
        <div class="f6 f5-ns lh-copy pb4" v-html="articleData.contact.text" />
      </article>
    </main>
    <Footer />
  </div>
</template>

<script>
import POSTCONFIG from '../post.config'
import CommonUtils from '../mixins/CommonUtils'
import ArticleData from '../data/data.json'
import Footer from '~/components_local/Footer'
import Header from '~/components_local/Header'

export default {
  components: {
    Footer,
    Header
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

<style></style>
