<img src="https://camo.githubusercontent.com/ea9046fc37789f259415303c57edeab46aa54af1/68747470733a2f2f692e696d6775722e636f6d2f4f77784a5166782e676966" width="100%">

# Workshop - React-Three-Fiber

[React-Three-Fiber](https://medium.com/better-programming/react-three-fiber-build-3d-for-the-web-with-react-and-webgl-easily-c0df8801292) or R3F is a powerful React renderer for three.js scenes, both for the web and with React Native.

- :scissors: Examples

  - [Three JS examples](https://threejs.org/)

  - [React three fiber examples](https://codesandbox.io/examples/package/react-three-fiber)

- :books: Documentation

  - [react-three-fiber](https://inspiring-wiles-b4ffe0.netlify.app/)

  - [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)

  - [drei](https://drei.react-spring.io/?path=/story/abstractions-billboard--billboard-st)

  - [react-spring](https://www.react-spring.io/docs/hooks/basics)

- :link: Links

  - [Three JS examples](https://threejs.org/)

  - [React three fiber examples](https://codesandbox.io/examples/package/react-three-fiber)

- :headphones: Screencasts

  - [`Basics with Paul Henschel`](https://www.youtube.com/watch?v=1rP3nNY2hTo) the creator of r3f & react-spring

## Exercises

1. Create a new react app and add the following dependencies: [`react-three-fiber`](https://www.npmjs.com/package/react-three-fiber) [`drei`](https://www.npmjs.com/package/drei)

First we will need a `<Canvas />` element to draw on. import it from `drei` and add it in Index.js.

Try adding `<OrbitControls/>` to your scene! you should now be able to move around your scene.

It should look something like this:

  <p align="center">
    <img src="https://via.placeholder.com/350x150" width="80%" alt="box with orbitControls">
  </p>
2. Continue working on the previous assignment. Add a `<Plane />` beneath your box and add some lights! (`<directionalLight/>`).

It should look something like this:

  <p align="center">
    <img src="https://via.placeholder.com/350x150" width="80%" alt="box with floor">
  </p>
3. Continue working on the previous assignment. Add an `onClick` to your `<Box>` and see if you can change the color and size of the `<Box>`.

It should look something like this:

  <p align="center">
    <img src="https://via.placeholder.com/350x150" width="80%" alt="two boxes changing size">
  </p>
4. Now it's time to create a new project, just like in step 1. This time we will also add [`react-spring`](https://www.npmjs.com/package/react-spring) to ur dependencies which will allow us animate our shapes.

Copy the `Planets` array from the [`Planets.js`](resources/Planets.js) file.
Iterate over the Planets and create a `<sphereBufferGeometry/>` for each one. Use the `size` property to determine it's radius (tip: the ratios between the planets sizes might not look great, try to figure out a way to keep them somewhat proportionate while still presenting them nicely).

If we let position `[0,0,0]` represent the Sun's position. Position the planets accordingly using their `distanceFromSun` property.

It should look something like this:

  <p align="center">
    <img src="https://via.placeholder.com/350x150" width="80%" alt="solar system linear">
  </p>

5. Continue working on the previous assignment. Now let's animate the planets. Each planet has a `orbitalVelocity` property. Use this to determine how fast they should orbit around the Sun.

**Extra:** 6. Check out [drei's documentation](https://drei.react-spring.io/?path=/story/abstractions-billboard--billboard-st) and add a `<Html/>` to each of the planet containing the planet's name!

**Extra:** 7. If you still have time, continue on your solar system and see what else you can add! Perhaps lines indicating the orbit of the planets, some info about the planets triggered when clicking them or maybe add some textures to the planets surface?
