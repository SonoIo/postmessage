
# Post message

Utility to communicate between windows.postMessage with IFrame and window.parent

## How to

### Server

```
#!javascript
var server = new PostMessage({
	target: iframe.contentWindow,
	origin: window.location.protocol + '//' + window.location.host,
	destination: window.location.protocol + '//iframehost' + ':' + window.location.port
});
server.emit('myevent', { foo: 'bar' }, function (data) {
	console.log(data); // Out: 'done!'
});
```

### Client

```
#!javascript
var client = new PostMessage({
	target: window.parent,
	origin: window.location.protocol + '//' + window.location.host,
	destination: window.location.protocol + '//pagehost' + ':' + window.location.port
});
client.on('myevent', function (data, fn) {
	console.log(data); // Out: { foo: 'bar' }
	fn('done!');
});
```

## License

MIT
