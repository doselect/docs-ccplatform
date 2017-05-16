## Android problems
These problems evaluates the developer's expertise in developing mobile apps for Android platform.

### Description
It should include the application specifications regarding buttons and other navigation elements as expected by the testcases.
For example,
> Activity name should be 'MainActivity'  
> EditText field, where the expression and the final answer is displayed, should have the id 'xyz'

It is preferred to include mockups so that the developer gets the clear idea about the design. See [sample problem](sample.md) for example.

### Testcases
We use [Espresso testing framework](https://developer.android.com/training/testing/ui-testing/espresso-testing.html) for writing testcases for Android problems. For the sake of consistency in the evaluation, the submission should follow the below guidelines.

** Package name: ** `com.doselect.androidapp`  
** Build tools version: ** `25.0.2`  
** Target sdk version: ** `25`  

It is recommended to use the boilerplate available at [GitHub](https://github.com/doselect/dexter-stubs/tree/master/android). Please refrain from changing the gradle configurations, otherwise your evaluation can fail.

Have a look at the testcase in the [sample problem](sample.md) for better understanding.
