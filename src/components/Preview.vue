<template>
  <div id="preview">
    <h1>{{ profile.content[0].name.value }}</h1>
    <p>
      {{ profile.content[0].city.value }} | {{ profile.content[0].birthday.value }}
    </p>
    <h1>{{ workHistory.title }}</h1>
    <div v-for="item in workHistory.content">
      <h3>{{ item.company.value }}</h3>
      <p>{{ item.workContent.value}}</p>
    </div>
    <h1>{{ studyHistory.title }}</h1>
    <div v-for="item in studyHistory.content">
      <h3>{{ item.school.value }}</h3>
      <p>{{ item.duration.value}}</p>
      <p>{{ item.degree.value}}</p>
    </div>
  </div>
</template>

<style>
  #preview {
    border: 1px solid #00f;
    min-height: 100px;
  }
</style>

<script>
  export default {
    props: ['profile', 'workHistory', 'studyHistory', 'project', 'awards', 'contacts'],
  }
</script>
