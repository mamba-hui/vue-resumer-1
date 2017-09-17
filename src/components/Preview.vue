<template>
  <div id="preview">
    <h1>{{ profile.content[0].name.value }}</h1>
    <p>
      {{ profile.content[0].city.value }} | {{ profile.content[0].birthday.value }}
    </p>
    <h1 v-if="filter(workHistory.content).length > 0">{{ workHistory.title }}</h1>
    <div v-for="(item, index) in filter(workHistory.content)" :key="index">
      <h3>{{ item.company.value }}</h3>
      <p>{{ item.workContent.value}}</p>
    </div>
    <h1 v-if="filter(studyHistory.content).length > 0">{{ studyHistory.title }}</h1>
    <div v-for="(item, index) in studyHistory.content" :key="index">
      <h3>{{ item.school.value }}</h3>
      <p>{{ item.duration.value}}</p>
      <p>{{ item.degree.value}}</p>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['profile', 'workHistory', 'studyHistory', 'project', 'awards', 'contacts'],
    methods: {
      filter(items) {
        return  items.filter((item) => {
          let lock = false
          Object.keys(item).forEach((key) => {
            if(item[key].value) {
              lock = true
            }
          })
          return lock
        })
      }
    }
  }
</script>

<style>
  #preview {
    border: 1px solid #00f;
    min-height: 100px;
  }
</style>


