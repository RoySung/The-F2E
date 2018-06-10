<template>
  <div class="todolist-page">
    <div class="header">
      <div class="tabs">
        <div class="tab active"><label>My Tasks</label></div>
        <div class="tab"><label>In Progress</label></div>
        <div class="tab"><label>Completed</label></div>
      </div>
    </div>
    <div class="content">
      <div class="add-task-btn"><i class="fas fa-plus"></i>Add Task</div>
      <div class="list__wrap">
        <div class="list__item">
          <div class="title-wrap">
            <div class="name-wrap">
              <div class="checkbox-input">
                <input type="checkbox">
                <i class="fa fa-check" aria-hidden="true"></i>
              </div>
              <!-- <div class="name-text">Type Something Here…</div> -->
              <input type="text" class="name-input" placeholder="Type Something Here…">
            </div>
            <div class="btn-content">
              <a class="btn top-btn top-btn--active"><i class="fas fa-2x fa-star"></i></a>
              <a class="btn edit-btn edit-btn--active"><i class="fas fa-2x fa-pencil-alt"></i></a>
            </div>
          </div>
          <div class="content-wrap content-wrap--editing">
            <div class="content-wrap__content">
              <form class="form-wrap">
                <div class="field deadline-field">
                  <label><i class="far fa-calendar-alt"></i>Deadline</label>
                  <datetime input-class="date-picker" type="datetime" placeholder="Select DateTime" v-model="datetime"></datetime>
                </div>
                <div class="field comment-field">
                  <label><i class="far fa-comment"></i>Comment</label>
                  <textarea placeholder="Type your memo here…"></textarea>
                </div>
              </form>
            </div>
            <div class="content-wrap__bottom-wrap">
              <div class="bottom-btn cancel-btn">Cancel</div>
              <div class="bottom-btn confirm-btn">Ok</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { Datetime } from 'vue-datetime';
  export default {
    components: {
      Datetime
    }
  }
</script>

<style lang="sass" src="./style.sass">
</style>
