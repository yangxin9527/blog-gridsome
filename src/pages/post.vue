<template>
  <Layout>
    <template>
      <div  class="container">
        <div  class="journal-hero">
          <h1  class="journal-header">
            a wise person once said...
          </h1>
        </div>
      </div>
      <g-link
        :to='`/post/${post.node.id}`'
        class="journal-post"
        v-for="post in this.$page.posts.edges"
        :key='post.node.id'
        ><div  class="container journal">
          <h2  class="journal-title">
            {{post.node.title}}
          </h2>
          <p  class="journal-excerpt">
           {{post.node.subtitle}}
          </p>
        </div>
      </g-link>
    </template>
  </Layout>
</template>
<page-query>
query{
  posts: allStrapiPost{
    edges{
      node{
        id
        title

      }
    }
  }
}
</page-query>


<script>
export default {
  mounted(){
 
  }
};
</script>

<style>
</style>