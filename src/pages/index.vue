<script setup lang="ts">
import { GamePlay } from '~/composables/logic'

const play = new GamePlay(12, 12)
const state = play.state
</script>

<template>
  <div>
    Minesweeper

    <div p5>
      <div
        v-for="row, y in state"
        :key="y"
        flex="~"
        items-center justify-center
      >
        <MineBlock
          v-for="block, x in row" :key="x"
          :block="block"
          @click="play.onClick(block)"
          @contextmenu.prevent="play.onRightClick(block)"
        />
      </div>
    </div>
  </div>
</template>
