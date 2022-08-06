<template>
  <div class="home">
<GetAllNotes></GetAllNotes>

</div>
</template>

<script>
import GetAllNotes from '@/components/GetAllNotes.vue'
// @ is an alias to /src
export default {
  name: 'GetNote',
  components: {
    GetAllNotes
 
  }
}
</script>
