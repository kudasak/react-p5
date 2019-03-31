# react-p5

This Component lets you integrate p5 Sketches into your React App.

### Installation

```bash
npm i react-p5
```

### Usage

```js
import React, { Component } from "react";
import ReactP5 from "react-p5";

export default class App extends Component {
    constructor(props) {
        super(props);
        this.state = {
            x: 50,
            y: 50
        };
    }
    setup = (p5, parent) => {
        p5.createCanvas(500, 500).parent(parent);
    };
    draw = p5 => {
        p5.background(0);
        p5.ellipse(this.state.x, this.state.y, 70, 70);
    };
    windowResized = p => {
        p.resizeCanvas(200, 200);
    };
    incrementX = e => {
        this.setState(s => ({ x: s.x + 10 }));
    };
    render() {
        return (
            <div>
                <h1>My App</h1>
                <ReactP5 setup={this.setup} draw={this.draw} windowResized={this.windowResized} />
                <span>X: {this.state.x}</span>
                <span>Y: {this.state.y}</span>
                <button onClick={this.incrementX}>X+10</button>
            </div>
        );
    }
}
```