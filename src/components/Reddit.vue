<template>
    <Page class="page">
        <ActionBar title="Reddit" class="action-bar"/>
        <ScrollView>
            <StackLayout class="home-panel">
                <!--Add your page content here-->


                <ListView class="list-group" for="post in posts" @itemTap="onItemTap" style="height:2000px">
                    <v-template>
                        <FlexboxLayout flexDirection="row" class="list-group-item">
                            <Image :src="post.data.thumbnail" class="thumb img-circle"/>
                            <Label :text="post.data.title" class="list-group-item-heading" style="width: 60%"/>
                        </FlexboxLayout>
                    </v-template>
                </ListView>

            </StackLayout>
        </ScrollView>
    </Page>
</template>

<script>
  import ImagePage from './ImagePage'
  import axios from 'axios'

  export default {
    data () {
      return {
        posts: []
      }
    },
    methods: {
      onItemTap: function (args) {
        console.log('Item with index: ' + args.item.data.title + ' tapped')
        this.$navigateTo(ImagePage, {
          context: {
            propsData: {
              post: args.item.data
            }
          }
        })
      },
    },
    mounted () {
      /*
      fetch('https://www.reddit.com/r/aww.json')
        .then(response => response.json())
        .then(data => {
          this.posts = data.data.children
        })
        */
      axios.get('https://www.reddit.com/r/aww.json')
        .then(response => {
          this.posts = response.data.data.children
        })
    },
  }
</script>
