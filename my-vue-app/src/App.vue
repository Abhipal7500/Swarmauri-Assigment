<template>
  <div id="app">
    <h1>Interactive Card Display</h1>


    <div v-if="currentCardIndex === 0" class="card">
      <CardImage 
        src="https://images.unsplash.com/photo-1506748686214-e9df14d4d9d0?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwzNjUyOXwwfDF8c2VhcmNofDJ8fG1vdW50YWluc3xlbnwwfHx8fDE2OTg0OTk2NjI&ixlib=rb-1.2.1&q=80&w=1080" 
        caption="Serene Mountains" 
        overlay="Explore the Peaks"
      />
      <CardHeader 
        title="Mountain Adventure" 
        subtitle="A serene view of the mountains"
        image="https://via.placeholder.com/100"
      />
      <CardBody :collapsible="true" :expanded="true" ariaLabel="Card Content">
        <p>
          Discover the tranquility of mountain landscapes and connect with nature on a deeper level.
        </p>
      </CardBody>
    </div>

    <div v-if="currentCardIndex === 1" class="card">
      <CardImage 
        src="https://images.unsplash.com/photo-1507525428034-b723cf961d3e?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwzNjUyOXwwfDF8c2VhcmNofDR8fGJlYWNoJTIwbGFuZHNjYXBlfGVufDB8fHx8MTY5ODQ5OTczNQ&ixlib=rb-1.2.1&q=80&w=1080" 
        caption="Sunny Beach" 
        overlay="Relax by the Shore"
      />
      <CardHeader 
        title="Beach Bliss" 
        subtitle="Feel the waves and the sun"
        image="https://images.unsplash.com/photo-1445820130724-e5e0c89eac3f?crop=entropy&cs=tinysrgb&fit=max&fm=jpg&ixid=MnwzNjUyOXwwfDF8c2VhcmNofDF8fGZvcmVzdHxlbnwwfHx8fDE2OTg0OTk4MTA&ixlib=rb-1.2.1&q=80&w=1080"
      />
      <CardBody :collapsible="true" :expanded="true" ariaLabel="Card Content">
        <p>
          Enjoy the warmth of the sun and the soothing sound of waves at a sunny beach.
        </p>
      </CardBody>
    </div>

    <div v-if="currentCardIndex === 2" class="card">
      <CardImage 
        src="https://via.placeholder.com/600x400?text=Nature+Image+3" 
        caption="Calm Forest" 
        overlay="Walk Among the Trees"
      />
      <CardHeader 
        title="Forest Retreat" 
        subtitle="Immerse yourself in greenery"
        image="https://via.placeholder.com/100"
      />
      <CardBody :collapsible="true" :expanded="true" ariaLabel="Card Content">
        <p>
          Reconnect with nature by exploring the calm and serene forests, a perfect escape.
        </p>
      </CardBody>
    </div>

    <!-- Navigation Button -->
    <button @click="showNextCard">
      {{ currentCardIndex === cards.length - 1 ? 'Restart' : 'Next' }}
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import CardImage from '@swarmakit/vue/src/components/CardImage/CardImage.vue';
import CardHeader from '@swarmakit/vue/src/components/CardHeader/CardHeader.vue';
import CardBody from '@swarmakit/vue/src/components/CardBody/CardBody.vue';
import Button from '@swarmakit/vue/src/components/Button/Button.vue';

const currentCardIndex = ref(0);
const cards = [
  { title: 'Mountain Adventure', subtitle: 'A serene view of the mountains', image: 'https://via.placeholder.com/100', content: 'Discover the tranquility of mountain landscapes and connect with nature on a deeper level.' },
  { title: 'Beach Bliss', subtitle: 'Feel the waves and the sun', image: 'https://via.placeholder.com/100', content: 'Enjoy the warmth of the sun and the soothing sound of waves at a sunny beach.' },
  { title: 'Forest Retreat', subtitle: 'Immerse yourself in greenery', image: 'https://via.placeholder.com/100', content: 'Reconnect with nature by exploring the calm and serene forests, a perfect escape.' },
];

const showNextCard = () => {
  if (currentCardIndex.value < cards.length - 1) {
    currentCardIndex.value += 1;
  } else {
    currentCardIndex.value = 0; 
  }
};
</script>

<style scoped>
#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  margin-top: 30px;
  background-color: #f9f9f9;
  padding: 20px;
}

h1 {
  font-size: 2.5rem;
  color: #2c3e50;
  margin-bottom: 20px;
}

.card {
  width: 70%;
  margin: 20px auto;
  background: white;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.2);
}

.card p {
  font-size: 1rem;
  color: #555;
  line-height: 1.6;
  margin: 10px 20px;
  text-align: justify;
}

button {
  background-color: #3498db;
  color: white;
  padding: 10px 20px;
  font-size: 1rem;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin: 20px;
}

button:hover {
  background-color: #2980b9;
}
</style>
