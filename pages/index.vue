<template>
  <section class="container">
      <mytable/>
  </section>
</template>

<script>
import Vue from 'vue'
import Buefy from 'buefy'
import 'buefy/lib/buefy.css'

Vue.use(Buefy)

Vue.component('mytable', {
  data () {
    return {
      slotsType: 'default',
      tableData: [
        {i: '1', b: 'b1', c: 'c1', d: 'd1', e: 'e1'},
        {i: '2', b: 'b2', c: 'c2', d: 'd2', e: 'e2'},
        {i: '3', b: 'b3', c: 'c3', d: 'd3', e: 'e3'}
      ]
    }
  },
  methods: {
    getDefaultScopedSlots (props) {
      const slots = [
        <b-table-column field="i" label="I" width="40">
          { props.row.i }
        </b-table-column>
      ]

      // We construct different columns on specific condition
      //
      // In the further situation,
      // the columns could be dynamically generated.
      if (this.slotsType === 'default') {
        slots.push([
          <b-table-column field="b" label="B" width="40">
            { props.row.b }
          </b-table-column>,
          <b-table-column field="c" label="C" width="40">
            { props.row.c }
          </b-table-column>,
          <b-table-column field="d" label="D" width="40">
            { props.row.d }
          </b-table-column>
        ])
      } else {
        slots.push([
          <b-table-column field="e" label="E" width="40">
            { props.row.e }
          </b-table-column>
        ])
      }

      return slots
    }
  },
  render () {
    return (
      <section class="section">
        <b-switch
          value={ this.slotsType }
          on-input={ (v) => { this.slotsType = v } }
          true-value="alternate"
          false-value="default"
        >
        Columns: [{ this.slotsType === 'default' ? 'I, B, C, D' : 'I, E' }]
        </b-switch>
        <b-table
          data={ this.tableData }
          scopedSlots={{
            default: this.getDefaultScopedSlots,
            empty: () => (<div>Empty.</div>)
          }}
        >
        </b-table>
      </section>
    )
  }
})
</script>
