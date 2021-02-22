<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button @click="handleClick">加算 {{ count }}</button>
    <CopyDocs docs="For a guide and recipes on how to configure / customize this project,"/>
    <RefLinks />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
// import RefLinks from './RefLinks.vue';
import CopyDocs from './CopyDocs.vue';
type Props = {
    msg: string,
    count: number
}


export default defineComponent({
  name: 'HelloWorld',
  components: { CopyDocs },
  props: {
      msg: {
          type: String,
            required: true
      },
      count: {
        type: Number,
        required: true
      },
  },
  emits: ['child-event'],
  setup (props: Props, {emit}) {
      const handleClick = () => {
        emit('child-event',props.count + 1)
      }
      return { handleClick }
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
    padding: 15px;
    font-size: 1.8rem;
}

</style>
