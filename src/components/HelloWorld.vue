<template>
  <v-container>
    <v-row>
      <v-col v-for="(item, i) in items" :key="i"
             cols="4"

      >
        <v-card
            :color="item.color"
            dark
            height="200"
        >
          <v-card-title
              class="headline"
          >
            {{ item.title }}
          </v-card-title>
          <v-card-subtitle v-text="item.artist"></v-card-subtitle>

          <v-card-actions>
            <v-btn
                outlined
                width="100%"
                style="top:50px!important;"
                @click="overlay = !overlay"
            >
              Subscribe
            </v-btn>
            <v-overlay
                :absolute="absolute"
                :opacity="opacity"
                :value="overlay"
                :z-index="zIndex"
            >
              <v-btn
                  color="primary"
                  @click="overlay = false"
              >
                Hide Overlay
              </v-btn>

              <v-btn
                  color="primary"
                  @click="overlay = false"
              >
                Hide Overlay
              </v-btn>
            </v-overlay>
          </v-card-actions>
        </v-card>


      </v-col>


    </v-row>
  </v-container>

</template>

<script>
export default {
  name: 'HelloWorld',
  props : {
    items : {
      type: Array,
      default() {
        return []
      }
    }
  },
  data: () => ({
    absolute: false,
    opacity: 0.1,
    overlay: false,
    zIndex: 5,


  }),

  methods: {

  }
}
</script>


