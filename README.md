# ShLib Svg
  
SVG tool with loading sprites from external files. Written in ECMA 6 vanilla JS
(uses StealJS to compile). 

Fast, small, no runtime dependencies.

Examples in [index.html](index.html) and [index.js](index.js)

## Draw a simple rect

```
Svg.addElement(svg, "rect", {x: 10, y: 10, width: 50, height: 50, fill: "red"});
```

## Draw Elements from Sprite (sprite.svg)

```
Svg.loadSprite("./assets/sprite.svg", ["star", "circle", "triangle", "smiley"]);
Svg.addElement(svg2, "use", {"href": "#triangle", x: 10, y: 10});
Svg.addElement(svg2, "use", {"href": "#smiley", x: 100, y: 10});
Svg.addElement(svg2, "use", {"href": "#smiley", transform: "translate(200,10) scale(0.5)"});
```

## Animate Elements from Sprite

```
let star = Svg.addElement(svg3, "use", {"href": "#star", x: -47, y: -45, transform: "translate(60,60)"});
Svg.addElement(star, "animateTransform", {
    attributeName: "transform", type: "rotate",
    values: "0 0 0; 360 0 0", additive: "sum", dur: "6s", repeatCount: "indefinite"
});
Svg.addElement(star, "animateMotion", { dur:"10s", values:"0,0; 250,0; 0,0", repeatCount:"indefinite" });
```