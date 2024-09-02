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
	mode: 'development',
	entry: './src/index.js',
	output: {
		path: path.resolve(__dirname, 'assets'),
		filename: 'scripts.js'
	}
};

