# Introduction

### 1. The Coordinate System

1. svg 默认长宽值为 height=150, width=300
2. svg 中元素使用 cx, cy attribute 控制位置

### 2. Scales

1. 需要一个将数据转换为坐标的方程, 称为 scale
2. scale 有 `domain`(0%-100%) 和 `range`(0px-npx) 属性, 
3. `domain`: 数据的范围
4. `range`: 坐标的范围
5. x(25): X 轴的 scale, 在 range n=400 时, x(25)=100

### 3. Add Axis and translation

1. 使用 `transform=“translate(0, 150)”` 来调整位置


```js
var axes = d3.select('#test2');
    var margin = {top: 10, bottom: 30, left: 30, right: 40};
    var width = 450 - margin.left - margin.right;
    var height = 400 - margin.top - margin.bottom;
    // append svg and create axes
    var svg2 = axes
        .append("svg")
            .attr("width", width + margin.left + margin.right)
            .attr("height", height + margin.top + margin.bottom)
        .append("g")
            .attr("transform", "translate(" + margin.left + "," + margin.top + ")");
    // create axes
    var xaxis = d3.scaleLinear()
        .domain([0, 100])
        .range([0, width]);
    var yaxis = d3.scaleLinear()
        .domain([0, 100])
        .range([height, 0]);
    svg2.append('g')
        .attr("transform", "translate(0, " + height + ")")
        .call(d3.axisBottom(xaxis));
    svg2.append('g')
        .call(d3.axisLeft(yaxis));
```