<script lang="ts" setup>
defineProps({
  title: String,
  desc: String,
  buttonText: String,
  reverse: Boolean,
  hasBackground: Boolean,
  hasBtn: Boolean,
  isMobileReverse: Boolean,
  image: String,
});
</script>
<template>
  <section :class="{'bg-background-secondary' : hasBackground, 'section-2' : reverse, 'section-1' : !reverse}">
    <div class="relative md:max-w-7xl xl:max-w-screen-2xl mx-auto grid grid-cols-12 gap-4 min-h-[60vh] max-h-screen  px-5 py-10">
      <div class="col-span-12 w-full h-full lg:col-span-6 md:col-span-6 sm:col-span-12" :class="{
        'md:order-first col-1': !reverse,
        'md:order-last col-2': reverse,
        'order-last': isMobileReverse,
        'order-first': !isMobileReverse,
      }">
        <div class="h-full flex flex-col gap-10 md:justify-center items-center">
          <p :class="{'title-1' : hasBackground,'title-2' : !hasBackground}" class="text-center text-4xl md:text-5xl inline-block lg:w-5/6 md:w-full mx-auto" >
            {{ title }}
          </p>
          <p
            class="desc-text text-text-secondary text-base md:text-lg  font-normal leading-normal text-justify md:text-center inline-block lg:w-full md:w-full mx-auto" :class="{'desc-1' : hasBackground,'desc-2' : !hasBackground}">
            <slot name="desc" />
          </p>

          <ButtonOutline url="/white-paper" v-if="hasBtn" :text="buttonText" />
        </div>
      </div>
      <div class="col-span-12 w-full lg:col-span-6 md:col-span-6 sm:col-span-12 h-full flex-col flex justify-center"
        :class="{
          'md:order-first col-1 ': reverse,
          'md:order-last col-2  ': !reverse,
          'order-first': isMobileReverse,
          'order-last': !isMobileReverse

        }">
        <div class="h-auto w-full mx-auto md:mx-0 lg:w-[500px] md:w-auto sm:w-2/3"
          :class="{ 'md:mr-auto': reverse, 'md:ml-auto': !reverse }">
          <img class="mx-auto md:mx-0" :class="{ 'md:mr-auto': reverse, 'md:ml-auto': !reverse }"
            :src="`/images/${image}.svg`"  alt="Section image" />
          <!-- <slot name="model" /> -->
        </div>
      </div>
    </div>
  </section>
</template>


