<script setup>
  import TheWelcome from '../components/TheWelcome.vue'
  // IMPORT TABLE COMPONENT
  import Table from '../components/Table.vue'
  // IMPORT AXIOS
  import axios from 'axios'

  // IMPORT WEB3 
  import Web3 from 'web3'
</script>

<template>
  <Table :columns="columns" :items="items" />
</template>
<script>
  export default {
    name: "Home",
    components: {
      TheWelcome,
      Table
    },
    data() {
      return {
        // columns: [{
        //     label: "Name",
        //     field: "name",
        //     typeData: "string",
        //     sort: "asc",
        //     width: 150
        //   },
        //   {
        //     label: "Position",
        //     field: "position",
        //     typeData: "string",
        //     sort: "asc",
        //     width: 270
        //   },
        //   {
        //     label: "Office",
        //     field: "office",
        //     typeData: "string",
        //     sort: "asc",
        //     width: 200
        //   },
        //   {
        //     label: "Age",
        //     field: "age",
        //     typeData: "string",
        //     sort: "asc",
        //     width: 100
        //   },
        //   {
        //     label: "Start date",
        //     field: "date",
        //     typeData: "date",
        //     sort: "asc",
        //     width: 150
        //   },
        //   {
        //     label: "Salary",
        //     field: "salary",
        //     typeData: "price",
        //     sort: "asc",
        //     width: 100
        //   }
        // ],
        // items: [{
        //     name: "Tiger Nixon",
        //     position: "System Architect",
        //     office: "Edinburgh",
        //     age: "61",
        //     date: "2011/04/25",
        //     salary: "320800"
        //   },
        //   {
        //     name: "Garrett Winters",
        //     position: "Accountant",
        //     office: "Tokyo",
        //     age: "63",
        //     date: "2011/07/25",
        //     salary: "170750"
        //   },
        //   {
        //     name: "Ashton Cox",
        //     position: "Junior Technical Author",
        //     office: "San Francisco",
        //     age: "66",
        //     date: "2009/01/12",
        //     salary: "86000"
        //   },
        //   {
        //     name: "Cedric Kelly",
        //     position: "Senior Javascript Developer",
        //     office: "Edinburgh",
        //     age: "22",
        //     date: "2012/03/29",
        //     salary: "433060"
        //   },
        //   {
        //     name: "Airi Satou",
        //     position: "Accountant",
        //     office: "Tokyo",
        //     age: "33",
        //     date: "2008/11/28",
        //     salary: "162700"
        //   },
        //   {
        //     name: "Brielle Williamson",
        //     position: "Integration Specialist",
        //     office: "New York",
        //     age: "61",
        //     date: "2012/12/02",
        //     salary: "372000"
        //   },
        // ],
        columns : [],
        items : [],
        URL_WEB3 : 'http://localhost:8545/',
      }
    },
    methods: {
      // GET DATA
      async getData() {
        const response = await axios.get('https://jsonplaceholder.typicode.com/users')
        // this.items = response.data
        console.log(response.data)
      },
      // GET DATA BLOCK NUMBER 
      async getDataBlockNumber() {
        const web3 = new Web3(this.URL_WEB3)
        const blockNumber = await web3.eth.getBlockNumber()
        console.log(blockNumber)
      },
      // GET BATA BLOCK 
      async getDataBlock() {
        const web3 = new Web3(this.URL_WEB3)
        const block = await web3.eth.getBlock('latest')
        
        this.columns = Object.keys(block).map((key) => {
          switch (key) {
            case 'number':
              return {
                label: key,
                field: key,
                typeData: 'number',
                sort: 'asc',
                width: 150
              }
            case 'hash':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 270
              }
            case 'parentHash':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 200
              }
            case 'nonce':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 100
              }
            case 'sha3Uncles':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 100
              }
            case 'logsBloom':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 100
              }
            case 'transactionsRoot':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 100
              }
            case 'stateRoot':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 100
              }
            case 'miner':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 100
              }
            case 'difficulty':
              return {
                label: key,
                field: key,
                typeData: 'number',
                sort: 'asc',
                width: 100
              }
            case 'totalDifficulty':
              return {
                label: key,
                field: key,
                typeData: 'number',
                sort: 'asc',
                width: 100
              }
            case 'extraData':
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 100
              }
            case 'size':
              return {
                label: key,
                field: key,
                typeData: 'number',
                sort: 'asc',
                width: 100
              }
            case 'gasLimit':
              return {
                label: key,
                field: key,
                typeData: 'number',
                sort: 'asc',
                width: 100
              }
            case 'gasUsed':
              return {
                label: key,
                field: key,
                typeData: 'number',
                sort: 'asc',
                width: 100
              }
            case 'timestamp':
              return {
                label: key,
                field: key,
                typeData: 'timestamp',
                sort: 'asc',
                width: 100
              }
            case 'transactions':
              return {
                label: key,
                field: key,
                typeData: 'array',
                sort: 'asc',
                width: 100
              }
            case 'uncles':
              return {
                label: key,
                field: key,
                typeData: 'array',
                sort: 'asc',
                width: 100
              }
            default:
              return {
                label: key,
                field: key,
                typeData: 'string',
                sort: 'asc',
                width: 100
              }
          }
      
        })
        this.items = [block]
      }
    },
    mounted() {
      this.getDataBlockNumber();
      this.getDataBlock();
    },
  }
</script>