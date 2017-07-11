<!-- http://www.treejs.cn/v3/api.php -->
<template>
  <ul id='tree' class='ztree'>
  </ul>
</template>

<script>
export default {
  mounted () {
    var zNodes = [
      { id: 1, pId: 0, name: 'AnYang', open: true },
      { id: 101, pId: 1, name: 'AnYang_1' },
      { id: 102, pId: 1, name: 'AnYang_2' },
      { id: 103, pId: 1, name: 'AnYang_3' },
      { id: 104, pId: 1, name: 'AnYang_4' },
      { id: 105, pId: 1, name: 'AnYang_5' },
      { id: 2, pId: 0, name: 'Seoul', open: true },
      { id: 201, pId: 2, name: 'Seoul_1' },
      { id: 202, pId: 2, name: 'Seoul_2' },
      { id: 203, pId: 2, name: 'Seoul_3' },
      { id: 204, pId: 2, name: 'Seoul_4' },
      { id: 205, pId: 2, name: 'Seoul_5' }
    ]

    var setting = {
      view: {
        dblClickExpand: true,
        showLine: true,
        showIcon: false,
        selectedMulti: false
      },
      data: {
        simpleData: {
          enable: true,
          idKey: 'id',
          pIdKey: 'pId',
          rootPId: ''
        }
      }
    }

    $.fn.zTree.init($('#tree'), setting, zNodes);
    var zTree = $.fn.zTree.getZTreeObj('tree');
    zTree.selectNode(zTree.getNodeByParam('id', 101));
  }
}
</script>

<style>
ul.ztree {
  height: 100%;
}
</style>