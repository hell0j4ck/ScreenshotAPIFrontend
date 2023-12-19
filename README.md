<b>NOTE: Incase of a chrome browser not found ERROR. Add the following line of code to a puppeteer.config.cjs file and npm uninstall then npm install puppeteer. You should be able to see the new .cache folder generated in the root directory. Now the cache directory is officially changed and there should be no problem running the app.</b>  <br><br>
<b>I've Already Included The Below Code Is In The Application So You Don't Have To.</b>

const {join} = require('path');

<p>
  /**<br>
 * @type {import("puppeteer").Configuration}<br>
 */<br>
module.exports = {  <br>
  // Changes the cache location for Puppeteer.  <br>
  cacheDirectory: join(__dirname, '.cache', 'puppeteer'),  <br>
};  <br>
</p>




<h1>INSTRUCTIONS</h1>

Puppetteer by default installs the headless browser in the local user profile instead of in the root directory, which causes the error of "Browser not found" in some deployments. The code above when saved as puppeteer.config.cjs forces puppeteer to install the headless browser in the root directory of the application.

It is IMPORTANT TO NOTE that before deployment, the node_modules folder and .cache folder must be deleted.

The reason being, the .cache folder is large in size and contains files/executables that in my experience cannot be uploaded to the repository. 

If you upload the code WITHOUT the .cache folder while the node_modules folder is still there, running NPM INSTALL does NOT reinstall the browser (This is a glitch with puppetteer), that is why once you delete both folders, NPM INSTALL will reinstall the node_modules and .cache files upon deployment.

If you remove the .cache folder while the node_modules folder is still there, you can reinstall the browser by running the Install Browser .cache Folder.bat script or Install Browser.bat batch scripts included in the application.

However, since most serverless application deployment platforms like Render, FlyIO, or Lambda does not give you the option to go in and run the Install Browser .cache Folder.bat manually, removing both folders will ensure that everything gets installed the way they should by simply running NPM INSTALL.


<h2>Starting The Server</h2>

<p>For local testing before deploying, simply run the NPM Install Batch File followed by the Start Server batch file</p>
<br>

<img src="https://github.com/hell0j4ck/ScreenshotAPI/assets/71343643/3d5a93cb-3ac4-4161-95d1-af999e9ca3dd">

<h2>Screenshot Request</h2>

<p>For screenshots, you will use the <b>/screenshot</b> route followed by the query string <b>url</b> containing your url</p>
<br>

<img src="https://github.com/hell0j4ck/ScreenshotAPI/assets/71343643/0567a37e-d166-4f1d-905b-29ad11f06b5f">
<img src="https://github.com/hell0j4ck/ScreenshotAPI/assets/71343643/e4b17211-dc5e-4f17-bb20-b45d0aeaac92">

<h2>PDF Request</h2>

<p>For PDFs, you will use the <b>/pdf</b> route followed by the query string <b>url</b> containing your url</p>
<br>

<img src="https://github.com/hell0j4ck/ScreenshotAPI/assets/71343643/a05de586-1cce-42f5-80e8-e1ec2875ca6b">
<img src="https://github.com/hell0j4ck/ScreenshotAPI/assets/71343643/6500587c-787a-418d-a6b3-842fc4696f3f">




