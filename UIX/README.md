## Front-end applicaton problems
These kind of problems are used to assess candidate's proficiency in building front-end applications.

** Problem type code:** `UIX`

### Description
It should contain the specifications regarding input elements, navigation, etc as expected by the testcases.  
For example,
> Input field for xyz should have the id 'xyz' and type 'number'

It is preferred to include mockups so that the developer has a clear idea of the design. See [sample problem](sample.md) for reference.

### Evaluation time limit
Time limit (in seconds) for evaluation script

### Testcases
Testcases are used to evaluate the functionality of the app. We use [Node.js](https://nodejs.org) for evaluating front-end applications.

The following libraries are used.
* Mocha test framework https://mochajs.org/
* WebDriver JavaScript bindings https://www.npmjs.com/package/selenium-webdriver
* PhantomJS https://www.npmjs.com/package/phantomjs-prebuilt
* Chai http://chaijs.com/

Have a look at the testcase in [sample problem](sample.md) for reference.
