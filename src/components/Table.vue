<template>
  <div class="overflow-x-auto relative">
    <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
      <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
        <tr>
          <th scope="col" class="py-3 px-6" v-for="(column, index) in columns" :key="index"> {{ column.label }}</th>
        </tr>
      </thead>
      <tbody>
        <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700" v-for="(item, index) in items" :key="index">
          <td class="py-4 px-6" v-for="(column, indexColumn) in columns" :key="indexColumn">{{ 
          formatValue(item[column.field], column.typeData) }}</td>


        </tr>
      </tbody>
    </table>
    <!-- PAGINATION -->
    <div class="flex justify-between items-center mt-4">
      <div class="flex items-center">
        <span class="text-sm text-gray-700 dark:text-gray-400">Showing 1 to 10 of {{ totalRecords }} entries</span>
        <div class="relative mx-4">
          <select
            class="rounded border appearance-none border-gray-400 py-2 focus:outline-none focus:border-gray-500 text-base pl-3 pr-10">
            <option>10</option>
            <option>20</option>
            <option>30</option>
            <option>40</option>
            <option>50</option>
          </select>
          <span
            class="absolute right-0 top-0 h-full w-10 text-center text-gray-600 pointer-events-none flex items-center justify-center">
            <svg class="h-4 w-4 fill-current" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
              <path d="M7 7l3-3 3 3v4H7V7zm2 6a2 2 0 11-.001-3.999A2 2 0 019 13z" />
            </svg>
          </span>
        </div>
        <span class="text-sm text-gray-700 dark:text-gray-400">entries</span>
      </div>
      <div class="flex items-center">
        <button class="bg-gray-200 text-gray-600 h-10 w-10 rounded-full outline-none focus:outline-none mr-1"
          type="button">
          1
        </button>
        <button class="bg-gray-200 text-gray-600 h-10 w-10 rounded-full outline-none focus:outline-none mr-1"
          type="button">
          2
        </button>
        <button class="bg-gray-200 text-gray-600 h-10 w-10 rounded-full outline-none focus:outline-none mr-1"
          type="button">
          3
        </button>
        <button class="bg-gray-200 text-gray-600 h-10 w-10 rounded-full outline-none focus:outline-none mr-1"
          type="button">
          4
        </button>
      </div>
    </div>
  </div>

</template>


<script>
  export default {
    name: "Table",
    data() {
      return {
        totalRecords: 0,
      }
    },
    props: {
      columns: {
        type: Array,
        required: true,
      },
      items: {
        type: Array,
        required: true,
      },
    },
    mounted() {
      this.totalRecords = this.items.length;
    },
    methods: {
      // FORMAT VALUE
      formatValue(value, typeData) {
        switch (typeData) {
          case 'date':
            return new Date(value).toLocaleDateString();
          case 'timestamp':
            return new Date(value).toLocaleTimeString();
          case 'price':
            return new Intl.NumberFormat('en-US', {
              style: 'currency',
              currency: 'IDR'
            }).format(value);
          default:
            return value;
        }
      },
    },



  };
</script>