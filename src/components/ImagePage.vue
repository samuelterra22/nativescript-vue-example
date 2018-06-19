<template>
    <Page class="page">
        <ActionBar title="Image Page" class="action-bar"/>
        <StackLayout class="home-panel">
            <Label textWrap="true" :text="this.post.title" class="h2 description-label"/>

            <Image :src="this.post.thumbnail"/>

            <Button class="button" text="Back" @tap="onButtonTap"/>
        </StackLayout>
    </Page>
</template>

<script>

  export default {
    data () {
      return {}
    },
    props: {
      post: {
        type: Object,
        require: true
      }
    },
    methods: {
      onButtonTap () {
        this.$navigateBack()
      },
    },
  }
</script>
