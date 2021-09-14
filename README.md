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

1. Create a new react app and add the following dependencies:

   - [`@react-three/fiber`](https://www.npmjs.com/package/@react-three/fiber)
   - [`@react-three/drei`](https://www.npmjs.com/package/@react-three/drei)
   - [`three`](https://www.npmjs.com/package/three)

   Since we are using [WebGL](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) we will need a `canvas` element. Luckily we can import it from `@react-three/fiber` and add it to our react app.

   ```javascript
   import { Canvas } from "@react-three/fiber";

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

   body {
     margin: 0;
   }

   canvas,
   .App {
     width: 100%;
     height: 100%;
   }

   canvas {
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

   Now let's create our cube component. Copy the snippet into a react component that accepts `color`, `width`, `height` & `depth` as props.

   ```javascript
   <Cube width={1} height={1} depth={1} color="hotpink" />
   ```

   Now you probably still have a black cube, and that is because we haven't added any [lights](https://threejs.org/docs/#api/en/lights/AmbientLight) to our scene yet. go ahead and add `<ambientLight/>` inside your canvas (optionally you can also add a [`<pointLight/>`](https://threejs.org/docs/#api/en/lights/PointLight) aswell, it can be positioned via the `position` prop, you will need to provide it with an array containing a [Vector3](https://threejs.org/docs/#api/en/math/Vector3), meaning a x, y & z value).
   You should now see the color of your cube.

   `drei` that we installed is a useful collection of helpers for `@react-three/fiber` try importing and adding `<OrbitControls/>` to your scene.

   ```javascript
   import { OrbitControls } from "@react-three/drei";
   ```

   It should look something like this:

    <p align="center">
      <img src="/img/Lesson_1.gif" width="80%">
    </p>

2. Continue working on the previous assignment. We are going to animate our `<Cube />`. First add [`@react-spring/three`](https://www.npmjs.com/package/react-spring) to your dependencies.

   ```javascript
   import { useSpring, a } from "@react-spring/three"

     //...
     const props = useSpring({
       scale: clicked ? [1.5, 1.5, 1.5] : [1, 1, 1],
     });

   return (
     <a.mesh scale={props.scale}>
     { ... }
     </a.mesh>
   )
   ```

   Now when we add `a.` to our mesh (i.e `<a.mesh/>`) some of it's properties can be animated with react-spring, check out the documentation for [`useSpring`](https://react-spring.io/hooks/use-spring) and then see if you can add an `onClick` that changes the `scale` property of the mesh and a hover effect that changes the `color` of the cube.

   Here you can find information about [`pointer events`](https://docs.pmnd.rs/react-three-fiber/API/events).

   The scale property accepts an array containing a [Vector3](https://threejs.org/docs/#api/en/math/Vector3)

   Don't forget to update your material `<a.meshStandardMaterial/>`

   It should look something like this:

   <p align="center">
     <img src="/img/Lesson_2.gif" width="80%">
   </p>

3. **Extra:** Another way to animate our objects rather than using `@react-spring/three` is utilizing the [`useFrame`](https://docs.pmnd.rs/react-three-fiber/tutorials/basic-animations) hook from `@react-three/fiber`. See if you can add a simple animation to your `<Cube />` like the one in the screenshot below.

4. **Extra:** See if you can add some shadows to your scene. A good place to start to figure out how to do so is [`softShadows`](https://docs.pmnd.rs/drei/shaders/soft-shadows). Remember to add something that the shadow can be cast on.

   Here's an example how it could look with shadows and an animation:

   <p align="center">
     <img src="/img/Extra.gif" width="80%">
   </p>
