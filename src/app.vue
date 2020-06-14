<template>
  <v-app dark>
    <v-container>
      <div class="mb-5">
        Get Source Code:
        <a href="https://github.com/darrenfang/vuetify-datetime-picker/blob/master/src/app.vue" target="_blank">
          https://github.com/darrenfang/vuetify-datetime-picker/blob/master/src/app.vue
        </a>
      </div>

      <v-row align="center">
        <v-expansion-panels multiple>
          <v-expansion-panel>
            <v-expansion-panel-header>Null Value</v-expansion-panel-header>
            <v-expansion-panel-content>
              <v-flex xs4>
                <v-datetime-picker
                   v-model="item.starts_at_unix"
                   date-format="dd.MM.yyyy"
                   :auto-input="true"
                   @input="inputDate('starts_at_unix', 'starts_at')"
                   :time-picker-props="{
                       format: '24hr'
                   }"
                   :textFieldProps="{
                        filled: true,
                        rounded: true
                     }"
                />
              </v-flex>
              <div>Datetime value: <span v-text="item.starts_at"/></div>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-expansion-panels>
      </v-row>
    </v-container>
  </v-app>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css'
import moment from 'moment'

export default {
  data () {
    return {
      timeProps: {
        useSeconds: true,
        ampmInTitle: true
      },
      item: {
        starts_at_unix: moment.utc().toDate(),
        starts_at: null
      }
    }
  },
  methods: {
    inputDate (from, to) {
      if (this.item[from]) {
        this.item[to] = moment.utc(this.item[from]).format('DD.MM.YYYY HH:mm')
      } else {
        this.item[to] = null
      }
    }
  }
}
</script>
