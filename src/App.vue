<template>
  <h2>Volume Tracker (0-20)</h2>
  <h3>Current Volume - {{ volume }}</h3>
  <div>
    <button @click="volume +=2">Increase</button>
    <button @click="volume -=2">Decrease</button>
  </div>
  <input type="text" v-model="movie">
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      volume : 0,
      movie:''
    };
  },
  methods: {},
  computed: {},
  watch: {
    volume (newValue,oldValue){
      if(newValue > oldValue && newValue === 16){
        alert('Listening to a high volume for a long time may damage your hearing');
      }
    },
    movie(newValue){
      console.log(`Calling api with movie name = ${newValue}`)
    }
  }

};
</script>


<!-- computed setter -->
<!-- <template>
  <h2>Full name - {{ firstName }} {{ lastName }}</h2>
  <h2>Computed Full name {{ fullName }}</h2>
<button @click="changeFullName">Change Name</button>



  <button @click="items.push({ id: 4, title: 'keyboard', price: 50 })">Add</button>
  <h2>Total - {{ total }}</h2>
  <h2>Method Total - {{ getTotal() }}</h2>
  <input type="text" v-model="country">

  <template v-for="item in items" :key="item.id">
    <h2 v-if="item.price > 100">{{ item.title }} {{ item.price }}</h2>
  </template>
  <h2 v-for="item in expensiveItems" :key="item.id">
    {{ item.title }} {{ item.price }}
  </h2>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      firstName: 'John',
      lastName: 'Wayne',
      items: [
        {
          id: 1,
          title: 'TV',
          price: 100
        },
        {
          id: 2,
          title: 'Phone',
          price: 200
        },
        {
          id: 3,
          title: 'Laptop',
          price: 300
        }
      ],
      country: ''
    };
  },
  methods: {
    getTotal() {
      return this.items.reduce((total, curr) => (total = total + curr.price), 0);
    },
    changeFullName(){
      this.fullName = 'Clark Kent'
    }
  },
  computed: {
    fullName: {
      get() {
        return `${this.firstName} -  ${this.lastName}`
      },
      set(value){
        const names = value.split(' ')
        this.firstName = names[0]
        this.lastName = names[1]
      }
      
    },
    total() {
      return this.items.reduce((total, curr) => (total = total + curr.price), 0);
    },
    expensiveItems() {
      return this.items.filter(item => item.price > 100);
    }
  }
};
</script>   -->


<!-- bonus directives -->
<!-- <template>
  <h2 v-once>{{ name }}</h2>
  <button @click="name = 'Batman'">Change Name</button>
  <h2 v-pre>{{ name }}</h2>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      name:'John'
    };
  },
};
</script>  -->


<!-- modifiers and forms -->
<!-- <template>
  <div>
    <pre>{{ JSON.stringify(formValues, null, 2) }}</pre>
  </div>
  <form @submit.prevent="submitForm">
    <div>
      <label for="name">Name: </label>
      <input type="text" id="name" v-model.trim.lazy="formValues.name">
    </div>
    <div>
      <label for="profile">Profile Summary: </label> <br>
      <textarea id="profile" v-model="formValues.profileSummary" cols="30" rows="10"></textarea>
    </div>
    <div>
      <label for="country">Country : </label> <br>
      <select id="country" v-model="formValues.country">
        <option value="">Select a country</option>
        <option value="india">India</option>
        <option value="japans">Japan</option>
        <option value="philippines">Philippines</option>
      </select>
    </div>
    <div>
      <label for="job">Job Location : </label> <br>
      <select id="job" multiple v-model="formValues.jobLocation">
        <option value="">Select a country</option>
        <option value="india">India</option>
        <option value="japans">Japan</option>
        <option value="philippines">Philippines</option>
      </select>
    </div>
    <div>
      <input type="checkbox" id="remoteWork" true-value="yes" false-value="no" v-model="formValues.remoteWork" />
      <label for="remoteWork">Open to remote work?</label>
    </div>
    <div>
      <label for="skill">Skill Sets</label>
      <input type="checkbox" id="html" value="html" v-model="formValues.skillSet"/>
      <label for="html">HTML</label>
      <input type="checkbox" id="css" value="css" v-model="formValues.skillSet"/>
      <label for="css">CSS</label>
      <input type="checkbox" id="java" value="java" v-model="formValues.skillSet"/>
      <label for="java">Javascript</label>

    </div>
    <div>
      <label>Years of Experience</label>
      <input type="radio" id="0-2" value="0-2" v-model="formValues.yearsOfExperience"/>
      <label for="html">0-2</label>
      <input type="radio" id="3-4" value="3-4" v-model="formValues.yearsOfExperience"/>
      <label for="css">3-4</label>
      <input type="radio" id="5-6" value="5-6" v-model="formValues.yearsOfExperience"/>
      <label for="java">5-6</label>

    </div>
    <div>
      <label for="age">Age</label>
      <input @keyup.enter="submitForm" type="number"  id="age" v-model.number="formValues.age">
    </div>

   <div>
      <button>Submit</button>
    </div>


</form>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      formValues: {
        name: '',
        profileSummary: '',
        country: '',
        jobLocation: [],
        remoteWork: false,
        skillSet :[],
        yearsOfExperience: '',
        age:null
      }
    };
  },
  methods: {
    submitForm(){
      console.log('Form values',this.formValues)
    }


  }
};
</script>  -->


