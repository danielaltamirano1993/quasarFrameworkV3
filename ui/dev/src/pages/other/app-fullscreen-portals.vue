<template>
  <div class="bg-yellow-4 q-pa-md">
    <q-card flat class="bg-grey-2" ref="fullscreen">
      <q-card-section class="text-center q-pt-xl">
        <q-btn
          icon="aspect_ratio"
          label="Fullscreen all"
          flat
          color="primary"
          @click="fullscreenEl()"
        />

        <q-btn
          icon="aspect_ratio"
          label="Fullscreen tooltip"
          flat
          color="primary"
          @click="fullscreenEl($refs.tooltip)"
        />

        <q-btn
          icon="aspect_ratio"
          label="Fullscreen none"
          flat
          color="primary"
          @click="fullscreenNone"
        />

        <div ref="tooltip">
          <h4 class="text-grey q-mb-sm" @click="fullscreenEl($refs.tooltip)">
            Hover to see tooltip
            <q-tooltip>Tooltip</q-tooltip>
          </h4>
        </div>

        <q-btn-dropdown no-caps color="primary" class="q-mt-sm" label="Btn dropdown">
          <q-list dense>
            <q-item clickable v-close-popup class="text-caption text-weight-bold">
              <q-item-section>
                <q-item-label>Item type 1</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable v-close-popup class="text-caption text-weight-bold">
              <q-item-section>
                <q-item-label>Item type 2</q-item-label>
              </q-item-section>
            </q-item>
            <q-item clickable v-close-popup class="text-caption text-weight-bold">
              <q-item-section>
                <q-item-label>Item type 3</q-item-label>
              </q-item-section>
            </q-item>
            <div class="column">
              <q-btn
                stretch
                icon="aspect_ratio"
                label="Fullscreen All"
                flat
                color="primary"
                @click="fullscreenEl()"
              />
            </div>
            <div class="column">
              <q-btn
                stretch
                icon="aspect_ratio"
                label="Fullscreen Tooltip"
                flat
                color="primary"
                @click="fullscreenEl($refs.tooltip)"
              />
            </div>
            <div class="column">
              <q-btn
                stretch
                icon="aspect_ratio"
                label="Fullscreen None"
                flat
                color="primary"
                @click="fullscreenNone"
              />
            </div>
          </q-list>
        </q-btn-dropdown>

        <q-select
          v-model="model"
          :options="options"
          label="Select"
        />

        <div class="q-mt-sm q-gutter-md">
          <q-btn label="Show simple dialog" @click="showSimpleDialog" />

          <q-btn label="Show dlg in dlg" @click="dlgInDlg1 = true" />

          <q-btn label="Show bottom sheet" @click="showBottomSheet" />

          <q-btn label="Show dialog" @click="dialog1 = true" />

          <q-btn label="Toggle seamless dialog (in fullscreen el)" @click="dialog2 = dialog2 === false" />

          <q-btn label="Toggle seamless dialog (outside fullscreen el)" @click="dialog3 = dialog3 === false" />
        </div>

        <q-dialog v-model="dialog1">
          <q-card class="bg-white">
            <q-card-section>
              Modal dialog
            </q-card-section>

            <q-card-section>
              <q-btn
                icon="aspect_ratio"
                label="Fullscreen all"
                flat
                color="primary"
                @click="fullscreenEl()"
              />

              <q-btn
                icon="aspect_ratio"
                label="Fullscreen inside"
                flat
                color="primary"
                @click="fullscreenEl($refs.fullscreenInside1.$el)"
              />

              <q-btn
                icon="aspect_ratio"
                label="Fullscreen none"
                flat
                color="primary"
                @click="fullscreenNone"
              />
            </q-card-section>

            <q-card-section ref="fullscreenInside1" class="bg-orange-2 q-pa-md">
              Fullscreen inside modal dialog
              <span class="text-italic">Hover here for tooltip <q-tooltip>Some tooltip</q-tooltip></span>
            </q-card-section>
          </q-card>
        </q-dialog>

        <q-dialog v-model="dialog2" seamless position="top">
          <q-card class="bg-white">
            <q-card-section>
              Seamless dialog (in fullscreen el)
            </q-card-section>

            <q-card-section>
              <q-btn
                icon="aspect_ratio"
                label="Fullscreen all"
                flat
                color="primary"
                @click="fullscreenEl()"
              />

              <q-btn
                icon="aspect_ratio"
                label="Fullscreen inside"
                flat
                color="primary"
                @click="fullscreenEl($refs.fullscreenInside2.$el)"
              />

              <q-btn
                icon="aspect_ratio"
                label="Fullscreen none"
                flat
                color="primary"
                @click="fullscreenNone"
              />
            </q-card-section>

            <q-card-section ref="fullscreenInside2" class="bg-blue-2 q-pa-md">
              <div class="x-my-md">
                Fullscreen inside seamless dialog (in fullscreen el)
              </div>

              <q-btn label="Toggle seamless dialog inside local fullscreen" @click="dialog4 = dialog4 === false" />

              <q-dialog v-model="dialog4" seamless position="left">
                <q-card class="bg-white">
                  <q-card-section>
                    Seamless dialog
                  </q-card-section>

                  <q-card-section>
                    <q-btn
                      icon="aspect_ratio"
                      label="Fullscreen all"
                      flat
                      color="primary"
                      @click="fullscreenEl()"
                    />

                    <q-btn
                      icon="aspect_ratio"
                      label="Fullscreen inside"
                      flat
                      color="primary"
                      @click="fullscreenEl($refs.fullscreenInside4.$el)"
                    />

                    <q-btn
                      icon="aspect_ratio"
                      label="Fullscreen none"
                      flat
                      color="primary"
                      @click="fullscreenNone"
                    />
                  </q-card-section>

                  <q-card-section ref="fullscreenInside4" class="bg-red-2 q-pa-md">
                    Fullscreen inside modal dialog
                    <span class="text-italic">Hover here for tooltip <q-tooltip>Some tooltip</q-tooltip></span>
                  </q-card-section>
                </q-card>
              </q-dialog>
            </q-card-section>
          </q-card>
        </q-dialog>
      </q-card-section>
    </q-card>

    <video
      style="width: 300px"
      src="https://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4"
      controls
      playsinline
      loop
    />

    <q-dialog v-model="dialog3" seamless position="bottom">
      <q-card class="bg-white">
        <q-card-section>
          Seamless dialog (outside fullscreen el)
        </q-card-section>

        <q-card-section>
          <q-btn
            icon="aspect_ratio"
            label="Fullscreen all"
            flat
            color="primary"
            @click="fullscreenEl()"
          />

          <q-btn
            icon="aspect_ratio"
            label="Fullscreen inside"
            flat
            color="primary"
            @click="fullscreenEl($refs.fullscreenInside3.$el)"
          />

          <q-btn
            icon="aspect_ratio"
            label="Fullscreen none"
            flat
            color="primary"
            @click="fullscreenNone"
          />
        </q-card-section>

        <q-card-section ref="fullscreenInside3" class="bg-green-2 q-pa-md">
          Fullscreen inside seamless dialog (outside fullscreen el)
          <span class="text-italic">Hover here for tooltip <q-tooltip>Some tooltip</q-tooltip></span>
        </q-card-section>
      </q-card>
    </q-dialog>

    <q-dialog v-model="dlgInDlg1" persistent>
      <q-card ref="dlgInDlg1Target">
        <q-card-section>
          <div class="text-h6">Inception</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Perferendis laudantium minus earum totam modi laborum illo, corporis fuga saepe animi aliquam ea enim assumenda ut nulla natus aperiam quis. Iste.
        </q-card-section>

        <q-card-actions align="right" class="text-primary">
          <q-btn flat label="Open another dialog" @click="dlgInDlg2 = true" />
          <q-btn flat label="Fullscreen" @click="dlgInDlg1Fullscreen" />
          <q-btn flat label="Show notif" @click="showNotif" />
          <q-btn flat label="Close" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <q-dialog v-model="dlgInDlg2" persistent transition-show="scale" transition-hide="scale">
      <q-card class="bg-teal text-white" style="width: 300px" ref="dlgInDlg2Target">
        <q-card-section>
          <div class="text-h6">Persistent</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          Click/Tap on the backdrop.
        </q-card-section>

        <q-card-actions align="right" class="bg-white text-teal">
          <q-btn flat label="OK" v-close-popup />
          <q-btn flat label="Show notif" @click="showNotif" />
          <q-btn flat label="Fullscreen" @click="dlgInDlg2Fullscreen" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>

