<template>
  <div>
    <h4 class="form-label">Creating the form</h4>
  </div>
  <div>
    <h1>New Character</h1>

    <FormKit type="form">
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
const param1 = ref('name')
console.log (param1);

// console.log (this.name);
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
</script>
