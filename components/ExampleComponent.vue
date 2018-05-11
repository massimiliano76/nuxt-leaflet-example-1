<template>
  <div>
    Hello, {{ greeting }}!
    <b-button @click="doStuff" :text="doStuff">Do stuff</b-button>
  </div>
</template>

<script>
export default {
  data: () => ({
    greeting: "Hello!"
  }),
  methods: {
    doStuff: function() {
      return "hello";
    }
  }
};
</script>

