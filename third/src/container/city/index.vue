<template>
  <div>
    <h1>三级联动</h1>
    <div class="input">
      <select @click="add()">
        <option v-for="(item,ind) in cityList " :value="item.name" :key="ind">{{item.name}}</option>
      </select>
      <select @click="adds()" aria-placeholder="请选择">
        <option v-for="(item,ind) in twice " :value="item.name" :key="ind">{{item.name}}</option>
      </select>
      <select aria-placeholder="请选择">
        <option v-for="(item,ind) in third " :value="item.name" :key="ind">{{item}}</option>
      </select>
    </div>
  </div>
</template>

<script>
import { mapState } from "vuex";
export default {
  data() {
    return {
      twice: [],
      third: []
    };
  },
  computed: {
    ...mapState({
      cityList: state => state.city
    })
  },
  mounted() {
    this.$store.dispatch("city");
  },
  methods: {
    add() {
      this.cityList.map(i => {
        if (i.name === event.target.value) {
          this.twice = i.city;
        }
      });
    },
    adds() {
      this.twice.map(i => {
        this.third = i.area;
      });
    }
  }
};
</script>
<style scoped  lang="">
select {
  width: 80px;
  height: 30px;
}
</style>