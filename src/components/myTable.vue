<template>
  <div class="flex-col">
    <table>
      <thead>
        <tr>
          <th>Item</th>
          <th>Tipo</th>
          <th>Via</th>
          <th>Data de compra</th>
          <th>Valor da compra</th>
          <th>Requer Diluição</th>
        </tr>
      </thead>
      <tr v-if="currentPage == 1" v-for="item in data" :key="item">
        <td class="px-2">{{ item.item }}</td>
        <td class="px-2">{{ item.tipo }}</td>
        <td class="px-2">{{ item.via }}</td>
        <td class="px-2">{{ item.dt_compra }}</td>
        <td class="px-2">{{ item.vl_compra }}</td>
        <td class="px-2">{{ item.requer_diluicao }}</td>
      </tr>
      <tr v-else>
        <td class="px-2"><input type="text" /></td>
        <td class="px-2"><input type="text" /></td>
        <td class="px-2"><input type="text" /></td>
        <td class="px-2"><input type="text" /></td>
        <td class="px-2"><input type="number" /></td>
        <td class="px-2">
          <select name="requer_diluicao" id="requer_diluicao">
            <option value="Sim">Sim</option>
            <option value="Não">Não</option>
          </select>
        </td>
        <td><button>Cadastrar</button></td>
      </tr>
    </table>
    <div class="flex justify-center">
      <button @click="previousPage" :disabled="currentPage === 1">
        Previous
      </button>
      <span>{{ currentPage }} / {{ totalPages }}</span>
      <button @click="nextPage" :disabled="currentPage === totalPages">
        Next
      </button>
    </div>
  </div>
</template>
<script lang="ts">
  import backend from '../backend.json'
  export default {
    data() {
      return {
        data: backend,
        currentPage: 1,
        totalPages: 2,
      }
    },
    methods: {
      previousPage() {
        if (this.currentPage > 1) {
          this.currentPage -= 1
        }
      },
      nextPage() {
        if (this.currentPage < this.totalPages) {
          this.currentPage += 1
        }
      },
    },
  }
</script>

<style>
  table {
    border-collapse: collapse;
    width: 100%;
  }
  th,
  td {
    border: 1px solid #ddd;
    padding: 8px;
  }
  tr:nth-child(even) {
    background-color: #f2f2f2;
  }
  tr:hover {
    background-color: #ddd;
  }
  th {
    padding-top: 12px;
    padding-bottom: 12px;
    text-align: left;
    background-color: #4caf50;
    color: white;
  }

  button {
    background-color: #4caf50;
    border-radius: 4px;
    color: white;
    border: none;
    padding: 8px 16px;
    text-decoration: none;
    margin: 4px 2px;
    cursor: pointer;
  }
</style>
