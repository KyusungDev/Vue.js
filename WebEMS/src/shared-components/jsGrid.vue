<template>
  <div id='jsGrid'>
  </div>
</template>

<script>
export default {
  mounted() {
    var clients = [
      { 'index': 1, 'type': 'ALM', 'sev': 'CR', 'sa': 'SA', 'target': 'SITE1 / CET-10448 / ANyang_4', 'ip': '2.0.5.1', 'aid': 'GIUA-2-3', 'cause': 'OPTIC_OUT', 'reason': '---', 'datetime': '2017-07-11 10:27:45' },
      { 'index': 2, 'type': 'ALM1', 'sev': 'CR', 'sa': 'SA', 'target': 'SITE1 / CET-10448 / ANyang_4', 'ip': '2.0.5.1', 'aid': 'GIUA-2-3', 'cause': 'OPTIC_OUT', 'reason': '---', 'datetime': '2017-07-11 10:27:45' },
      { 'index': 3, 'type': 'ALM2', 'sev': 'CR', 'sa': 'SA', 'target': 'SITE1 / CET-10448 / ANyang_4', 'ip': '2.0.5.1', 'aid': 'GIUA-2-3', 'cause': 'OPTIC_OUT', 'reason': '---', 'datetime': '2017-07-11 10:27:45' },
      { 'index': 4, 'type': 'ALM3', 'sev': 'CR', 'sa': 'SA', 'target': 'SITE1 / CET-10448 / ANyang_4', 'ip': '2.0.5.1', 'aid': 'GIUA-2-3', 'cause': 'OPTIC_OUT', 'reason': '---', 'datetime': '2017-07-11 10:27:45' },
      { 'index': 5, 'type': 'ALM4', 'sev': 'CR', 'sa': 'SA', 'target': 'SITE1 / CET-10448 / ANyang_4', 'ip': '2.0.5.1', 'aid': 'GIUA-2-3', 'cause': 'OPTIC_OUT', 'reason': '---', 'datetime': '2017-07-11 10:27:45' }
    ];

    var countries = [
      { Name: '', Id: 0 },
      { Name: 'United States', Id: 1 },
      { Name: 'Canada', Id: 2 },
      { Name: 'United Kingdom', Id: 3 }
    ];

    $('#jsGrid').jsGrid({
      width: '100%',
      height: '100%',
      inserting: false,
      sorting: true,
      paging: false,
      data: clients,
      fields: [
        { type: 'number', name: 'index', title: '번호', width: 30, align: 'center' },
        { type: 'text', name: 'type', title: '타입', width: 30, align: 'center' },
        { type: 'text', name: 'sev', title: '등급', width: 30, align: 'center' },
        { type: 'text', name: 'sa', title: 'SA', width: 20, align: 'center' },
        { type: 'text', name: 'target', title: '그룹/장비/노드', width: 150, align: 'center' },
        { type: 'text', name: 'ip', title: 'IP 주소', width: 50, align: 'center' },
        { type: 'text', name: 'aid', title: '카드/슬롯/포트/서비스 (AID)', width: 100, align: 'center' },
        { type: 'text', name: 'cause', title: '발생 원인', width: 130, align: 'center' },
        { type: 'text', name: 'reason', title: '설명', width: 130, align: 'center' },
        { type: 'text', name: 'datetime', title: '발생 시각', width: 80, align: 'center' }
      ]
    });
  },
  methods: {
    onResized: function() {
      $('#jsGrid').jsGrid('refresh');
    }
  },
  created () {
    this.$parent.$on('resized', this.onResized);
  }
}
</script>

<style>
.jsgrid-cell {
  padding: 0.3em 0.3em;
}

.jsgrid-header-cell {
  padding: .4em .4em;
}
</style>