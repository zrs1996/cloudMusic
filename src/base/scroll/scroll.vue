<template>
  <div ref="wrapper">
      <slot></slot>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
    name: "scroll",
    props: {
        probeType: {
            type: Number,
            default: 1
        },
        click: {
            type: Boolean,
            default: true
        },
        data: {
            type: Array,
            default: null
        }
    },
    mounted() {
        setTimeout(() => {
            this._initScroll()
        }, 20);
    },
    methods: {
        _initScroll() {
            if (!this.$refs.wrapper) { return }
            this.srcoll = new BScroll(this.$refs.wrapper, {
                probeType: this.probeType,
                click: this.click
            })
        },
        enable() {
            this.srcoll && this.srcoll.enable()
        },
        disable() {
            this.srcoll && this.srcoll.disable()
        },
        refresh() {
            this.srcoll && this.srcoll.refresh()
        }
    },
    components: {
        BScroll
    },
    watch: {
        data() {
            setTimeout(() => {
                this.refresh()
            }, 20);
        }
    }
}
</script>

<style>

</style>