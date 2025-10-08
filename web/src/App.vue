<template>
<div>bot: {{ bot_name }}</div>
<div>rating: {{ rating }}</div>
<router-view></router-view>
</template>

<script>

import {ref} from 'vue'
import $ from 'jquery'

export default {
  name: 'App',
  setup() {
    let bot_name = ref("")
    let rating = ref("")

    $.ajax({
      url: "http://localhost:8080/pk/getbotinfo/",
      type: "GET",
      success(resp) {
        bot_name.value = resp.name
        rating.value = resp.rating
      },
    });


    return {
      bot_name,
      rating
    }
  }
}

</script>

<style>

</style>
