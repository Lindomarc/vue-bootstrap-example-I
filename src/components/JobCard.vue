<template>
    <div>
    <b-col>
      <b-card 
      :title="name" 
      img-src="https://picsum.photos/600/300/?image=25"
      img-alt="job-info"
      img-top
      tag="article"
      style="max-width:20rem"
      footer="Card Footer"
      class="mb-2">
        <b-card-text>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iste, aperiam!</b-card-text  >
        <b-button variant="primary">Apply</b-button>
      </b-card>
    </b-col>
    </div>
</template>

<script>
export default {
  props:["name"]
    
}
</script>

<style lang="scss">

</style>