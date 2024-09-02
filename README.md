<h1>How to Install Webpack in a WordPress Theme</h1>

<h2>Webpack-WordPress Setup</h2>

<h3>Initialization</h3>
<ol>
  <li>Initialize your project:
    <pre><code>npm init -y</code></pre>
  </li>
  <li>Install Webpack as a development dependency:
    <pre><code>npm install webpack webpack-cli --save-dev</code></pre>
  </li>
</ol>

<h3>Update <code>package.json</code> Scripts</h3>
<p>Add the following scripts to your <code>package.json</code> file:</p>
<pre><code>
"scripts": {
  ...
  "build": "webpack",
  "start": "webpack --watch"
}
</code></pre>
<p><em>Note: Remove any other scripts if needed.</em></p>

<h3>Create <code>webpack.config.js</code></h3>
<p>Add the following code to the <code>webpack.config.js</code> file:</p>
<pre><code>
const path = require('path');

module.exports = {
  mode: 'production',
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'assets'),
    filename: 'scripts.js'
  }
};
</code></pre>
<p><strong>Note:</strong> If you change the mode to <code>development</code>, CSS and JS code will not be minified.</p>

<h3>Create the <code>src</code> Folder</h3>
<ol>
  <li>Inside your theme folder, create a <code>src</code> folder.</li>
  <li>Add an <code>index.js</code> file in the <code>src</code> folder.</li>
  <li>Optionally, create a <code>js</code> folder within <code>src</code> and add as many script files as needed.</li>
</ol>

<h3>Create the <code>assets</code> Folder</h3>
<p>Finally, run the following command to test if everything works and to compile your JavaScript files:</p>
<pre><code>npm run build</code></pre>

<h3>Add compiled scripts to theme</h3>
<pre><code>wp_enqueue_script('custom-sripts', get_template_directory_uri() . '/assets/scripts.js', array('jquery'), '1.0', true);</code></pre>

<h3>Add scss support with command <pre><code>npm i css-loader sass-loader node-sass mini-css-extract-plugin -D</code></h3></pre>
<p>Create scss folder inside src folder</p>
<p>Add main.scss file</p>

<p>Update folowing code to webpack.config.js</p>
<pre><code>
  const path = require("path");
const MiniCssExtractPlugin = require("mini-css-extract-plugin");

module.exports = {
  mode: "production",
  entry: "./src/index.js",
  output: {
    path: path.resolve(__dirname, "assets"),
    filename: "scripts.js",
  },
  module: {
    rules: [
      {
        test: /\.(scss|css)$/,
        use: [
          MiniCssExtractPlugin.loader,
          {
            loader: "css-loader",
            options: { url: false },
          },
          "sass-loader",
        ],
      },
    ],
  },
  plugins: [
    new MiniCssExtractPlugin({
      filename: "css/main.css", // Relative path to the output directory
    }),
  ],
};
</code></pre>

<h3>Add compiled main.css file to theme</h3>
<pre><code>wp_enqueue_style('main-styles', get_template_directory_uri() . '/assets/css/main.css', array(), '1.0.0', 'all');</code></pre>

<h3>Comands for watch/build</h3>
<ol>
  <li><code>npm run start</code></li>
  <h4>Or</h4>
  <li><code>npm run build</code></li>
</ol>
