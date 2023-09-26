<template>
    <button class="fancy-btn">
        <slot/> 
      </button>
  </template>
  
  <style>
  .fancy-btn {
    color: #000000;
    background: linear-gradient(315deg, #42d392 25%, #d6ff64);
    border: none;
    padding: 5px 10px;
    margin: 5px;
    border-radius: 8px;
    cursor: pointer;
  }
  </style>