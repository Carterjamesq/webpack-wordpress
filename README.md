<h1>How to insatll webpack to Wordpress theme</h1>

# webpack-wordpress

<h2>Inizialization</h2>
<ul>
  <li>npm init</li>
  <li>npm install webpack -D</li>
</ul>

<p>Add comands to <span>package.json</span></p>

"scripts": {
	...
 
	"build": "webpack",
	"start": "webpack --watch"
},
<i>Remove other scrips if need</i>

<h2>Create webpack.config.js file</h2>
<p>Add code to webpack.config.js</p>
const path = require('path');

module.exports = {
	mode: 'production',
	entry: './src/index.js',
	output: {
		path: path.resolve(__dirname, 'assets'),
		filename: 'scripts.js'
	}
};
note: if change mode to development it's doesnt minify css, js code 

<h2>Create src folder inside theme folder</h2>
<p>Create <b>src</b> folder with <b>index.js</b> file</p>
<p>Create <b>js</b> folder with .js file scritp ( add as many as need script files )</p>

<h2>Create <b>assets</b>s folder</h2>
<sapn>Run <b>npm run build</b> command to test if everything works and js scripts compile</sapn>
