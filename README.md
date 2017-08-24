# nightwatchWin10Sample
Clean project running nightwatch js under Win 10 environment


### Environment
* install jdk for running selenium server
* install node.js
* install python (2.x version)
* install Visual Studio and create and C++ project to install the necessary packages.(see the [Install issue with NPM](https://github.com/socketio/socket.io/issues/2277) below.)
* download selenium standalone server
* download webdriver (chrome, firefox, IE)

### Step1 Install package
```{r, engine='bash', count_lines}
$ npm install socket.io
$ npm install -g npm
$ npm install -g nightwatch
```

### Step2 Create Repo
1. Create `MyRepoName`
2. Copy npm & nightwatch folders into `MyRepoName`
3. Create folders 
* `selenium` (for seleunim standalone jar file)
* `reports` (for test reports )
* `webdriver` (where you place the webdriver files)
* `tests` (where you place your test scripts)

### Step3 Set Config
1. copy `nightwatch.json` from nightwatch/bin into `MyRepoName`.
2. touch a file `nightwatch.js` points to `runner.js`
```js
require('C:/MyRepoName/nightwatch/bin/runner.js');
```
3. set selenium server
* `start_process` as true will automatically launch the selenium server. Otherwise you have to launch the selenium server manually by using command.
```{r, engine='bash', count_lines}
$ java -jar selenium/selenium-server-standalone.jar
```
* set `server_path` where you place the selenium standalone server file
```json
"selenium": {
    "start_process": true,
    "server_path": "selenium/selenium-server-standalone.jar",
    "log_path": "",
    "host": "127.0.0.1",
    "port": 4444,
    "cli_args": {
        "webdriver.chrome.driver": "webdriver/chromedriver.exe",
        "webdriver.ie.driver": "",
        "webdriver.firefox.profile": ""
    }
},
```

4. set browser as chrome
```json
"desiredCapabilities" : {
  "browserName" : "chrome",
  "javascriptEnabled" : true,
  "acceptSslCerts" : true,
  "chromeOptions" : {
    "args" : ["start-fullscreen"]
  }
}
```

5. for more browswer settings. please refereance [[camel's Blog] Nightwatch.js debug 血淚史](https://blog.camel2243.com/2017/06/17/test-nightwatch-debug-%E8%A1%80%E6%B7%9A%E5%8F%B2/).
### Step4 Run test
Copy google.js as test script from `nightwatch\examples\tests` to `tests` folder.
```{r, engine='git', count_lines}
$ nightwatch tests/google.js
```

### Version Information
* windows 10
* Visual Studio 2015
* python v2.7.13
* npm 5.3.0
* nightwatch v0.9.16
* nodejs v8.0.0

### Reference 
[Nightwatch.js installation on Windows 10](https://www.youtube.com/watch?v=93ndNx-h1ag)

[[camel's Blog] Nightwatch.js debug 血淚史](https://blog.camel2243.com/2017/06/17/test-nightwatch-debug-%E8%A1%80%E6%B7%9A%E5%8F%B2/)

[Install issue with NPM](https://github.com/socketio/socket.io/issues/2277)



