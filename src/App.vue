<template>
  <v-app>
    <v-main class="pa-12">
      <h4> Slotted content with a wrapper div - incorrect order</h4>
      <ComponentWithASlot class="bg-red-accent-1">
        <div class="">
          <div v-if="showFirstChild">1</div>
          <div>2</div>
          <div>3</div>
        </div>

        <VDialog />
      </ComponentWithASlot>

      <VDivider class="my-10" />

      <h4>No wrapper div - correct order</h4>
      <ComponentWithASlot class="bg-green-accent-1">
        <div v-if="showFirstChild">1</div>
        <div>2</div>
        <div>3</div>

        <VDialog />
      </ComponentWithASlot>

      <VDivider class="my-10" />

      <h4>wrapper div with v-if=true - correct order</h4>
      <ComponentWithASlot class="bg-green-accent-1">
        <div v-if="true">
          <div v-if="showFirstChild">1</div>
          <div>2</div>
          <div>3</div>
        </div>

        <VDialog />
      </ComponentWithASlot>

      <VDivider class="my-10" />

      <h4>Wrapper div; no VDialog - correct order</h4>
      <ComponentWithASlot class="bg-green-accent-1">
        <div>
          <div v-if="showFirstChild">1</div>
          <div>2</div>
          <div>3</div>
        </div>
      </ComponentWithASlot>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
import ComponentWithASlot from '@/ComponentWithASlot.vue';

import { ref } from 'vue';

const showFirstChild = ref(false);

setTimeout(() => {
  showFirstChild.value = true;
}, 100)
</script>
