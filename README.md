
## Vue3 Data Table Component
### vue3-datatable-component
#### A lightweight and high-customizable data-table based on vue-3.
##### Paginate, Sort and Filter your tables with ease.




## Demo

 [View Demo Project]().
 
 

### Features

* Super easy to setup!
* Super light weight
* Highly-customizable
* A lot more coming!






## Install

```
npm i vue3-datatable-component
```

### Basic Usage
```
<template>
  <div id="app">
    <vue3-datatable-component
      :fields="fields"
      :data="studentData"
      :searchFilter="true"
      :sort="true"
    />
  </div>
</template>

<script>

import Vue3DatatableComponent from "vue3-datatable-component";

export default {
  name: 'App',
  components: {
    Vue3DatatableComponent,
  },
  setup() {
    //An array of values for the data
    const studentData = [
      {
        ID: "01",
        Name: "Abiola Esther",
        Course: "Computer Science",
        Gender: "Female",
        Age: "17",
      },
      {
        ID: "02",
        Name: "Robert V. Kratz",
        Course: "Philosophy",
        Gender: "Male",
        Age: "19",
      },
      {
        ID: "03",
        Name: "Kristen Anderson",
        Course: "Economics",
        Gender: "Female",
        Age: "20",
      },
      {
        ID: "04",
        Name: "Adam Simon",
        Course: "Food science",
        Gender: "Male",
        Age: "21",
      },
      {
        ID: "05",
        Name: "Daisy Katherine",
        Course: "Business studies",
        Gender: "Female",
        Age: "22",
      },
    ];
    const fields = ["ID", "Name", "Course", "Gender", "Age"];
    return { studentData, fields };
  },
};
</script>
```



## Configuration

| Name          | Type          |  Default       | Description |
| ------------- |:-------------:| :-------------:|:-------------:|
| fields        |   Array       |      [ ]        |      Specifies the table head         |
| data      | Array     |  [ ]     |  right bar     |
|     searchFilter  | Boolean    |  true    |  Displays search bar for filtering table data    |
|     sort  | Boolean    |  true    |  Sorts table data on click    |
```
