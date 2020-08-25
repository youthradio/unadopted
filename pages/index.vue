<template>
  <div>
    <main class="mw8 ph3">
      <article class="measure-wide center">
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
                  :src="team.photo"
                  class="db"
                  alt="Photo of a dimly lit room with a computer interface terminal."
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
          <!-- <li
            :key="`${i}-${team.name}`"
            class="flex flex-row-ns justify-around-ns items-center flex-column justify-center lh-copy pv3 ba bl-0 bt-0 br-0 b--solid b--red"
          >
            <span class="db"> {{ team.name }} </span>
          </li> -->
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

<style lang="scss" scoped></style>
