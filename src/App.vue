<template>
  <div id="app" class="container py-5 bg-secondary">
    <div
      v-for="(field, index) in fields"
      :id="field.id"
      :key="index"
      class="row"
    >
      <div class="col-12 col-md-5 mb-1">
        <b-form-select
          v-model="selectedLang[index]"
          :options="langOptions"
        />
      </div>

      <div class="col-10 col-md-5 mb-1">
        <b-form-select
          v-model="selectedSkill[index]"
          :options="skillOptions"
        />
      </div>

      <div class="col-2 mb-1 pl-0">
        <b-button
          variant="warning"
          class=""
          @click="RemoveField(index)"
        > Remove
        </b-button>
      </div>

    </div>

    <div class="col-12 pl-0">
      <b-button
        variant="warning"
        class=""
        @click="AddField"
      > Add
      </b-button>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
import { BootstrapVue, BButton, BFormSelect } from 'bootstrap-vue'


Vue.use(BootstrapVue)
Vue.component('b-button', BButton)
Vue.component('b-form-select', BFormSelect)

export default {
  name: 'App',
  data() {
    return {
      fields: [{ id: 1 }],
      nextTodoId: 2,

      selectedLang: ['0'],
      langOptions: [
        { value: '0', text: 'English' },
        { value: 'a', text: 'German' },
        { value: 'b', text: 'China' },
        { value: 'c', text: 'Polish' },
        { value: 'd', text: 'Russian' },
      ],

      selectedSkill: ['a1'],
      skillOptions: [
        { value: 'a1', text: 'Elementary' },
        { value: 'a2', text: 'Pre-Intermediate' },
        { value: 'b1', text: 'Intermediate' },
        { value: 'b2', text: 'Upper-Intermediate' },
        { value: 'c1', text: 'Advanced' },
      ],
    }
  },
  methods: {
    AddField() {
      this.fields.push({
        id: this.nextTodoId += this.nextTodoId,
      })
    },
    RemoveField(index) {
      this.selectedLang.splice(index, 1)
      this.selectedSkill.splice(index, 1)
      this.fields.splice(index, 1)
    },
  },
}
</script>

  