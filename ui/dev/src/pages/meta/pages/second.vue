<template>
  <q-page padding>
    <q-card class="inline-block q-mt-md">
      <q-card-section class="text-subtitle text-secondary">
        Current page: second
      </q-card-section>
      <q-separator />
      <q-card-section>
        <div class="row no-wrap items-center">
          <div class="text-caption q-mr-sm">Layout 1:</div>
          <q-btn-group>
            <q-btn no-caps color="primary" to="/meta/layout_1/first" label="first" />
            <q-btn no-caps color="secondary" to="/meta/layout_1/second" label="second" />
            <q-btn no-caps color="orange" to="/meta/layout_1/third" label="third" />
          </q-btn-group>
        </div>
        <div class="row no-wrap items-center q-mt-sm">
          <div class="text-caption q-mr-sm">Layout 2:</div>
          <q-btn-group>
            <q-btn no-caps color="primary" to="/meta/layout_2/first" label="first" />
            <q-btn no-caps color="secondary" to="/meta/layout_2/second" label="second" />
            <q-btn no-caps color="orange" to="/meta/layout_2/third" label="third" />
          </q-btn-group>
        </div>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<style>
</style>

<script>
import { useMeta } from 'quasar'
import { onMounted, onUnmounted } from 'vue'

export default {
  name: 'PageSecond',

  setup () {
    console.log('created second.vue')

    useMeta({
      title: 'PAGE 2',
      meta: {
        description: { name: 'description', content: 'Page 2' }
      },
      link: {
        google: { rel: 'stylesheet', href: 'http://bogus.com/2' }
      },
      bodyAttr: {
        some: 'value'
      },
      htmlAttr: {
        'third-page': 'w'
      },
      script: {
        ldJson: {
          type: 'application/ld+json',
          innerHTML: `{ "@context": "http://schema.org" }` // eslint-disable-line
        }
      }
    })

    onMounted(() => {
      console.log('mounted second.vue')
    })

    onUnmounted(() => {
      console.log('unmounted second.vue')
    })
  }
}
</script>
