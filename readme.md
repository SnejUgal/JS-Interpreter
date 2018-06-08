# `es-interpreter`
A fork of [JS-Interpreter] with ES 2015 standard library (not syntax yet!) (in development) and other additional features.

## Usage
```js
import Interpreter from "es-interpreter";

// This is the code we'll be running
const code = `
  var fibonacci = function (n) {
    var a = 1;
    var b = 1;
    var sum;

    for (var i = 0; i < n; i++) {
      sum = a + b;
      a = b;
      b = sum;
    }

    return sum;
  }

  log(fibonacci(23));
`;

// We need to init the log function to see the output
const init = (interpreter, scope) => {
  const log = interpreter.createNativeFunction((data) => {
    console.log(data);
  });

  interpreter.setProperty(scope, `log`, log);
};

const interpreter = new Interpreter(code, init);

interpreter.run();
```

## ES 2015?
Yes. But only the standard library right now. We're not going to support the ES 2015 syntax at the moment, but we're going to include the standard library of ES 2015. For ES 2015 syntax, you can use Babel.

## What about other editions of EcmaScript?
We'll be supporting newer versions after we implement older versions completely.

## May I use it in stable versions?
You may, but you shouldn't now. We may be making a lot of changes to the API that may be breaking in minor versions until v1.0.0.

[JS-Interpreter]: https://github.com/NeilFraser/JS-Interpreter