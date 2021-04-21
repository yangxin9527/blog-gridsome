<template>
  <Layout>
    <template>
         <div class="container">
    
        <div class="hero">
          <h1 class="hero-title">{{ web.title }}</h1>
          <h2 class="hero-subtitle">
            {{ web.sub }}
          </h2>
        </div>
        <div c class="projects">
          <div
               class="project" v-for="(post,index) in $page.list.edges" :key="index" v-if="post.node.cover"

          >
            <g-link
              class="project-link"
              :to='`/post/${post.node.id}`'
              ><img
                :src="GRIDSOME_API_URL+post.node.cover.url"
                class="thumbnail g-image g-image--lazy g-image--loaded"

              />
              <h3 c class="project-title">{{ post.node.title }}</h3>
              <div c class="categories">
                <span c class="category" v-for="(tag,index) in post.node.tags">{{ tag.title }}</span>
              </div>
            </g-link>
          </div>
        </div>
      </div>
      <div c>
        <div c class="latest-journals-heading container">
          <span c class="label">Latest and greatest</span>
        </div>
        <div c class="latest-journals">
          <div c class="container">
            <g-link

                v-for="post in this.$page.list.edges"
                :key="post.node.id"
                v-if="!post.node.cover"
                :to='`/post/${post.node.id}`'
              class="journal"
              ><h3 c class="journal-title">
              {{post.node.title}}
              </h3></g-link>
          </div>
        </div>
      </div>
    </template>

  </Layout>
</template>
<page-query>
query {
  list:allStrapiPost(filter: {}) {
      edges {
        node {
        id
        title
        tags{
          title
        }
        cover {
          url
        }
      }
    }
  }

  config:allStrapiConfig{
    edges{
      node{
        title
        sub
        img{
          url
        }
      }
    }
  }
}


</page-query>
<script>

export default {
  data(){
    return{

    }
  },
  computed:{
    web(vm){
      let title='博客'
      let sub='sub'
      try {
        const config = vm.$page.config.edges[0].node;
        title = config.title
        sub = config.sub
      }catch (err){

      }
      return{
        title,
        sub
      }
    }
  }
}
</script>

<style>

</style>