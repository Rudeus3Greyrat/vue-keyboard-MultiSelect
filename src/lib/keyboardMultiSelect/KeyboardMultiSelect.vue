<template>
  <div>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "KeyboardMultiSelect",
  props: {
    rawData: {
      type: Array,
      default: function () {
        return []
      }
    }
  },
  data() {
    return {
      listData: [],
      isShift: false,
      isCtrl: false,
      arr:[]
    }
  },
  watch: {
    listData: {
      handler: function (val) {
        Object.keys(val).forEach(el => {
          val[el].selected ? this.arr[el].elm.setAttribute('style', 'background-color:darkgrey') : this.arr[el].elm.setAttribute('style', 'background-color:none')
        })
        let temp = []
        Object.keys(val).forEach(el => {
          val[el].selected ? temp.push(val[el].value):''
        })
        this.$emit('selectChange',temp)
      },
      deep: true,
      immediate: true
    }
  },
  created() {
    this.keyEvent();
    this.modifyData();
  },
  mounted() {
    this.addClick()
  },
  methods: {
    modifyData() {
      for (let i = 0; i < this.rawData.length; i++) {
        this.listData[i] = {value: this.rawData[i], selected: false}
      }
    },
    addClick() {
      this.arr=this.$slots.default.filter(el=>{return el.tag})
      for (let i = 0; i < this.arr.length; i++) {
        this.arr[i].elm.addEventListener("click", () => {
          this.handleClick(this.listData[i], i)
        })
      }
    },
    keyEvent() {
      const that = this;
      document.onkeydown = function (e) {
        switch (e.code) {
          case 'ShiftLeft':
            that.isShift = true;
            break;
          case 'ShiftRight':
            that.isShift = true;
            break;
          case 'MetaLeft':
            that.isCtrl = true;
            break;
          case 'MetaRight':
            that.isCtrl = true;
            break;
        }
      };
      document.onkeyup = function (e) {
        switch (e.code) {
          case 'ShiftLeft':
            that.isShift = false;
            break;
          case 'ShiftRight':
            that.isShift = false;
            break;
          case 'MetaLeft':
            that.isCtrl = false;
            break;
          case 'MetaRight':
            that.isCtrl = false;
            break;
        }
      };
    },
    handleClick(item, index) {
      if (this.isCtrl) {
        if(item.selected){
          item.selected=false;
        }else{
          item.selected = true;
        }
        this.$set(this.listData, index, item);
        if (this.isShift) {
          const len = Object.keys(this.listData).length;
          let resultIndex = -1;
          for (let i = len - 1; i > -1; i--) {
            if (this.listData[i].selected) {
              if (i !== index) {
                resultIndex = i;
                break;
              }
            }
          }
          if (resultIndex < index) {
            for (let i = resultIndex; i <= index; i++) {
              this.listData[i].selected = true;
            }
          } else {
            for (let i = index; i <= resultIndex; i++) {
              this.listData[i].selected = true;
            }
          }
        }
      } else if (!this.isCtrl && !this.isShift) {
        Object.values(this.listData).forEach(data => {
          data.selected = false;
        });
        item.selected = true
        this.$set(this.listData, index, item);
      }
    }
  }
}
</script>

<style scoped>
</style>
