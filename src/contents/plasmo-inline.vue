<template>
  <button>Custom button</button>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import type { PlasmoContentScript, PlasmoGetInlineAnchor } from "plasmo";

export const config: PlasmoContentScript = {
  matches: ["https://www.plasmo.com/*"]
}

export const getInlineAnchor: PlasmoGetInlineAnchor = () =>
  document.querySelector("#supercharge > h2 > span")

// Use this to optimize unmount lookups
export const getShadowHostId = () => "plasmo-inline-example-unique-id"

export default defineComponent({
  setup() {
    return {}
  }
})
</script>
