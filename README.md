## React to Vue Guide

I have been developing in React for so long that it has become second nature. I recently started working for a new company and we are developing the web application in Vue. I took a few Vue courses and read the docs but I am always asking myself: 

**In React I would do it this way... but how do I implement it using Vue?**

So I decided to develop a little cheat sheet/guide for myself, and I hope you find it useful too!

---
### Looping through data to render multiple components


**React**
```
{this.props.members.map((member, index) => 
	<TableRow key={member.id} member={member} gray={index % 2 !== 0}/>
)}
```

**Vue**
```
 <table-row v-for="(member, index) in members" :key="member.id" :member="member" :gray="index % 2 !== 0" />
```
---
### Conditionally rendering a component

**React**

```
{ this.props.recent ? <Icon icon="dot" /> : null }
```

**Vue**

```
<icon v-if="recent" icon="dot"/>
```
---
### On Click Event

**React**
```
 handleClick = () => {
    console.log('Button Click!');
  }

  render() {
    return (
      <button onClick={this.handleClick}>
        Click Me
      </button>
    );
  }
```

**Vue**
```
<template>
	<button @click="onClick">Click Me</button>
</template>
<script>
export default {
  name: 'MyButton',
  methods: {
    onClick() {
      console.log('Button Click!');
    }
  }
}
</script>
```
---
### Conditionally applying a class

**React**
```
<Toggle className={this.state.open ? 'open' : null} />
```

**Vue**
```
<toggle :class="{open}" />  // using es6 or :class="{open: open}" the class open will be applied depending on the value of open

...

data: function() {
  return {
    open: false
  }
},
```
___