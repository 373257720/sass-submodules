<template>
  <div class="GZ-input">
    <el-input
     class="GZ-input"
      placeholder="Please input"
      clearable
      :style="CombineStyle"
      v-model="curName"
    ></el-input>
  </div>
</template>
<script>
export default {
  props: {
    name: String,
    styleParameters: Object
  },
  data () {
    return {
      curName: this.name,
      styleData: {
        '--color': '#606266',
        '--width': '60px',
        '--height': '40px',
        '--border': '2px',
        '--shape': 'solid',
        '--radius': '5px',
        '--background': 'white',
        '--padding': '0 30px 0 15px'
      },
      CombineStyle: {}
    }
  },
  created () {
    this.CombineStyle = {
      ...this.styleData,
      ...this.styleParameters
    }
    console.log(this.CombineStyle)
  },
  watch: {
    name: function (newVal, oldVal) {
      this.curName = newVal
    },
    curName: function (newVal, oldVal) {
      this.$emit('update:name', newVal)
    }
  },
  methods: {}
}
</script>
<style lang='scss' scoped>
.GZ-input {
  @include Font(
    $FontSize: inherit,
    $lineHeight: var(--lineHeight),
    $color: #606266
  );
  /deep/ .el-input {
    width: var(--width);
    .el-input__inner {
      color: var(--color);
      @include border(
        $px: var(--border),
        $shape: var(--shape),
        $radius: var(--radius)
      );
      @include boxModel(
        $width: var(--width),
        $height: var(--height),
        $background-color: var(--background),
        $padding: var(--padding)
      );
      &:focus {
        outline: none;
        border-color: $themeColor;
      }
    }
  }
}
</style>
