<template>
  <div class="introduction-video rounded-borders overflow-hidden" style="max-width: 530px">
    <div class="introduction-video__thumbnail relative-position" @click="showVideo">
      <q-img v-if="!video" src="https://cdn.quasar.dev/img/quasar-app-in-30-min.jpg" :ratio="1.78">
        <q-icon class="play-button absolute-center" color="white" name="play_circle_outline" size="150px" />
      </q-img>
    </div>
    <div v-if="video" class="introduction-video__container">
      <iframe
        src="https://www.youtube.com/embed/GV-D85D9KJQ?autoplay=1"
        frameborder="0"
        allowfullscreen
      />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const video = ref(false)

function showVideo () {
  video.value = true
}
</script>

<style lang="sass">
.introduction-video

  &__thumbnail
    cursor: pointer

    &:after
      content: ''
      display: block
      position: absolute
      left: 0
      top: 0
      width: 100%
      height: 100%
      z-index: 1
      background-color: rgba(0, 0, 0, 0.3)
      opacity: 0
      transition: opacity $header-quick-transition

    .play-button
      z-index: 2
      opacity: 0.5
      transition: opacity $header-quick-transition

    &:hover
      &:after
        opacity: 1

      .play-button
        opacity: 0.8

        &:hover
          opacity: 1

  &__container
    position: relative
    padding-bottom: 56.25%
    height: 0
    overflow: hidden
    max-width: 100%

    iframe, object, embed
      position: absolute
      top: 0
      left: 0
      width: 100%
      height: 100%
</style>
