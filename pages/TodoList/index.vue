<template>
  <div v-if="list" class="todolist-page">
    <div class="header">
      <div class="tabs">
        <div :class="{ active: isTasksState }" class="tab" @click="changeTasksState"><label>My Tasks</label></div>
        <div :class="{ active: isProgressState }" class="tab" @click="changeProgressState"><label>In Progress</label></div>
        <div :class="{ active: isCompletedState }" class="tab" @click="changeCompletedState"><label>Completed</label></div>
      </div>
    </div>
    <div class="content">
      <div class="add-task-btn" @click="newItem"><i class="fas fa-plus"></i>Add Task</div>
      <div class="list__wrap">
        <div class="list__item" v-for="(item, index) in sortedList" :key="`item-${index}`">
          <div class="title-wrap">
            <div class="name-wrap">
              <div class="checkbox-input">
                <input v-model="item.isCompleted" type="checkbox">
                <i class="fa fa-check" aria-hidden="true"></i>
              </div>
              <input v-if="editingIndex == index" type="text" class="name-input" placeholder="Type Title ..." v-model="item.title">
              <div v-else :class="{ 'name-text--completed': item.isCompleted }" class="name-text" v-html="item.title"></div>
            </div>
            <div class="btn-content">
              <a :class="{ 'top-btn--active': item.isTop }" class="btn top-btn" @click="item.isTop = !item.isTop"><i class="fas fa-2x fa-star"></i></a>
              <a :class="{ 'edit-btn--active': editingIndex == index }" class="btn edit-btn" @click="handleEditing(index)"><i class="fas fa-2x fa-pencil-alt"></i></a>
            </div>
          </div>
          <div :class="{ 'content-wrap--editing': editingIndex == index }" class="content-wrap">
            <div class="content-wrap__content">
              <form class="form-wrap">
                <div class="field deadline-field">
                  <label><i class="far fa-calendar-alt"></i>Deadline</label>
                  <datetime input-class="date-picker" type="datetime" placeholder="Select DateTime" v-model="item.deadline"></datetime>
                </div>
                <div class="field comment-field">
                  <label><i class="far fa-comment"></i>Comment</label>
                  <textarea placeholder="Type your memo here…" v-model="item.comment"></textarea>
                </div>
              </form>
            </div>
            <div class="content-wrap__bottom-wrap">
              <div class="bottom-btn cancel-btn" @click="cancelChange(index)"><i class="fas fa-times">Cancel</i></div>
              <div class="bottom-btn confirm-btn" @click="saveItem(index)"><i class="fas fa-plus">Save</i></div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { Datetime } from 'vue-datetime';

  // localstorage key
  const TODOLIST = 'todolist'
  // state
  const TASKS = 'tasks'
  const INPROGRESS = 'in progress'
  const COMPLETED = 'completed'
  export default {
    name: 'TodoList',
    data() {
      return {
        state: TASKS,
        list: [],
        backupItem: null,
        editingIndex: null
      }
    },
    computed: {
      sortedList: {
        get() {
          if (!this.list.length) return []
          const list = [...this.list]
          const sortedList = list.sort((a, b) => b.isTop - a.isTop)
          if (this.isCompletedState) {
            return sortedList.filter(item => item.isCompleted)
          } else {
            return sortedList
          }
        },
        set(list) {
          this.list = list
        }
      },
      editingItem() {
        return this.editingIndex != null ? this.sortedList[this.editingIndex] : null
      },
      isTasksState() {
        return this.state == TASKS
      },
      isProgressState() {
        return this.state == INPROGRESS
      },
      isCompletedState() {
        return this.state == COMPLETED
      }
    },
    watch: {
      sortedList: {
        handler(list) {
          window.localStorage.setItem(TODOLIST, JSON.stringify(list))
        },
        deep: true
      }
    },
    methods: {
      changeTasksState() {
        this.state = TASKS
      },
      changeProgressState() {
        this.state = INPROGRESS
      },
      changeCompletedState() {
        this.state = COMPLETED
      },
      handleEditing(index) {
        if (this.editingIndex == null) {
          this.editingIndex = index
          this.backupItem = Object.assign({}, this.sortedList[index])
        } else {
          this.cancelChange(index)
        }
      },
      saveItem(index) {
        this.editingIndex = null
        this.backupItem = null
        this.sortedList[index].isNew = false
      },
      cancelChange(index) {
        if (this.sortedList[index].isNew) {
          const list = [...this.sortedList]
          list.shift()
          this.sortedList = list
        } else {
          this.sortedList[index] = this.backupItem
          this.backupItem = null
        }
        this.editingIndex = null
      },
      newItem() {
        if (this.editingItem && this.editingItem.isNew) return
        const item = {
          title: '',
          deadline: new Date().toISOString(),
          comment: '',
          isNew: true,
          isTop: false,
          isCompleted: false
        }
        const list = [...this.sortedList]
        list.unshift(item)
        this.sortedList = list
        this.editingIndex = 0
      }
    },
    mounted() {
      let list = window.localStorage.getItem(TODOLIST)
      list = list ? JSON.parse(list) : []
      this.list = list
    },
    components: {
      Datetime
    }
  }
</script>

<style lang="sass" src="./style.sass">
</style>