<!-- event handling -->
<!-- <template>
  <h2>{{ name }}</h2>
  <div>
    <button v-on:click="changeName($event),increment(1,$event)">Change Name</button>
  </div>
  <h2>{{ count }}</h2>
  <div>
    <button @click="increment(1,$event)">Increment 1</button>
    <button @click="increment(5,$event)">Increment 5</button>
    <button @click="decrement(1)">Decrement 1</button>
    <button @click="decrement(5)">Decrement 5</button>
  </div>
</template>


<script>
export default {
  name: "App",
  data() {
    return {
      name:'John',
      count:0
    };
  },
  methods:{
    changeName(event){
      this.name = 'Batman';
      console.log(event)
    },
    increment(num,event){
      this.count+=num;
      console.log(event)
    },
    decrement(num){
      return this.count-=num;
    }
  }
};
</script> -->


<!-- 4th batch -->
<!-- <template>
  <h2>{{ 2 + 3 + 5 }}</h2>
  <h2>Add Method - {{ add(1, 2, 3) }}</h2>
  <h2>Multiply Method - {{ multiply(5) }}</h2>




</template>

<script>
export default {
  name: "App",
  data() {
    return {
      baseMultiplier: 5
    };
  },
  methods: {
    add(a, b, c) {
      return a + b + c;
    },
    multiply(num) {
      return num * this.baseMultiplier
    }


  }
};
</script> -->

<!-- 3rd batch -->
<!-- <template>
  <h2 v-for="(name, index) in names" :key="name">{{ index }} {{ name }}</h2>
  <h2 v-for="name in fullNames" :key="name.first">
    {{ name.first }} {{ name.last }}
  </h2>
  <div v-for="actor in actors" :key="actor.name">
    <h2>{{ actor.name }}</h2>
    <h3 v-for="movie in actor.movies" :key="movie"> {{ movie }}</h3>
  </div>
  <h2 v-for="(value,key,index) in myInfo" :key="value">{{ value }} {{ key }} {{ index }}</h2>

  <template v-for="name in names" :key="name">
  <h2>{{ name }}</h2>
  <hr/>
  </template>

</template>

<script>
export default {
  name: "App",
  data() {
    return {
      names: ["John", "Jerald", "Steph"],
      fullNames: [
        { first: "Jerald", last: "Anderson" },
        { first: "Jackson", last: "Hayes" },
        { first: "Sam", last: "Milby" },
      ],
      actors: [
        {
          name: "Janny Decosta",
          movies: ["Batman", "Superman"],
        },
        {
          name: "Ricardo Decosta",
          movies: ["Voltes 5", "Raging Potato"],
        },
      ],
      myInfo : {
        name:'Jannyss',
        channel:'JannySchools',
        course:'Vue3'
      }
    };
  },
};
</script>  -->


<!-- SECOND BATCH -->
<!-- 
<template>
  <h2 v-if="num === 0">The number is zero</h2>
  <h2 v-else-if="num < 0">The number is negative</h2>
  <h2 v-else-if="num > 0">The number is positive</h2>
  <h2 v-else>Not a number</h2>
  <template v-if="display">
    <h2>John</h2>
    <h2>Rey</h2>
    <h2>Vue</h2>
  </template>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      num: "Hi",
      display: false,
    };
  },
};
</script> -->




<!-- FIRST BATCH -->
<!-- <template>
<div>{{greet}} {{ name }}</div>
<div v-text="channel"></div>
<div v-html="action"></div>
<h2 :id="headingId">Heading</h2>
<h2 :class="underline">sdsad</h2>
<h2 :class="isPromoted && 'promoted'">Promoted Movie</h2>
<h2 :class="isSoldout ? 'sold-out':'new'">Sold out Movie</h2>
<h2 :class="['new','promoted']">dasdsads</h2>
<h2 :class="[isPromoted && 'promoted',isSoldout ? 'sold-out':'new']">My test</h2>
<h2 :class="{
  promoted:isPromoted,
  new:!isSoldout,
  'sold-out':isSoldout
}">Object conditional movie</h2>
<h2 :style="{
  color:isHighlight,
  'font-size':headerSize ,
  padding:'20px',
}">highlight</h2>
<h2 :style="headerStyleObject">Hi</h2>
<div :style="[baseStyleObject,successStyleObject]">Hi</div>
<div :style="[baseStyleObject,dangerStyleObject]">Hi</div>
<button :disabled="isDisabled">Disabled</button>
</template> -->

<!-- <script>

export default {
  name: 'App',
  data(){
    return {
      greet:"Hello",
      name:"Batmanss",
      channel:"John",
      action: "<a href='#' onclick=\"alert('gwapo ko');\">Win Prizes</a>",
      headingId:"Heading",
      isDisabled:true,
      underline:"underline",
      isPromoted:false,
      isSoldout:false,
      isHighlight:'red',
      headerSize:'50px',
      headerStyleObject : {
        color:'orange',
        fontSize: '50px',
        padding:'20px'
      },
      baseStyleObject : {
        fontSize: '50px',
        padding:'20px'
      },
      successStyleObject : {
        color:'green',
        backgroundColor:'lightgreen',
        border:'1px solid green',
        padding:'20px'
      },
      dangerStyleObject : {
        color:'darkred',
        backgroundColor:'red',
        border:'1px solid darkred',
        padding:'20px'
      }
    };
  },
};
</script> -->

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

.underline {
  text-decoration: underline;
}

.promoted {
  font-style: italic;
}

.new {
  color: olivedrab;
}

.sold-out {
  color: red;
}
</style>
