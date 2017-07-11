<template>
  <div id="app">
    <nav class="navbar navbar-default">
      <div class="navbar-header">
        <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#bs-example-navbar-collapse-1" aria-expanded="false">
          <span class="sr-only">Toggle navigation</span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <!--<img src="./assets/brand.png" alt="">-->
      </div>
      <div class="collapse navbar-collapse" id="bs-example-navbar-collapse-1">
        <ul class="nav navbar-nav">
          <li>
            <a href="#">Topology</span>
            </a>
          </li>
          <li>
            <a href="#">Dashboard</a>
          </li>
          <li>
            <a href="#">History</a>
          </li>
        </ul>
        <ul class="nav navbar-nav navbar-right">
          <li>
            <a href="#">Sign Out(admin)</a>
          </li>
          <li>
            <a href="#">Settings</a>
          </li>
          <li>
            <a href="#">Help</a>
          </li>
        </ul>
      </div>
    </nav>
    <div id="page-frame" class="split split-vertical">
      <div id="page-tree" class="split split-horizontal">
        <div class="input-group">
          <input type="text" class="form-control input-sm" placeholder="Search for...">
          <span class="input-group-btn">
            <button class="btn btn-default btn-sm" type="button"><i class="glyphicon glyphicon-search" aria-hidden="true"></i></button>
          </span>
        </div>
        <div class="sidebar-wrapper">
          <z-tree></z-tree>
        </div>
      </div>
      <div id="page-topology" class="split split-horizontal"></div>
    </div>
    <div id="page-grid" class="split split-vertical">
      <js-grid></js-grid>
    </div>
  </div>
</template>

<script>
import ZTree from './shared-components/ZTree'
import jsGrid from './shared-components/jsGrid'

export default {
  components: {
    ZTree,
    jsGrid
  },
  methods: {
    onResized: function() {
      this.$emit('resized');
    }
  },
  mounted: function () {
    Split(['#page-frame', '#page-grid'], {
      direction: 'vertical',
      sizes: [75, 20],
      gutterSize: 2,
      minSize: 100,
      onDragEnd: () => { this.onResized(); }
    })

    Split(['#page-tree', '#page-topology'], {
      sizes: [15, 85],
      minSize: 100,
      gutterSize: 3
    })
  }
}
</script>

<style>
* {
  /*border: 1px solid red;*/
}

html,
body {
  height: 100%;
}

#app {
  height: 100%;
  overflow-y: hidden;
}

.split,
.split-flex {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;

  overflow-y: auto;
  overflow-x: auto;
}

#page-grid {
  overflow-y: hidden;
}

.gutter {
  background-color: #eee;
  background-repeat: no-repeat;
  background-position: 50%;
}

.gutter.gutter-horizontal {
  cursor: ew-resize;
}

.gutter.gutter-vertical {
  cursor: ns-resize;
}

.split.split-horizontal,
.gutter.gutter-horizontal {
  height: 100%;
  float: left;
}

.navbar {
  margin-bottom: 0px;
  border-bottom: 3px solid #e5e5e5;

}

img {
  padding-top: 5px;
}

.navbar-default {
  color: #9e9e9e;
  background-color: #fff;
  height: 52px;
}

.nav>li>a:hover,
.nav>li>a:focus {
  color: #9e9e9e;
  background-color: silver;
}

.navbar-default .navbar-nav>li>a {
  font-weight: bold;
  color: #009688;
}

.navbar-default .navbar-right>li>a {
  font-weight: bold;
  color: #9e9e9e;
}

</style>
