<template>
  <div class="tags-input-container">
    <div class="tag" v-for="(tag, index) in tags" :key="'tag'+index">
      <span v-if="activeTag !== index" @click="activeTag = index">{{ tag }}</span>
      <input v-else 
            v-model="tags[index]" 
            v-focus 
            :style="{'width': tag.length + 'ch'}" 
            @keyup.enter="activeTag = null" 
            @blur="activeTag = null" />
      <span @click="removeTag(index)"><i class="fas fa-times-circle"></i></span>
    </div>
    <input v-model="tagValue" @keyup.enter="addTag">
  </div>
</template>

<script>
  export default {
    data: () => {
      return {
        tagValue: '',
        tags: [],
        activeTag: null
      }
    },
    methods: {
      addTag() {
        if(!this.tagValue == '')
          this.tags.push(this.tagValue);
        
        this.tagValue = '';
      },
      removeTag(index) {
        this.tags.splice(index, 1);
      }
    },
    directives: {
      focus: {
        inserted: (el) => {
          el.focus()
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .tags-input-container {
    width: 100%;
    max-width: 600px;
    padding: 10px;
    background-color: rgba($color: #ffffff, $alpha: .7);
    
    input {
      width: 100%;
      padding: 0;
      margin: 0;
      border: 0;
      outline: none;
      background-color: transparent;
      font-size: 1rem;
    }

    .tag {
      float: left;
      padding: 3px 5px;

      display: flex;
      justify-content: center;
      cursor: pointer;

      &:hover {
        background-color: #57c340;
        border-radius: 5px;
      } 

      span:first-child {
        margin-right: 8px;
      }  

      svg {
        color: #666;

        &:hover {
          color: #333;
        }
      }     
    }
  }
</style>