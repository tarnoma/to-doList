<template>
  <q-select
    v-model="lang"
    :options="langOptions"
    label="Choose Language"
    filled
  />
<br>
  <q-form @submit.prevent="onSubmit" @reset="onReset" class="q-gutter-md">
    <div>
      <q-input filled v-model="todo" type="text" :label="$t('inputLable')" />
    </div>
    <div>
      <q-btn :label="$t('addBtn')" type="submit" color="primary" />
      <q-btn :label="$t('resetBtn')" type="reset" color="primary" flat class="q-ml-sm" />
    </div>
  </q-form>
</template>

<script>
import { useTodoListStore } from "../stores/useTodoListStore";
const langOptions = [
  { value: "en-US", label: "English" },
  { value: "th", label: "Thai" },
];
export default {
  name: "TodoForm",
  data() {
    return {
      todo: "",
      store: useTodoListStore(),
      langOptions,
      lang: "",
    };
  },
  methods: {
    onSubmit() {
      if (this.todo.length == 0) return;
      this.store.addTodo(this.todo);
      this.todo = "";
    },
    onReset() {
      this.todo = "";
    },
    // getLangLabel(val) {
    //   return langOptions.find((item) => {
    //     return item.value == val;
    //   }).label;
    // },
  },
    watch: {
    lang() {
      this.$i18n.locale = this.lang.value
      import(`src/i18n/${this.lang.value}`).then(language => {
        this.$q.lang.set(language.default)
      })
    }
  },
//   mounted() {
    // this.lang = this.getLangLabel(this.$i18n.locale);
//   },
};
</script>

<style></style>
