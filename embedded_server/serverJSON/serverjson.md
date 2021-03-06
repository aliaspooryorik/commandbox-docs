# server.json

Every time you start a server, the settings used to start it are saved in a `server.json` file in the web root.  Any parameters that aren't supplied to the `start` command are read from this file (if it exists) and used as defaults.  Here are the possible properties for a `server.json` file:

**`/server.json`**
```javascript
{
	name : '',
	openBrowser : true,
	startTimeout : 240,
	stopsocket : 0,
	debug : false,
	trayicon : '/path/to/trayicon.png',
	trayOptions : [
		{
			"label":"Foo",
			"action":"openbrowser",
			"url":"http://${runwar.host}:${runwar.port}/foobar.cfm",
			"disabled":false,
			"image":"/path/to/image.png"
		}
	],
	jvm : {
		heapSize : 512,
		args : ''
	},
	web : {
		host : '127.0.0.1',
        webroot : 'src/cfml'
		directoryBrowsing : true,
        aliases : {
          "/foo" : "../bar",
          "/js" : "C:\static\shared\javascript"
      },
        errorPages : {
          "404" : "/path/to/404.html",
          "500" : "/path/to/500.html",
          "default" : "/path/to/default.html"
        },
        welcomeFiles : 'index.cfm,main.cfm,go.cfm'
		http : {
			port : 8080,
			enable : true
		},
		ssl : {
			enable : false,
			port : 443,
			cert : '',
			key : '',
			keyPass : ''
		},
		rewrites : {
			enable : true,
			config : '/path/to/config.xml'
		}
	},
	app : {
		logDir : '',
		libDirs : '',
		webConfigDir : '',
		serverConfigDir :'',
		webXML : '',
		WARPath : '',
		cfengine : 'lucee@5.x',
		serverHomeDirectory : ''
	},
	runwar : {
		args : ''
	}
}
```

## Server Setting Order

Settings are loaded in this order:

1. Typed by the user into the `start` command parameters
2. Read from `server.json`
3. Global defaults in the `server.defaults` config setting
3. Internal defaults from the `ServerService`


