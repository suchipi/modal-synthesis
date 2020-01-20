# modal-synthesis

This packages uses the Web Audio API to create a synthesizer for a modal sound.

You can use it to synthesize your own modal sounds, but I don't have documentation for how to do that yet, sorry :(

It involves looking at a spectrogram and identifiying the most important features of the sound.

Eventually I want to make a tool to automate it. But I'm no DSP expert, so it will take me a while.

If you know what you're doing, you can probably figure out how to make your own data, but in the meantime, you can use some samples I included.

## Usage

```js
const { makeModalSynthesis } = require("modal-synthesis");
const { glassHit } = require("modal-synthesis/samples");

const audioContext = new AudioContext();

const glass = makeModalSynthesis(glassHit, audioContext).makeModel({
  // You can use Math.random in here to vary the sound a bit
  amplitudeMultiplier: () => 1,
  frequencyMultiplier: () => 1,
  decayMultiplier: () => 1,
});

glass.outputNode.connect(audioContext.destination);

// Hit the glass
glass.excite();
```

## License

MIT
