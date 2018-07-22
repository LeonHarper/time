<template>
    <div class="TextOutput">
      <div class="narrator">
        <textarea rows="10" cols="100" readonly>
        	This is a narrator test
        </textarea>
      </div>
    </div>
</template>

<script>
  export default {
    props: ['output'],
    name: 'textOutput'
  }
</script>