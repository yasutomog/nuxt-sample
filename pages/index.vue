<template>
  <!--<div>-->
    <!--<div v-for="item in items">-->
      <!--<nuxt-link :to="'careers/' + item.id">-->
        <!--<h2>-->
          <!--{{ item.name }}-->
        <!--</h2>-->
      <!--</nuxt-link>-->
    <!--</div>-->
    <!--<client-only>-->
      <!--<form name="contact" method="POST">-->
        <!--<input type="hidden" name="form-name" value="contact">-->
        <!--<p>-->
          <!--<label>Your Name: <input type="text" name="name" placeholder="後藤"></label>-->
        <!--</p>-->
        <!--<p>-->
          <!--<label>Message: <textarea name="message" placeholder="テストメッセージ"></textarea></label>-->
        <!--</p>-->
        <!--<p>-->
          <!--<button type="submit">Send</button>-->
        <!--</p>-->
      <!--</form>-->
    <!--</client-only>-->
  <!--</div>-->
  <form name="contact" method="POST" data-netlify="true">
    <p>
      <label>Your Name: <input type="text" name="name" /></label>
    </p>
    <p>
      <label>Your Email: <input type="email" name="email" /></label>
    </p>
    <p>
      <label>Your Role: <select name="role[]" multiple>
        <option value="leader">Leader</option>
        <option value="follower">Follower</option>
      </select></label>
    </p>
    <p>
      <label>Message: <textarea name="message"></textarea></label>
    </p>
    <p>
      <button type="submit">Send</button>
    </p>
  </form>
</template>
<script>
import axios from 'axios'
export default {
  data () {
    return {
      items: []
    }
  },
  async asyncData () {
    const { data } = await axios.get(
      'https://yasutomog.microcms.io/api/v1/careers',
      {
        headers: { 'X-API-KEY': process.env.API_KEY }
      }
    )
    return {
      items: data.contents
    }
  }
}
</script>
