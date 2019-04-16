<template>
  <div id="app">
    <h1>Table example: simple phonebook</h1>
    <table-cmp :value="phonebookList"
      :columns="columns"
      :actions="actions"
      :selection="selected"
      :sortData="sortData"
      @sort="sortBy"
      @select="select"
      @action-edit="editItem"
      @action-delete="deleteItem">
    </table-cmp>
    <div>
      <p><strong>Item to edit</strong>: <i>{{ item ? item : 'neither for now...' }}</i></p>
    </div>
    <div>
      <p><strong>Selected items</strong>: <i>{{ selected && selected.length > 0 ? selected : 'none for now...' }}</i></p>
    </div>
  </div>
</template>

<script>
import TableCmp from '@/components/TableCmp'
import PencilIcon from '@/components/PencilIcon'
import TrashIcon from '@/components/TrashIcon'

export default {
  name: 'app',
  components: { TableCmp },
  data () {
    return {
      columns: [
        { column: 'first_name', title: 'First name', sortable: true, size: 23 },
        { column: 'last_name', title: 'Last name', sortable: true, size: 27 },
        { column: 'phone_number', title: 'Phone number', sortable: true }
      ],
      actions: [
        { action: 'edit', icon: PencilIcon, access: this.canEdit },
        { action: 'delete', icon: TrashIcon, access: this.canDelete }
      ],
      // dummy array of selected persons from phonebook
      // in the real world will be fetched from server
      selected: [
        { id: 2, first_name: 'Emely', last_name: 'Bishop', phone_number: '+468792140' },
        { id: 5, first_name: 'Kody', last_name: 'Mcdowell', phone_number: '+289327049' }
      ],
      sortData: {
        key: 'last_name',
        order: 'asc'
      },
      item: null
    }
  },
  computed: {
    phonebookList () {
      // dummy array of persons inside phonebook
      // in the real world will be fetched from server
      const phonebook = [
        { id: 1, first_name: 'Evan', last_name: 'Miles', phone_number: '+123456789' },
        { id: 2, first_name: 'Emely', last_name: 'Bishop', phone_number: '+468792140' },
        { id: 3, first_name: 'Landon', last_name: 'Meyer', phone_number: '+875923784' },
        { id: 4, first_name: 'Josue', last_name: 'Hendricks', phone_number: '+767251590' },
        { id: 5, first_name: 'Kody', last_name: 'Mcdowell', phone_number: '+289327049' }
      ]
      const list = phonebook.slice()
      return this.sort(list)
    }
  },
  methods: {
    // dummy function returns that edit is always possible
    // in the real world will return here some acl value or similar
    canEdit () {
      return true
    },
    // dummy function returns that delete is never possible
    // in the real world will return here some acl value or similar
    canDelete () {
      return false
    },
    editItem (item) {
      this.item = item
    },
    deleteItem (item) {
      // eslint-disable-next-line
      console.log('delete item:', item)
    },
    sort (list) {
      return list.sort((a, b) => {
        const order = this.sortData.order
        let acol = a[this.sortData.key]
        let bcol = b[this.sortData.key]
        if (this.sortData.key === 'last_name' || this.sortData.key === 'first_name') {
          acol = acol.toLowerCase()
          bcol = bcol.toLowerCase()
        }
        let result = 0
        if (order === 'asc') {
          if (acol < bcol) result = -1
          if (acol > bcol) result = 1
        } else {
          if (acol < bcol) result = 1
          if (acol > bcol) result = -1
        }
        return result
      })
    },
    sortBy (column) {
      if (column === this.sortData.key) {
        this.sortData.order = (this.sortData.order === 'asc') ? 'desc' : 'asc'
      } else {
        this.sortData.key = column
        this.sortData.order = 'asc'
      }
    },
    select (payload) {
      this.selected = payload.slice()
    }
  }
}
</script>

<style lang="scss">
body {
  background-color: antiquewhite;
}

#app {
  font-family: Arial, Helvetica, sans-serif;
  padding: 30px;

  @media screen and (max-width: 767px) {
    padding: 10px;
  }

  h1 {
    font-size: 30px;

    @media screen and (max-width: 767px) {
      font-size: 20px;
    }
  }

  p {
    font-size: 14px;

    @media screen and (max-width: 767px) {
      font-size: 10px;
    }
  }
}
</style>
