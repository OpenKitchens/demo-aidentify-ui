<script setup>
import Topbar from "@/components/resulttopbar.vue"
import EndAction from "@/components/endaction.vue"
import { ref } from 'vue'

import { useIndexImageStore } from '@/stores/indexImage.js'
import { useCoordinateStore } from '@/stores/coordinate.js'
const coordinate = useCoordinateStore()

const IndexImage = useIndexImageStore()

const imageUrl = ref(`/images/after/${IndexImage.data}.png`)
const imageUrlbefore = ref(`/images/before/${IndexImage.data}.jpg`)


coordinate.data.point1.xPos

console.log("hello")
</script>

<template>
  <div>
    <div class="bg-[#110a0a] w-screen h-dvh fixed z-[-2] top-0 left-0"></div>
    <div class="bg-gradient-to-b from-black via-[#00000055]/70 w-[100vw] left-0 fixed top-0">
      <div class="relative">
        <Topbar class="mx-auto w-[85vw] mt-6 mb-8" />
      </div>
    </div>

    <div class="absolute top-1/2 translate-y-[-50%] left-1/2 translate-x-[-50%] w-[100vw] z-[-1]">
      <div class="relative">
        <!--<div
          :style="{ 'top': coordinate.data.point1.yPos + 'px', 'left': coordinate.data.point1.xPos + 'px', 'position': 'absolute', 'overflow': 'hidden' }">
          <img :src="'/images/before/' + IndexImage.data + '.jpg'" :style="{'background-image': '/images/before/' + IndexImage.data + '.jpg','background-size': 'cover', 'background-repeat': 'no-repeat'}"
            class="w-[100vw]">
        </div>-->

        <img :src="imageUrl" alt="アップロードされた画像" class="w-[100vw]" id="picture">
        <div :style="{'top': coordinate.data.point1.yPos + 'px', 'left': coordinate.data.point1.xPos + 'px', 'position': 'absolute','width': Math.abs(coordinate.data.point1.xPos - coordinate.data.point2.xPos)+'px', 'height': Math.abs(coordinate.data.point1.yPos - coordinate.data.point2.yPos)+'px' }">
          <img :src="imageUrlbefore" :style="{'-webkit-clip-path': 'inset('+coordinate.data.point1.yPos+' '+Number(document.getElementById('picture').width - coordinate.data.point2.xPos)+' '+Number(document.getElementById('picture').height - coordinate.data.point2.yPos)+' '+coordinate.data.point1.xPos+')', 'clip-path': 'inset(20px 60px)+'}">
          <!--上右下左-->
        </div>
      </div>
    </div>

    <div class="fixed bottom-0 left-0 bg-gradient-to-t from-black via-[#00000055]/70">
      <div class="mt-8 mb-6 w-[100vw]">
        <EndAction class="mx-auto" />
      </div>
    </div>
  </div>
</template>

<style></style>