<script setup lang="ts">
const socials = [
  {
    icon: "tabler:brand-instagram",
    url: "https://www.instagram.com/cvlyuz",
    text: "Follow on Instagram",
  },
  {
    icon: "tabler:brand-telegram",
    url: "https://t.me/cvlyuz",
    text: "Follow on Telegram",
  },
  {
    icon: "tabler:brand-x",
    url: "https://x.com/cvlyuz",
    text: "Follow on X(Twitter)",
  },
];
</script>
<template>
  <div
    class="relative w-full h-screen p-10 bg-[url('../../assets/images/bg-pattern.jpg')] bg-contain bg-center"
  >
    <div class="container mx-auto h-full flex items-center justify-center">
      <div class="flex flex-col items-center">
        <div
          class="py-1 px-2.5 flex items-center gap-x-2 bg-neutral-800 border border-white/[0.8] rounded-full mb-2"
        >
          <span class="relative flex size-2">
            <span
              class="absolute inline-flex size-full rounded-full opacity-75 bg-success animate-ping"
            />
            <span
              class="relative inline-flex size-2 scale-90 rounded-full bg-success"
            />
          </span>
          <p class="text-xs text-white">Coming soon</p>
        </div>
        <div class="text-center space-y-1 sm:space-y-5 mb-4 sm:mb-6">
          <p
            class="font-publico font-bold text-2xl/[130%] sm:text-5xl/[54px] text-neutral-800"
          >
            Design your story, <br />
            <span class="text-blue-500">not just a document</span>
          </p>
          <p class="text-neutral-500 text-sm sm:text-lg">
            Your career isn’t just experience — it’s evolution. Let’s write it
            beautifully.
          </p>
        </div>
        <UButton
          size="md"
          leading-icon="tabler:brand-github"
          to="https://github.com/oxyyz/cvly"
          target="_blank"
          >GitHub</UButton
        >
      </div>
    </div>
    <div
      class="absolute bottom-10 translate-x-1/2 right-1/2 flex items-center gap-x-3"
    >
      <UTooltip
        v-for="value in socials"
        :key="value.text"
        :text="value.text"
        :content="{
          align: 'center',
          side: 'top',
          sideOffset: 8,
        }"
      >
        <UButton
          size="sm"
          :leading-icon="value.icon"
          :to="value.url"
          target="_blank"
        />
      </UTooltip>
    </div>
  </div>
</template>
