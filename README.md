<img src="https://camo.githubusercontent.com/ea9046fc37789f259415303c57edeab46aa54af1/68747470733a2f2f692e696d6775722e636f6d2f4f77784a5166782e676966" width="100%">

# Workshop - React-Three-Fiber

[React-Three-Fiber](https://medium.com/better-programming/react-three-fiber-build-3d-for-the-web-with-react-and-webgl-easily-c0df8801292) or R3F is a powerful React renderer for three.js scenes, both for the web and with React Native.

- :scissors: Examples

- [Three JS examples](https://threejs.org/)

- [React three fiber examples](https://codesandbox.io/examples/package/react-three-fiber)

- :books: Documentation

- [react-three-fiber](https://github.com/react-spring/react-three-fiber)

- [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)

- [drei](https://drei.react-spring.io/?path=/story/abstractions-billboard--billboard-st)

- [react-spring](https://www.react-spring.io/docs/hooks/basics)

- :link: Links

- [Three JS examples](https://threejs.org/)

- [React three fiber examples](https://codesandbox.io/examples/package/react-three-fiber)

- :headphones: Screencasts

- [`Basics with Paul Henschel`](https://www.youtube.com/watch?v=1rP3nNY2hTo) the creator of r3f & react-spring

## Exercises

1. Create a new react app and add the following dependencies:
   [`react-three-fiber`](https://www.npmjs.com/package/react-three-fiber)
   [`drei`](https://www.npmjs.com/package/drei)
   [`three`](https://www.npmjs.com/package/three)

Since we are using [WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) we will need a `canvas` element. Luckily we can import it from `react-three-fiber` and add it to our react app.

```javascript
import { Canvas } from "react-three-fiber";

export default function App() {
  return (
    <div className="App">
      <Canvas>
      // 3D Stuff
      { ... }
      </Canvas>
    </div>
  );
}
```

I also recommend adding some css to make our canvas a bit bigger.

```css
#root {
  width: 100vw;
  height: 100vh;
}

canvas {
  height: 100%;
  width: 100%;
  background: dodgerblue;
}
```

Let's begin! whenever we want to create a 3D shape in react three fiber we use the `<mesh>` element. So for instance if we want a pink cube with a side length of 1 we simply write:

```javascript
<mesh>
  <boxBufferGeometry attach="geometry" args={[1, 1, 1]} />
  <meshStandardMaterial attach="material" color="hotpink" />
</mesh>
```

Copy the snippet into a react component that accepts `color`, `width`, `height` & `depth` as props.

```javascript
<Cube width={1} height={1} depth={1} color="hotpink" />
```

Now you probably still have a black cube, and that is because we haven't added any [lights](https://threejs.org/docs/#api/en/lights/AmbientLight) to our scene yet. go ahead and add `<ambientLight/>` inside your canvas (optionally you can add a [`<pointLight/>`](https://threejs.org/docs/#api/en/lights/PointLight) aswell, it can be positioned via the `position` prop). No imports needed! Now you should be able to see the color you assigned to your cube.

`drei` is a useful collection of helpers for `react-three-fiber` try adding the `<OrbitControls/>` to your scene.

It should look something like this:

<p align="center">
  <img src="/img/Lesson_1.gif" width="80%" alt="box with orbitControls">
</p>

2. Continue working on the previous assignment. Now we are going to animate our `<Cube />`. First add [`react-spring`](https://www.npmjs.com/package/react-spring) to your dependencies.

```javascript
import { useSpring, a } from "react-spring/three"

  //...

return (
  <a.mesh>
  { ... }
  </a.mesh>
)
```

Now if we add `a.` to our mesh it can be animated with react-spring, check out the documentation for useSpring and then see if you can add a hover effect that changes the `color` of the cube and an `onClick` that changes the `scale` property of the mesh.

It should look something like this:

<p align="center">
  <img src="/img/Lesson_2.gif" width="80%" alt="two boxes changing size">
</p>

3. Now it's time to create a new project, just like in step 1.

Copy the `Planets` array from the [`Planets.js`](resources/Planets.js) file.
Iterate over the Planets and create a `<sphereBufferGeometry/>` for each one.
Use the `size` property to determine it's radius (tip: if they are way too big, use the scale attribute of the mesh to make them smaller). Feel free to add a Sun to the scene aswell. If we let position `[0,0,0]` represent the Sun's position. Position the planets accordingly using their `distanceFromSun` property.

4. Continue working on the previous assignment. Now let's animate the planets. Each planet has a `orbitalVelocity` property. Use this to determine how fast they should orbit around the Sun.

I suggest placing the planets within a `<group>` element since the groups position will default to `[0,0,0]` and we can use that as a pivot point when we rotate the planet.

You will also need to use the `useFrame` hook from `react-three-fiber` and add a reference to your mesh or group to then be able to update it each frame.

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
  <img src="/img/Lesson_3.gif"  width="80%" alt="solar system linear">
</p>

**Extra:** 5. Check out [drei's documentation](https://drei.react-spring.io/?path=/story/abstractions-billboard--billboard-st) and add a `<Html/>` to each of the planets containing the planet's name!

**Extra:** 6. If you still have time, continue on your solar system and see what else you can add! Perhaps lines indicating the orbit of the planets, some info about the planets triggered when clicking them or maybe check out some [texture loaders](https://drei.react-spring.io/?path=/story/loaders-cubetexture--use-cube-texture-loader-scene-st) and add some textures to the planets!
