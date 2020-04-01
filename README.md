Tutorial: 
https://medium.com/aubergine-solutions/continuous-integration-for-angular-with-angular-cli-jenkins-phantomjs-34a870fa096f

 > ng new angular-ci

Add dependecies for headless browser for ci
 > npm install --save-dev phantomjs-prebuilt karma-phantomjs-launcher

It will install karma-phantomjs-launcher in your angular project.
Now we have to configure PhantomJS. So we need to setup up some setting in karma.conf.js.
update in karma.conf.js file. (Added comments what changed)

Also, have to enable some polyfills which are needed by PhantomJS otherwise it won’t run the test suits.
update src/polyfills.ts to import needed libs.

4.Let’s configure Jenkins to setup Continuous Integration:
    Now it time to setup CI in Jenkins.
    1.First create one git repository in your project and push it on Gitlab or Bitbucket Or Github and get the repository URL.
    2. Now create freestyle project in Jenkins.
    3. In jenkins "Source Code Management" tab, setup the repository which have created just before. So whenever you push any changes in your branch it will run the Jenkins task which you setup in Jenkins Build. Also you can set build trigger as per your requirement.

5.Add following build script in "Build" section
    npm install
    ng test --single-run true