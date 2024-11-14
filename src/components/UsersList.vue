<script setup>

</script>

<template>
<main>
  <table>
    <thead>
    <tr>
      <th>ID</th>
      <th>Username</th>
      <th>Bannir</th>
    </tr>
    </thead>
    <tbody>
      <tr v-for="n in 15" :key="n">
        <td>{{ n }}</td>
        <td>{{ `username n°${n}` }}</td>
        <td><button class="delete">Bannir</button></td>
      </tr>
    </tbody>
  </table>
</main>
</template>

<style scoped lang="scss">

@import '@/assets/variables';
table {
  width: 100%;
  font-family: $body-font;
  font-size: 16px;
  thead {
    background-color: $brown;
    color: $blanchedalmond;
    tr {
      font-size: 20px;
      th {
        vertical-align: middle;
      }
    }
    tr:hover {
      background-color: inherit;
    }
  }
  tr {
    height: 30px;
    transition: 0.3s;
  }
  tr:nth-child(even) {
    background-color: lightgray
  }
  tr:hover {
    background-color: $bisque;
  }
  td {
    text-align: center;
    vertical-align: middle;
    border: 1px dashed $brown;
    button {
      cursor: pointer;
      line-height: 2rem;
      width: 100%;
      height: 100%;
      background-color: transparent;
      transition: background-color .5s;
    }
    button.validate:hover {
      background-color: lawngreen;
    }
    button.delete:hover {
      background-color: red;
    }
  }
}
</style>
