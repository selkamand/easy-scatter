# easy-scatter

A simple javascript package for gernerating D3 scatterplots


## Table of Contents
- [easy-scatter](#easy-scatter)
  - [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [Quick Start](#quick-start)
  - [Aesthetic Properties](#aesthetic-properties)
  - [Delayed Range Setting](#delayed-range-setting)

## Installation

Install the latest release form npm

`npm install easy-scatter`

## Quick Start

```{javascript}
import * as  d3 from "d3"
import {easyScatter} from "easy-scatter"

// Setup Data
const data = [
  { num1: 1.2, num2: 5, num3: 10, cat1: 'blue' },
  { num1: 2.1, num2: 6, num3: 9, cat1: 'blue' },
  { num1: 3.5, num2: 7, num3: 8, cat1: 'blue' },
  { num1: 4.3, num2: 8, num3: 7, cat1: 'blue' },
  { num1: 5, num2: 9, num3: 6, cat1: 'blue' },
  { num1: 6, num2: 10, num3: 5, cat1: 'red' },
  { num1: 7.1, num2: 11, num3: 4, cat1: 'red' },
  { num1: 7.9, num2: 12, num3: 3, cat1: 'red' },
  { num1: 9, num2: 13, num3: 2, cat1: 'red' },
];

// Generate Chart Template
const createScatterChart = easyScatter()
    .data(data) // Set the data
    .xCol("num1")
    .yCol("num1")
    .colorCol("cat1")
    .xRange([10,  100])
    .yRange([100,  400])

// Create SVG
const svg = d3
   .select("body")
   .append("svg")
   .attr("width", window.innerWidth)
   .attr("height", window.innerHeight)

// Create Chart
const scatter = createScatterChart(svg)
```


## Aesthetic Properties

You can connect any of the below aesthetic properties of your graph to a variable in your data using the indicated method to chain

```{r}
property: method
x: xCol() 
y: yCol()
color: colorCol()
size: sizeCol()
shape: shapeCol()
```

## Delayed Range Setting

As you specify requirements for your scatter chart by chaining methods to easyScatter(), its 'minspace' property is updated. This property is an object with 4 properties:  top, right, bottom, & left, each containing the pixel value required (external to the axes) to account for axis tick and text spacing.