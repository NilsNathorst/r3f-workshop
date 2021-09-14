<img src="https://camo.githubusercontent.com/ea9046fc37789f259415303c57edeab46aa54af1/68747470733a2f2f692e696d6775722e636f6d2f4f77784a5166782e676966" width="100%">

# 12 - React-Three-Fiber

[React-Three-Fiber](https://medium.com/better-programming/react-three-fiber-build-3d-for-the-web-with-react-and-webgl-easily-c0df8801292) or R3F is a powerful React renderer for three.js scenes, both for the web and with React Native.

- :books: Documentation

  - [@react-three/fiber](https://docs.pmnd.rs/react-three-fiber/getting-started/introduction)

  - [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)

  - [@react-three/drei](https://drei.pmnd.rs/?path=/story/performance-adaptive--adaptive-scene-st)

  - [@react-spring/three](https://react-spring.io/)

- :link: Links

  - [Three JS examples](https://threejs.org/)

  - [React three fiber examples](https://codesandbox.io/examples/package/react-three-fiber)

- :headphones: Screencasts

  - [`Basics with Paul Henschel`](https://www.youtube.com/watch?v=1rP3nNY2hTo) the creator of r3f & react-spring

## Exercises

1. Now it's time to create a new project, just like in step 1.

   Copy the `Planets` array from the [`Planets.js`](resources/Planets.js) file.
   Iterate over the Planets and create a [`<sphereBufferGeometry/>`](https://threejs.org/docs/?q=sph#api/en/geometries/SphereGeometry) for each one. Use the `size` property to determine it's radius, pass it as the first parameter of `args`.
   (tip: if they are way too big, use the scale attribute of the mesh to make them smaller).

   If we imagine position `[0,0,0]` as the Sun's position place the planets accordingly using their `distanceFromSun` property along the x-axis. (I'll let you figure out how to add a Sun on your own)

   ```javascript
   <mesh position={[ ... ]}>
   ```

2. Continue working on the previous assignment. Now let's animate the planets. Each planet has a `orbitalVelocity` property. Use this to determine how fast they should orbit around the Sun.

   I suggest placing each of the planets within a `<group>` element since the groups position will default to `[0,0,0]` and we can use that as a pivot point when we rotate the planet.

   You will also need to use the `useFrame` hook from `@react-three/fiber` and add a reference to your mesh or group to then be able to update it's properties each frame.

   ```javascript
   const mesh = useRef();

   useFrame(() => {
     /* Example: move something sideways 
       mesh.current.position.x += 1
     */
   });
   ```

   It should look something like this:

   <p align="center">
     <img src="/img/Lesson_3.gif" width="80%">
   </p>

3. **Extra:** Check out [drei's documentation](https://github.com/pmndrs/drei#html) and add a `<Html/>` to each of the planets containing the planet's name!

4. **Extra:** If you still have time, continue on your solar system and see what else you can add! Perhaps lines indicating the orbit of the planets, some info about the planets triggered when clicking them or maybe check out some [texture loaders](https://drei.pmnd.rs/?path=/story/loaders-texture--use-texture-scene-st) and add some textures to the planets!
