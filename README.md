![screenshot](assets/logo.png)

### JavaScript Voice Application Framework

Write your own voice apps and assistants with an easy-to-learn JavaScript API!


## About

Bumblebee is a set of libraries, tools, and methodologies that enables JavaScript developers to write their own conversational voice assistants in either NodeJS or on the web.

The open source technologies that Bumblebee uses are:

- [NodeJS](https://nodejs.org/en/) - V8 JavaScript engine
- [ElectronJS](https://www.electronjs.org/) - JavaScript desktop application framework
- [Mozilla DeepSpeech](https://github.com/mozilla/DeepSpeech) - Tensorflow-based speech-to-text processing
- [Picovoice Porcupine](https://github.com/Picovoice/porcupine) - JavaScript hotword detection
- [meSpeak](https://www.masswerk.at/mespeak/) - JavaScript text-to-speech library

Bumblebee builds upon these technologies by making them easier to use and tying them
together into an integrated voice application API.  Because these systems
run locally without any cloud services, stand-alone privacy-focused always-on voice applications can
finally be realized.

The Bumblebee project includes a voice app server console ([bumblebee-electron-app](https://github.com/jaxcore/bumblebee-electron-app)),
which automatically installs and sets up DeepSpeech, and runs the bumblebee websocket service that
voice applications can connect to. The applications run independently of the bumblebee server,
and use a websocket API to connect and communicate by receiving speech-to-text results
and hotword commands, or issuing text-to-speech instructions.

There are limitless ways to expand Bumblebee's capabilities by writing new applications that control
devices or services on a home network, retrieve data from the internet, and anything else you can think of.
And as you will see, they are both ***EASIER*** and ***MORE FUN*** to write than you think.

Bumblebee voice apps are small, simple, single file scripts. They can be shared easily between
systems and build upon eachother to create larger and smarter voice applications.
By associating a voice app with a hotword, your app becomes a voice assistant
that can be called upon at any time.

## Install Bumblebee

The [latest release](https://github.com/jaxcore/bumblebee/releases) is **COMING SOON**:

- MacOSX: [jaxcore-bumblebee-0.0.1-darwin-x64.dmg]()
- Linux: [jaxcore-bumblebee-0.0.1-linux-x64.tar.gz]()
- Windows [jaxcore-bumblebee-0.0.1-win-x64.tar.gz]()
- or install from [source](https://github.com/jaxcore/bumblebee-electron-app)

Disk Space Requirements:

- Bumblebee Application: 450 MB (approx.)
- DeepSpeech English model: 1.4 GB

![screenshot](assets/screenshot.png)

## Hello World

To get started, create the most simple Bumblebee app possible, a "Hello World" voice application.

Create a new directory and NPM project:

```
mkdir helloworld
cd helloworld
npm init
npm install jaxcore-bumblebee
```

Create a new file named `helloworld.js`:

```
const Bumblebee = require('jaxcore-bumblebee');

class HelloWorldApp extends Bumblebee.Application {
	constructor() {
		super(...arguments);
	}

	async loop() {
		this.console('Say "Hello World"');

		let recognition = await this.recognize();
		this.console(recognition);

		if (recognition.text === 'hello world') {
			await this.playSound('okay');
			await this.say('Hello World');
		}
		else {
			await this.playSound('error');
		}
	}
}

Bumblebee.connectApplication(HelloWorldApp, {
	name: "Hello World",
	autoStart: true
});
```

Run the voice app:

```
node helloworld.js
```

With the speakers and microphone turned on, you will be able to talk to this application and listen to it's responses.  It doesn't do very much yet, if it hears you say "hello world' it will respond by making a beep sound and also saying "hello world".

This program will run continuously until the NodeJS script is closed using `Command+C` or `Control+C` and it can be started and stopped at any time.

## Documentation (Coming Soon)

This is a brand new project with much more to come.  

Use github's "watch" feature to stay tuned for updates!