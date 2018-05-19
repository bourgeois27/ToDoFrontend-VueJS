<template>
  <div>
    <div class="row">
      <app-header></app-header>
    </div>
    <div class="container">
      <app-tasks></app-tasks>
    </div>
    <div class="row">
      <app-footer></app-footer>
    </div>
  </div>
</template>

<script>
import Header from './components/Header';
import Tasks from './components/Tasks';
import Footer from './components/Footer';

export default {
  components: {
    appHeader: Header,
    appTasks: Tasks,
    appFooter: Footer
  }
}
</script>

<style>

</style>
