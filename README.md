# Simple bunyan console logging stream

Logs [bunyan](https://github.com/trentm/node-bunyan) message text to STDOUT.
Output is directed to STDERR if a message's level ("fatal" (60),  "error" (50),  "warn" (40),  "info" (30),  "debug" (20), "trace" (10))
is greater or equals the value set by option `stderrThreshold`:

````
var bunyan = require('bunyan')
var consoleStream = require('bunyan-console-stream')
// ...

var stream_options = {
  stderrThreshold: 40 // log warning, error and fatal messages on STDERR
  displayStack: true // log error stack, if present
}

var logger = bunyan.createLogger({
  name: loggerName,
  streams: [
    {
      type: 'raw',
      stream: consoleStream.createStream(stream_options)
    },
    //...
  ]
})
// ...

logger.info('Success!');   // STDOUT output: INFO: Success!         			        
logger.error('Fail.');     // STDERR output: ERROR: Fail.

````
