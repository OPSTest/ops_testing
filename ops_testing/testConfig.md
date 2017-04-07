# Test Config

 Please follow the steps to setup the testing environment.

 ## Prerequisites
 OPS E2E Testing using the [Protractor](http://www.protractortest.org/#/tutorial) as the test framework. Protracotr is a Node.js program. To run, you need to install [Node.js](https://nodejs.org/en/) and [Java Development kit(JDK)](http://www.oracle.com/technetwork/java/javase/downloads/index.html) first.

 ## Download the Project
 [Project Address](https://mseng.visualstudio.com/VSChina/VSChina%20Team/_git/OpenPublishing.E2ETesting). You can clone the repo with *"git clone* {clone url}" command into your directory.

 ## Install opse2e tool
 [Opse2e](https://mseng.visualstudio.com/VSChina/VSChina%20Team/_git/Templating.E2ETools) is a private nodejs package, please go to [VSO WebComponents management page](https://mseng.visualstudio.com/DefaultCollection/VSChina/Templating/_packaging?feed=WebComponents&package=8316a24e-039a-496d-a3d3-125e7cdf1a8d&version=0bdaa70c-ecc7-4e3b-b68f-5a188988ce26&_a=package) to get your npmrc credential. See the steps.
 1.Click ‘Connect to feed’ button and then 'Generate npm credentials', 
 2.Finally copy the credential text to a **.npmrc** file and saved to user home directory. (such as C:\Users\jinbwan\.npmrc)

 Opse2e is a cli-based tool, you could run the following command to exec e2e cases.  
 1.*npm run opse2e init*    
 It does something like ‘webdriver-manager update’, but download chrome driver to current node_modules directory. This command just need run once.

 2.*npm run opse2e protractor*  
 
 It’s kind of similar as previous ‘gulp e2e’. But the good thing is you don’t need start a standalone selenium server any longer.  

 It has a big improvement that it’ll host a temporary selenium server on a free port automatically every time you run this command.  

 More information about the command could be got via '--help' options.  

 ## Running the test cases
 You can running the test cases with optional parms. For example:  
 *npm run opse2e -- protractor --suite pullRequest --baseUrl https://ops.microsoft.com/ --branch develop*  
 Please see the more information about the command
