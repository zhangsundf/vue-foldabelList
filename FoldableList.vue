<template>
  <div class="foldable-list" v-if="toggle">
    <header>
      <p class="title">
        我是title
      </p>
      <p class="toogle" @click="toggle = !toggle">
        {{ toggle ? '收起' : '展开' }}
      </p>
    </header>
    <div class="list" v-if="toggle">
      <p class="title dark-bg">
        <span v-for="(title, inx) in list.title">
          {{ title }}
        </span>
      </p>
      <ul class="list-main">
        <li
          v-for="(item, index) in list.list"
          :class="{ 'dark-bg': index % 2 === 1 }"
        >
          <span v-for="(val, inx) in list.title" v-else>
            {{ item[val] }}
          </span>
        </li>
      </ul>
    </div>
  </div>
  <div class="foldable" v-else>
    <header>
      <p class="title">
        我是title
      </p>
      <p class="toogle" @click="toggle = !toggle">
        {{ toggle ? '收起' : '展开' }}
      </p>
    </header>
  </div>
</template>
<script lang="ts">
import { Component, Vue, Prop } from 'com/vue-ts'

@Component
export default class FoldableList extends Vue {
  @Prop() list: any
  toggle: boolean = true
}
</script>

<style lang="scss" scoped>
.foldable {
  height: 30px;
  background: var(--block);
}
.foldable,
.foldable-list {
  text-align: left;
  font-size: 14px;
  font-family: PingFangSC-Semibold;
  background: var(--block);
  header {
    padding: 0 20px;
    border-top: 3px solid var(--background);
    line-height: 30px;
    display: flex;
    .title {
      flex: 1;
    }
    .toggle {
      width: 40px;
    }
  }
}
.foldable-list {
  flex: 1;
  display: flex;
  flex-direction: column;
  div.list {
    flex: 1;
    display: flex;
    flex-direction: column;
    overflow: hidden;
    p.title {
      color: var(--text-color);
      line-height: 30px;
      span {
        display: inline-block;
        width: 11.11%;
        padding-left: 20px;
        box-sizing: border-box;
        border-right: 1px solid var(--divide-color);
      }
    }
    .list-main {
      flex: 1;
      overflow: auto;
      li {
        line-height: 30px;
        span {
          padding-left: 20px;
          display: inline-block;
          width: 11.11%;
          box-sizing: border-box;
          border-right: 1px solid var(--divide-color);
        }
        &:last-child {
          border-bottom: 1px solid var(--divide-color);
        }
      }
    }
  }
}

.dark-bg {
  background: var(--default-bg);
}
.linkText {
  color: red;
}
</style>