<script>
export default {
  data () {
    return {
      model: null,
      options: [ 'Option 1', 'Option 2', 'Option 3' ],

      dialog1: false,
      dialog2: false,
      dialog3: false,
      dialog4: false,

      dlgInDlg1: false,
      dlgInDlg2: false
    }
  },
  methods: {
    fullscreenEl (el = this.$refs.fullscreen.$el) {
      this.$q.fullscreen
        .exit()
        .catch(() => {})
        .then(() => {
          setTimeout(() => {
            this.$q.fullscreen
              .request(el)
              .catch(() => {})
          })
        })
    },

    fullscreenNone () {
      this.$q.fullscreen.exit()
    },

    showSimpleDialog () {
      this.$q.dialog({
        title: 'Confirmation required',
        message: 'Are you sure?',
        cancel: {
          flat: true,
          noCaps: true,
          label: 'Cancel'
        },
        ok: {
          noCaps: true,
          color: 'negative',
          label: 'Confirm'
        },
        persistent: true
      }).onOk(() => {
        // do something
      })
    },

    showBottomSheet () {
      this.$q.bottomSheet({
        message: 'Bottom Sheet message',
        actions: [
          {
            label: 'Fullscreen All',
            img: 'https://cdn.quasar.dev/img/logo_drive_128px.png',
            id: 'fullscreen all'
          },
          {
            label: 'Fullscreen None',
            img: 'https://cdn.quasar.dev/img/logo_keep_128px.png',
            id: 'fullscreen none'
          }
        ]
      }).onOk(action => {
        if (action.id === 'fullscreen all') {
          this.showBottomSheet()
          this.fullscreenEl()
        }
        else if (action.id === 'fullscreen none') {
          this.showBottomSheet()
          this.fullscreenNone()
        }
      })
    },

    dlgInDlg1Fullscreen () {
      this.$refs.dlgInDlg1Target.$el.requestFullscreen()
    },

    dlgInDlg2Fullscreen () {
      this.$refs.dlgInDlg2Target.$el.requestFullscreen()
    },

    showNotif () {
      this.$q.notify({
        message: 'Notification message'
      })
    }
  }
}
</script>
