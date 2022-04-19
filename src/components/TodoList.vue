<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(a, i) in todoItems" :key="i" class="shadow">

        <i class="checkBtn fas fa-check" aria-hidden="true"></i>

        {{ a }}

        <span class="removeBtn" type="button" @click="removeTodo(a, i)">

          <i class="far fa-trash-alt" aria-hidden="true"></i>

        </span>
      </li>
    </transition-group>
  </section>
</template>

<script>
export default {
  methods:{
    removeTodo(a, i){
      this.$emit('removeTodo', a, i);
    }
  },
  props:{
    todoItems : Array,
  }
};
</script>

<style scoped>
  ul{
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }

  li{
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }

  .checkBtn{
    line-height: 45px;
    color: #62acde;
    margin-right: 10px;
  }

  .removeBtn{
    margin-left: auto;
    color: #de4343;
  }

  .list-enter-active, .list-leave-active{
    transition: all 1s;
  }

  .list-enter, .list-leave-to{
    opacity: 0;
    transform: translateY(30px);
  }
</style>>
</style>