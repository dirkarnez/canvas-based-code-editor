[canvas-based-code-editor](https://dirkarnez.github.io/canvas-based-code-editor/)
=================================================================================
Use https://github.com/millermedeiros/js-signals/wiki/Examples for interactivity

### Yoga ([Playground | Yoga](https://www.yogalayout.dev/playground))
```jsx
<Layout config={{useWebDefaults: false}}>
  <Node style={{width: 250, height: 475, padding: 10}}>
    <Node style={{flex: 1, rowGap: 10}}>
      <Node style={{flex: 1}} />
      <Node
        style={{
          position: "absolute",
          width: "100%",
          bottom: 0,
          height: 64,
          flexDirection: "row",
          alignItems: "center",
          justifyContent: "space-around",
        }}
      >
        <Node style={{height: 40, width: 40}} />
        <Node style={{height: 40, width: 40}} />
        <Node style={{height: 40, width: 40}} />
        <Node style={{height: 40, width: 40}} />
      </Node>
    </Node>
  </Node>
</Layout>
```
### On https://layout.pixijs.io/docs/guides/guide/quick-start/
```javascript
import { Application, Assets, Container, Graphics, Text, SplitText } from 'pixi.js';
// import the library before creating your pixi application to ensure all mixins are applied
import '@pixi/layout';

(async () => {
    // Create a new application
    const app = new Application();

    await app.init({ background: '#1099bb', resizeTo: window });
    document.body.appendChild(app.canvas);
    const texture = await Assets.load('https://pixijs.com/assets/bunny.png');

    // Create a new layout for the stage that will fill the entire screen
    // and center the content
    app.stage.layout = {
        width: app.screen.width,
        height: app.screen.height,
        justifyContent: 'center',
        alignItems: 'center',
    };

    // Create and add a container to the stage that will be used to hold the bunnies
    // The container will be centered in the stage and will have a gap of 4 pixels
    // between the bunnies
    // The container will also wrap the bunnies if there are too many to fit in a single row
    const container = new Container({
        layout: {
            width: '100%',
            height: '100%',
            justifyContent: 'start',
            flexDirection: 'row',
            alignContent: 'start',
            flexWrap: 'wrap',
            gap: 4,
        },
    });

    app.stage.addChild(container);
    const text = new SplitText({
        text: "Hello",
        style: {
            fontFamily: 'monospace',
            fontSize: 24
        },
        lineAnchor: 0.5,  // Center of each line
        // wordAnchor: { x: 0, y: 0.5 },  // Left-center of each word
        // charAnchor: { x: 0.5, y: 0.5 },  // Bottom-center of each character
        autoSplit: true  // Auto-update segments on text/style changes
    });

    text.chars.forEach((char, i) => {
        // console.log(JSON.stringify(char));
        const obj = new Graphics()
            .rect(0, 0, 1.8, char.height) // Create a rectangle with dimensions 200x100
            .fill('red'); // Fill the rectangle with a red color
        obj.x = i * char.width;
        container.addChild(obj);
    });
        
    // Add the bunny to the container
    container.addChild(text);
})();


```
