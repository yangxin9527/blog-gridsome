<template>
  <Layout>
    <template>
      <div class="container">
        <div class="journal-header">
          <h1 class="journal-title">{{$page.post.title}}</h1>
          <div class="journal-meta">
            <div class="journal-author" v-if="$page.post.user">
              <span class="label">Author</span
              ><span class="author-name">{{ $page.post.user.username }}</span>
            </div>
            <div class="journal-date">
              <span class="label">Date</span>
              <div>{{time}}</div>
            </div>
            <div class="journal-time">
              <span class="label">Time</span><span>{{$page.post.needTime}} read</span>
            </div>
          </div>
        </div>
        <article>
          <img
              v-if="$page.post.cover"
              class="mar10"
              :src="GRIDSOME_API_URL+$page.post.cover.url"

          />
            <div class="col-lg-8 col-md-10 mx-auto" v-html="mdToHtml($page.post.content)" >
              </div>
        </article>
      </div>
    </template>
  </Layout>
</template>
<page-query>
query($id:ID!){
  post:strapiPost(id:$id){
    id
    title
    content
    published_at
    cover{
      url
    }
    user{
      username
    }
    needTime
  }
}
</page-query>

<script>
import MarkdownIt from 'markdown-it';
import dayjs from 'dayjs'
const md = new MarkdownIt();
export default {
    name:'PostPage',
  metaInfo(){
    return{
      title:this.$page.post.title
    }
  },
  methods:{
    mdToHtml(markdown){
      return md.render(markdown)
    }
  },
  computed:{
    time(){
      return dayjs(this.$page.post.published_at).format('YYYY-MM-DD')
    }
  },
  mounted(){
      console.log()
  }
};
</script>

<style>
.mar10{
  margin: 10px;
}
</style>