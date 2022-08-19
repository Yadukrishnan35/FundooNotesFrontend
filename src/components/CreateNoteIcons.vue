<template>
    <div class="ic" style="margin right:10px">
        <img class="ic" style="width:20px" :src="require('../components/Icons/add_alert.svg')" />
        <img style="width:20px" class="ic" :src="require('../components/Icons/person.svg')" />
        <img style="width:20px" class="ic" :src="require('../components/Icons/palette.svg')" />
        <img style="width:20px" margin-right:20px class="ic" :src="require('../components/Icons/image.svg')" />
        <img style="width:20px" class="ic" :src="require('../components/Icons/archive.svg')" />
        <img style="width:20px" class="ic" :src="require('../components/Icons/more_vert.svg')" />
    </div>
</template>

<script>
export default {
    name: "CreateNoteIcons",
}
</script>
<style scoped>
.ic{
 display: flex;
flex-direction: row;
gap:10px;
justify-content: space-around;
padding-bottom: 10px;
padding-top: 5px;
padding-left: 2px;
}
</style>
