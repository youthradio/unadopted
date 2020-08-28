<template>
  <div class="sans-serif overflow-hidden">
    <nuxt />
  </div>
</template>

<style lang="scss">
@import '~assets/css/styles.scss';
@import '~@/node_modules/plyr/dist/plyr.css';

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
