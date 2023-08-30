# Learning the before and after pseudo-elements and concepts of animation.

The `sun` has Before and After elements and also have scale animation to pulsate.

The `ship` also have animation and you can stop it if you hover them (`animation-play-state`, see below to understand this and other animation properties)

![ezgif com-video-to-gif (4)](https://github.com/vanesascode/sea-scene-css-animation-before-after/assets/131259155/62eff44b-a20c-41d9-b788-2b9e1e83e5a4)

## 🔷 Before and After pseudo-elements:

They allow you to `insert` content before or after an element's content. They are commonly used for adding decorative elements or icons to HTML elements without modifying the actual HTML structure.

You can use actual content:

```
.my-element::before {
  content: "Before";
  /* other styles */
}

.my-element::after {
  content: "After";
  /* other styles */
}

```

Or just elements that help your visuals:

```
.sun {
  position: relative;
  width: 50px;
  height: 50px;
  border-radius: 50%;
  background-color: #df7606;
  animation: pulsate 2s ease-in-out infinite;
  z-index: 2;
}

.sun::before,
.sun::after {
  content: "";
  position: absolute;
  border-radius: 50%;
  animation: pulsate 5s ease-in-out infinite;
  z-index: 2;
}
```

Notice how the ::before and ::after elements have a position `absolute`, while the reference element has a position `relative`.

---

## 🔷 Animations:

CSS animations allow you to create dynamic and engaging effects on web pages. They work by defining a set of keyframes that specify how an element should change its appearance over time.

STEPS:

1. `Define the animation`: First, you need to specify the animation properties using the @keyframes rule. This rule allows you to define different stages or keyframes of the animation, along with the styles that should be applied at each stage.

```
@keyframes myAnimation {
  0% {
    background-color: red;
    transform: translateX(0);
  }
  50% {
    background-color: blue;
    transform: translateX(200px);
  }
  100% {
    background-color: green;
    transform: translateX(0);
  }
}
```

2. `Apply the animation`: Once the animation is defined, you can apply it to an element using the animation property. This property accepts various values to control the animation's duration, timing function, delay, and iteration count.

```
.my-element {

  animation-name: myAnimation;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: 0s;
  animation-iteration-count: infinite;
  animation-fill-mode: forwards;
  animation-direction: alternate;
  animation-play-state: running;
}
```

In this example, the animation will run for 2 seconds, have an easing effect, start immediately, and repeat infinitely.

---

#### 🔹 animation-timing-function

The animation-timing-function property in CSS allows you to control the pace or speed of an animation.

1.  `ease` : This is the default timing function. It starts slow, accelerates through the middle, and slows down again towards the end. It creates a smooth and natural-looking animation.

2.  `linear` : This timing function produces a constant speed throughout the animation. It does not have any acceleration or deceleration.

3.  `ease-in` : The animation starts slowly and gradually accelerates towards the end. It creates a smooth and gentle entrance effect.

4.  `ease-out` : The animation starts quickly and gradually decelerates towards the end. It creates a smooth and gentle exit effect.

5.  `ease-in-out` : This timing function combines the ease-in and ease-out functions. It starts slowly, accelerates in the middle, and slows down towards the end.

6.  `step-start` : This timing function creates a sudden jump to the next keyframe at the beginning of the animation. It does not provide any intermediate values between keyframes.

7.  `step-end` : This timing function holds the initial keyframe value until the animation reaches the end, where it jumps to the final keyframe value. It also does not provide any intermediate values.

8.  `steps(n)` : This timing function allows you to define the number of steps ( n ) you want the animation to take. It divides the animation into equal steps and holds the intermediate values for an equal duration.

9.  `cubic-bezier(x1, y1, x2, y2)` : This timing function provides a custom cubic Bezier curve for the animation. You can specify the control points ( x1 , y1 , x2 , y2 ) to create your own acceleration and deceleration effects.

---

#### 🔹 animation-iteration-count

The animation-iteration-count property in CSS allows you to specify the number of times an animation should run.

1.  `infinite` : This value makes the animation repeat indefinitely. It will continue to run until it is paused or stopped.

2.  <number> : You can specify a specific number to determine how many times the animation should repeat. For example, animation-iteration-count: 3; will make the animation repeat three times.

3.  `initial` : This value sets the animation-iteration-count property to its default value, which is usually 1 .

4.  `inherit` : This value inherits the animation-iteration-count value from the parent element.

---

#### 🔹 animation-fill-mode

The animation-fill-mode property in CSS determines how an element's styles are applied before and after an animation. It controls the styles of an element before the animation starts and after it ends.

By default, an animation does not affect an element's styles before it starts or after it ends. However, the animation-fill-mode property allows you to specify how the element should appear in those stages.

1.  `none` : This is the default value. It means that the element's styles are not affected by the animation before or after it runs.

2.  `forwards` : With this value, the element retains the styles of the last keyframe after the animation ends. In other words, it holds the animation's final state.

3.  `backwards` : When using this value, the element applies the styles of the first keyframe before the animation starts. It means that the element will appear as if the animation has already played from the beginning.

4.  `both` : This value combines the effects of forwards and backwards . The element retains the styles of the first keyframe before the animation starts and holds the styles of the last keyframe after the animation ends.

Remember that animation-fill-mode only affects the styles of an element; it does not impact the actual animation itself.

---

#### 🔹 animation-play-state

The animation-play-state property in CSS controls whether an animation is running or paused. It allows you to start, stop, or pause an animation dynamically.

1.  `running` : This is the default value. It indicates that the animation is running.

2.  `paused` : This value pauses the animation at its current state. The animation will remain in that state until it is resumed.

By changing the value of animation-play-state , you can control the playback of an animation. For example, you can use JavaScript to toggle the animation-play-state property between running and paused to start or pause an animation based on user interactions or specific events.

Example:

```

@keyframes myAnimation {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

.my-element {
  animation-name: myAnimation;
  animation-duration: 2s;
  animation-play-state: running;
}

.my-element:hover {
  animation-play-state: paused;
}

```

---

#### 🔹 animation-play-state

The animation-direction property in CSS determines the direction of an animation. It controls whether the animation should play forward, backward, or alternate between forward and backward.

1.  `normal` : This is the default value. It indicates that the animation should play forward from the beginning to the end.

2.  `reverse` : This value plays the animation backward, starting from the end and going back to the beginning.

3.  `alternate`: With this value, the animation plays forward and then backward in a continuous loop. It alternates between each iteration.

4.  `alternate-reverse` : This value is similar to alternate , but it starts by playing the animation backward and then forward.

---

#### 🔹 Shorthand notation

When it comes to combining multiple CSS properties in one line, shorthand notation is commonly used. Take the following example:

```
.my-element {
  animation-name: myAnimation;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: 0s;
  animation-iteration-count: infinite;
  animation-direction: alternate;
  animation-fill-mode: forwards;
  animation-play-state: running;
}
```

#### 🔹 You can do this:

```
.my-element {
  animation: myAnimation 2s ease-in-out 0s infinite alternate forwards running;
}
```
