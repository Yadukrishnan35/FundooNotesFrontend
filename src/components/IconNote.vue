<template>
  <div class="ic" style="margin right:10px">
    <img
      class="ic"
      style="width: 20px"
      :src="require('../components/Icons/add_alert.svg')"
    />
    <img
      style="width: 20px"
      class="ic"
      :src="require('../components/Icons/person.svg')"
    />
        <ColourMenu v-bind:noteId="NoteObject"></ColourMenu>   

        <!-- <ColourMenu v-bind:value="[NoteObject.id, NoteObject.colour]"></ColourMenu>  -->
    <!-- <img
      @click="colourNote()"
      style="width: 20px"
      class="ic"
      :src="require('../components/Icons/palette.svg')"
    /> -->
    <img
      style="width: 20px"
      margin-right:20px
      class="ic"
      :src="require('../components/Icons/image.svg')"
    />
    <img
      @click="archiveNote()"
      style="width: 20px"
      class="ic"
      :src="require('../components/Icons/archive.svg')"
    />
    <!-- <img style="width:20px" class="ic" :src="require('../components/Icons/more_vert.svg')" /> -->
    <MoreVertMenu v-bind:noteId="NoteObject.id"></MoreVertMenu>
    
    <!-- <more-vert-menu></more-vert-menu> -->
    <!-- <MoreVertMenu></MoreVertMenu> -->
  </div>
</template>

<script>
import NoteService from "@/services/userService/NoteService";
import MoreVertMenu from "./MoreVertMenu.vue";
import ColourMenu from "./ColourMenu.vue";


export default {
  name: "NoteIcons",
  components: { MoreVertMenu, ColourMenu },
  
  props: {
    NoteObject: {},
    colour:[]
  },
  //archive method
  methods: {
    archiveNote() {
      console.log("Archive notes calling", this.NoteObject);

      let reqData = {
        // id:this.NoteData.id,
        id: this.NoteObject.id,
        
      };

      console.log(this.NoteObject.id);
      NoteService.prototype
        .archiveNote(reqData)
        .then((response) => {
          console.log(response);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  };

// //     colourNote() {
// //       console.log("Colour note is calling", this.NoteObject);

// //       let reqData = {
// //         // id:this.NoteData.id,
// //         id: this.NoteObject.id,
// //       };

// //       console.log(this.NoteObject.id);
// //       NoteService.prototype
// //         .colourNote(reqData)
// //         .then((response) => {
// //           console.log(response);
// //         })
// //         .catch((error) => {
// //           console.log(error);
// //         });
// //     },
// //   },
// };
</script>
<style scoped>
.ic {
  display: flex;
  flex-direction: row;
  gap: 10px;
  justify-content: space-around;
  padding-bottom: 10px;
  padding-top: 5px;
  padding-left: 2px;
}
</style>
