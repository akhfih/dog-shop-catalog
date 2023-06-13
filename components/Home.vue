<!-- Please remove this file from your project -->
<template>
  <div>
    <TheHero></TheHero>
    <BaseHeading>
      <template #heading>The <span>Dog</span> breed</template>
      <template #subheading
        >Siapa yang mencintaiku akan mencintai anjingku juga.</template
      >
    </BaseHeading>
  </div>
</template>

<script>
export default {
  name: 'NuxtHome',
}
</script>
