<script setup>
  import newView from '../components/newView.vue'
  import emitView from '../components/emitView.vue'

  import { RouterLink, RouterView } from 'vue-router'
  import { ref, reactive, computed, watch } from 'vue'
  import home from './HomeView.vue'

  const selected = ref('')
  const picked = ref('One')
  const count = ref(0)
  const secondCount = ref(0)
  const message = ref('')
  const age = ref('')
  const countc = ref('')
  const checked = ref('')

  const items = reactive ({
    name: 'Items',
    itemList: [
      'Milk',
      'Bread',
      'Apples'
    ]
  })

  const cart = ref([
  { id: 1, name: 'Milk' },
  { id: 2, name: 'Bread' },
  { id: 3, name: 'Apples' },
  ]);

  const occupants = reactive ({
    name: 'House',
    people: [
      'Harold', 
      'Meely',
      'Trace'
    ]
  })

  const occupantsMessage = computed(() => {
    return occupants.people.length > 0 ? 'Yes' : 'No'
  })

  const inter = 'Hello Visitor';
  const html = '<h1> This is html (: </h1>'
  const link = 'https://www.deakin.edu.au/'
  let number = 3
  let forNumber = 1

  const isActive = ref(true)
  const hasError = ref(false)

  const activeColour = ref('salmon')
  const fontSize = ref(30)

  const myUnit = reactive({
    title: 'Responsive Web Apps',
    code: 'SIT120',
    trimester: '2nd'
  })
 
  //2. Method?
  function say(message) { 
    alert(message)
  }

  //9. Watcher
  watch(count, (newValue, oldValue) => {
  console.log(`Count has changed from ${oldValue} to ${newValue}`);
  });

  //10. Props
  const props = defineProps(['huggy'])
  console.log(props.huggy)
  const moreProps = {
    id: 1,
    name: 'daisyLee'
  }

</script>

<template>
  
  <div 
    class="Essential Concepts"
    :style ="{color: activeColour, fontSize: fontSize + 'px' }" 
    :class="{active: isActive, 'text-danger': hasError}"> <!-- 5a. Binding class & 5b. Binding style-->

    <span> Message: {{ inter }}</span> <!-- 1a. text interpolation --> 
    <span v-html="html"></span> <!-- 1b. Raw HTML -->
    <a v-bind:href="link">Deakin Site </a> <!-- 1c. Attribute bindings using an argument -->
    <br>
    <a :href="link">Also the Deakin Site </a> <!-- Shorthand attribute binding -->
    <br>
    <span> Number: {{ number + 1 }}</span> <!-- 1d. Javascript inside syntax -->
    <br> 
    <button @click="count++"> <!-- 3. Reactive (ref) -->
      {{ count }}
    </button>
    <br>
    <p> People living in house: </p>
    <span>{{ occupantsMessage }}</span> <!-- 4. Computing -->

    <ul>
      <li v-for="(value, key) in myUnit" :key="key"> <!-- 6a. v-for with an object -->
        {{key}}: {{ value }}
      </li>
    </ul>

    <span v-for="forNumber in 10" :key="forNumber">{{ forNumber }}</span> <!-- 6b. v-for with a range -->
    
    <!-- 6a and 6b. Cant get to work due to key rule and v-if/for rule
    <ul>
      <template v-for="item in items"> 
          <li>{{  item.msg }}</li>
          <li class="Essential Concepts" role="for template"></li> 
      </template>
    </ul>
    
    <li v-for="item in cart" :key="item.id" v-if="item.name !== 'Yes'"> 
      {{ item.name }}
    </li>
    -->

    <!-- 6e. v-for with a component -->
    <NewView  
      v-for="(item, index) in items"
      :item="item"
      :index="index"
      :key="item.id"
    />

    <br>
    <button @click="secondCount++">Add 1</button> <!-- 7a. Event Handling (inline)-->
    <p>The second count is: {{ secondCount }}</p>

    <button @click="say('oh... hello')">Hey there partner!</button> <!-- 7b. Method Handling -->
    <button @click="say('later')">Well bye then!</button>

    <!-- 8a. Form input bindings & 8b modifiers  -->

    <p>Your name is... {{ message }}</p>
    <input v-model.lazy="message" placeholder="your name here" />
    <br>
    <p>You are this old... {{ age }}</p>
    <input v-model.number="age" placeholder="your age here" />
    
    <br>
    <input type="checkbox" id="checkbox" v-model="checked" />
    <label for="checkbox">{{ checked }}</label>
    <br>

    <div>Picked: {{ picked }}</div>
    <input type="radio" id="one" value="One" v-model="picked" />
    <label for="one">One</label>
    <input type="radio" id="two" value="Two" v-model="picked" />
    <label for="two">Two</label>
    <br>

    <span> Selected: {{ selected }}</span>
    <select v-model="selected">
      <option>Top</option>
      <option>Jungle</option>
      <option>Middle</option>
      <option>ADC</option>
      <option>Support</option>
    </select>
    <br>

    <!-- 10. Continuation of props and others-->
    <newView :id=moreProps.id :name="moreProps.name" />

    <div>
      <emitView @increase-by="(n) => countc += n" />
        <p>{{ countc }}</p>
    </div>

    <!-- Slots -->
    <newView>
      Click here!
    </newView>
    
    <!-- Routing -->
    <RouterLink to="/">Home</RouterLink> 

  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
  }
}
</style>
