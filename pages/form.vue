<template>
  <div>
    <h4 class="form-label">Creating the form</h4>
  </div>
  <div>
    <h1>New Character</h1>

    <FormKit type="form"
      @submit="createCharacter"
      :plugins="[castRangeToNumber]"
      submit-label="Create Character"
      #default="{ value }"
     >
      <FormKit
        type="text"
        name="name"
        id="name"
        validation="required|not:Admin"
        label="Name"
        help="Enter your character's full name"
        placeholder="“Scarlet Sword”"
      />

      <FormKit
        type="select"
        label="Class"
        name="classname"
        id="classname"
        placeholder="Select a class"
        :options="['Warrior', 'Mage', 'Assassin']"
      />

      <FormKit
        type="range"
        name="strength"
        id="strength"
        label="Strength"
        value="5"
        validation="min:2|max:9"
        validation-visibility="live"
        min="1"
        max="10"
        step="1"
        help="How many strength points should this character have?"
      />

      <FormKit
        type="range"
        name="skill"
        id="skill"
        validation="required|max:10"
        label="Skill"
        value="5"
        min="1"
        max="10"
        step="1"
        help="How much skill points to start with"
      />

      <FormKit
        type="range"
        name="dexterity"
        id="dexterity"
        validation="required|max:10"
        label="Dexterity"
        value="5"
        min="1"
        max="10"
        step="1"
        help="How much dexterity points to start with"
      />
    </FormKit>
  </div>
</template>

<script setup>
//  const { data } = await useFetch("http://localhost:8080/api/v1/posts", {
//        method: 'POST',
//        query: {
//          name: this.name,
//          classname: this.classname,
//          strength: this.strength,
//          skill: this.skill,
//          dexterity: this.dexterity,
//        }
//        });

import { onMounted } from 'vue'
import { getNode } from '@formkit/core'

const castRangeToNumber = (node) => {
  // We add a check to add the cast only to range inputs
  if (node.props.type !== 'range') return

  node.hook.input((value, next) => next(Number(value)))
}

const CHARACTER_BASE_STATS = {
  Warrior: {
    strength: 9,
    skill: 1,
    dexterity: 5,
  },
  Mage: {
    strength: 5,
    skill: 10,
    dexterity: 8,
  },
  Assassin: {
    strength: 5,
    skill: 4,
    dexterity: 10,
  },
}

const createCharacter = async (fields) => {
  // await new Promise((r) => setTimeout(r, 1000))
  // alert(JSON.stringify(fields))

  const { data } = await useFetch("http://localhost:8080/api/v1/posts", {
        method: 'POST',
        body: {
          name: fields.name,
          classname: fields.classname,
          strength: fields.strength,
          skill: fields.skill,
          dexterity: fields.dexterity,
        }
        })
        .then(response => {
          console.log ("success");
          this.$router.push({
          path: '/posts/' + data.data.id
          })
        })
        .catch(error => {
          console.log ("failed");
        });
}
</script>
