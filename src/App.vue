<template>
  <InteractiveRating></InteractiveRating>
</template>

<script>

import InteractiveRating from './components/InteractiveRating'
export default {
  components: { InteractiveRating },

}
</script>

<style>
:root{
  --orange: hsl(25, 97%, 53%);
  --white: hsl(0, 0%, 100%);
  --light-grey: hsl(217,12%, 63%);
  --medium-grey: hsl(216, 12%, 54%);
  --medium-grey-2: hsl(216, 12%, 25%);
  --dark-blue: hsl(213, 19%, 18%);
  --very-dark-blue: hsl(216, 12%, 8%);
}
*{
  font-family: sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
p{
  font-size: 15px;
}

</style>
