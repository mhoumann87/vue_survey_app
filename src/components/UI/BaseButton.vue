<template>
  <button>
    <slot></slot>
  </button>
</template>

<style scoped>
  button {
    font: inherit;
    border: 1px solid #360032;
    background-color: #360032;
    color: #fff;
    padding: 0.5rem 2rem;
    cursor: pointer;
    transition: all 0.3s ease-in;
  }

  button:hover,
  button:focus,
  button:active {
    border-color: #5c0556;
    background-color: #5c0556;
  }
</style>
