<template>
 
 <v-dialog v-model="show" max-width="600px">
    <v-card style="height:200px ;">
      <div style="padding-left: 20px;
        padding-top: 5px;">
      <div>
        <!-- {{ NoteData.id }} -->
         {{ NoteData.title }}
        <input type="text" v-model="title" />
      </div>
      <div>
        {{ NoteData.description }}
        <input type="text" v-model="description" />
        
      </div>
      </div>
      <div class="note_ic">
            <NoteIcons v-bind:NoteObject="NoteData"></NoteIcons>
          </div>
 
      <div class="cls_btn">
      <v-card-actions>
        <v-btn small color="white" elevation="0" @click.stop="show = false" @click="submit"
          >Close</v-btn
        >
      </v-card-actions>
      </div>
    </v-card>
  </v-dialog>
</template>

<script>
import NoteService from "@/services/userService/NoteService";
import NoteIcons from "./IconNote.vue";
export default {
  name: "DialogueNote",
  components: { NoteIcons },
  data() {
    return {
      dialog: false,
      
      title: this.NoteData.title,
      description: this.NoteData.description,
    };
  },
  props: {
    value: Boolean,
    NoteData: {},
    
  },
  methods: {
    submit() {
      console.log("calling submit function");
      console.log(this.title);
      console.log(this.description);
      let reqData = {
        id:this.NoteData.id,
        title: this.title,
        description: this.description,
      };

      console.log(reqData);
      NoteService.prototype
        .UpdateNotes(reqData)
        .then((responce) => {
          console.log(responce);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  computed: {
    show: {
      get() {
        return this.value;
      },
      set(value) {
         this.$emit("input", value);
      },
    },
  },
  title: {
    get() {
      return this.NoteData.title;
    },
    set(value) {
      this.$emit("input", value);
    },
  },
  description: {
    get() {
      return this.NoteData.description;
    },
    set(value) {
      this.$emit("input", value);
    },
  },
  // mounted() {
   
  //   this.title=this.NoteData.title
  //   this.description=this.NoteData.description
  // }
};
</script>
<style scoped>
.cls_btn {
  padding-left: 500px;
  margin-top: -50px;
}
.note_ic {
  display: flex;
  flex-direction: row;
  /* justify-content: space-between; */
  padding-left: 10px;
  padding-right: 100px;
  gap: 18px;
  margin-top: 90px;
  margin-right: 10px;
}
</style>
