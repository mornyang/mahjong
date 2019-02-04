<template>
  <div id="app">
    <p>{{ hand }}</p>
    <el-row>
      <el-switch
        v-model="dealer"
        active-text="庄家"
        inactive-text="子家">
      </el-switch>
    </el-row>
    <el-row>
      <el-switch
        v-model="rong"
        active-text="荣和"
        inactive-text="自摸">
      </el-switch>
    </el-row>
    <el-row class="handLine">
      <div>
        <span>手牌：</span>
        <span v-for="item in hand" :key=item><input type="button" :class=item class="mahjong" @click="removeSelf(item)"></span>
        <el-button size="mini" @click="clear()">清空</el-button>
      </div>
    </el-row>
    <span v-for="item in zList" :key=item><input type="button" :class=item class="mahjong blank-right" @click="addMahjong(item)"></span><br>
    <span v-for="item in mList" :key=item><input type="button" :class=item class="mahjong blank-right" @click="addMahjong(item)"></span><br>
    <span v-for="item in pList" :key=item><input type="button" :class=item class="mahjong blank-right" @click="addMahjong(item)"></span><br>
    <span v-for="item in sList" :key=item><input type="button" :class=item class="mahjong blank-right" @click="addMahjong(item)"></span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      dealer: true,
      rong: true,
      zList: [
        'z1', 'z2', 'z3', 'z4', 'z5', 'z6', 'z7'
      ],
      mList: [
        'm1', 'm2', 'm3', 'm4', 'm5', 'm6', 'm7', 'm8', 'm9', 'me'
      ],
      pList: [
        'p1', 'p2', 'p3', 'p4', 'p5', 'p6', 'p7', 'p8', 'p9', 'pe'
      ],
      sList: [
        's1', 's2', 's3', 's4', 's5', 's6', 's7', 's8', 's9', 'se'
      ],
      hand: [],
      paly: [],
      hu: []
    }
  },
  methods: {
    addMahjong (id) {
      let same = this.hand.filter((item) => {
        return item === id
      })
      if (same.length === 4) {
        this.$message({
          message: '这种牌到达上限',
          type: 'warning'
        })
        return
      }
      if (this.hand.length === 13) {
        this.$message({
          message: '手牌到达上限',
          type: 'warning'
        })
        return
      }
      this.hand.push(id)
      this.hand.sort()
    },
    removeSelf (id) {
      let index = this.hand.indexOf(id)
      if (index > -1) {
        this.hand.splice(index, 1)
      }
    },
    clear () {
      this.hand = []
    }
  }
}
</script>

<style>
  .mahjong{
    width:24px;
    height:36px;
    border:0;
  }
  .blank-right{
    margin-right: 5px;
  }
  .z1{
    background:url(./assets/t_real/0j1.png) no-repeat left top
  }
  .z2{
    background:url(./assets/t_real/0j2.png) no-repeat left top
  }
  .z3{
    background:url(./assets/t_real/0j3.png) no-repeat left top
  }
  .z4{
    background:url(./assets/t_real/0j4.png) no-repeat left top
  }
  .z5{
    background:url(./assets/t_real/0j5.png) no-repeat left top
  }
  .z6{
    background:url(./assets/t_real/0j6.png) no-repeat left top
  }
  .z7{
    background:url(./assets/t_real/0j7.png) no-repeat left top
  }
  .m1{
    background:url(./assets/t_real/0m1.png) no-repeat left top
  }
  .m2{
    background:url(./assets/t_real/0m2.png) no-repeat left top
  }
  .m3{
    background:url(./assets/t_real/0m3.png) no-repeat left top
  }
  .m4{
    background:url(./assets/t_real/0m4.png) no-repeat left top
  }
  .m5{
    background:url(./assets/t_real/0m5.png) no-repeat left top
  }
  .m6{
    background:url(./assets/t_real/0m6.png) no-repeat left top
  }
  .m7{
    background:url(./assets/t_real/0m7.png) no-repeat left top
  }
  .m8{
    background:url(./assets/t_real/0m8.png) no-repeat left top
  }
  .m9{
    background:url(./assets/t_real/0m9.png) no-repeat left top
  }
  .me{
    background:url(./assets/t_real/0me.png) no-repeat left top
  }
  .p1{
    background:url(./assets/t_real/0p1.png) no-repeat left top
  }
  .p2{
    background:url(./assets/t_real/0p2.png) no-repeat left top
  }
  .p3{
    background:url(./assets/t_real/0p3.png) no-repeat left top
  }
  .p4{
    background:url(./assets/t_real/0p4.png) no-repeat left top
  }
  .p5{
    background:url(./assets/t_real/0p5.png) no-repeat left top
  }
  .p6{
    background:url(./assets/t_real/0p6.png) no-repeat left top
  }
  .p7{
    background:url(./assets/t_real/0p7.png) no-repeat left top
  }
  .p8{
    background:url(./assets/t_real/0p8.png) no-repeat left top
  }
  .p9{
    background:url(./assets/t_real/0p9.png) no-repeat left top
  }
  .pe{
    background:url(./assets/t_real/0pe.png) no-repeat left top
  }
  .s1{
    background:url(./assets/t_real/0s1.png) no-repeat left top
  }
  .s2{
    background:url(./assets/t_real/0s2.png) no-repeat left top
  }
  .s3{
    background:url(./assets/t_real/0s3.png) no-repeat left top
  }
  .s4{
    background:url(./assets/t_real/0s4.png) no-repeat left top
  }
  .s5{
    background:url(./assets/t_real/0s5.png) no-repeat left top
  }
  .s6{
    background:url(./assets/t_real/0s6.png) no-repeat left top
  }
  .s7{
    background:url(./assets/t_real/0s7.png) no-repeat left top
  }
  .s8{
    background:url(./assets/t_real/0s8.png) no-repeat left top
  }
  .s9{
    background:url(./assets/t_real/0s9.png) no-repeat left top
  }
  .se{
    background:url(./assets/t_real/0se.png) no-repeat left top
  }
</style>
