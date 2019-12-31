<template>
  <div>123456</div>
</template>

<script>
import Vue from "./vue.js";

export default {
  data() {
    return {};
  },
  beforeCreate() {
    if (this.$isServer) return;

    this.popperVM = new Vue({
      data: { node: "123" },
      render() {
        return this.node;
      }
    }).$mount();
  },
  mounted() {
    if (this.popperVM) {
      this.popperVM.node = (
        <div>
          23123
          <div ref="abcd">1234</div>
        </div>
      );
    }
    window.cc = this;
    this.$nextTick(() => {
      document.body.appendChild(this.$refs.abcd);
    });
  },
  methods: {
    handleChange(value) {
      console.log(value);
    }
  }
};
</script>
