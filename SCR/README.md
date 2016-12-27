## Script problems
Script problems or Programming problems are problems where the required solution is a script or a program in any of the allowed technologies. You need to understand the below fields to create script problems on DoSelect.

### Evaluation mode
Specify how the solution will be judged for correctness.

- **I/O testcase based:** In this mode, sets of input files and expected output files are supplied. Developer's submitted solution is run for each input and it's output is compared with the expected output.
- **Automated Testing Framework (ATF):** In this mode, the testcase script imports the user's solution and evaluates it.

### Problem name
Some fancy name for the problem. If the problems are part of a hackathon/problemset, the name should go along with the theme of the hackathon/problemset.

### Description
This explains the problem. The problem description should be interesting and easy to follow.

### Difficulty level
Specify the difficulty of the problem. Possible difficulties are `Easy`, `Medium` and `Hard`.

### Execution time limit (in seconds)
Time alloted for the developer's code run. This should be utilized to prevent brute force solutions from getting accepted.

### Allowed programming languages
Specify the programming languages which should be allowed for developers to submit their solution code.

### Tags
Add relevant tags for the problem. Eg. Algorithm, Data structures, etc.

### Testcases
Testcases are used to evaluate the correctness of the solution.

- You can specify the `weightage` for each testcase. The larger portion of score will be allocated for high weightage testcases.
- You can also set certain testcases as sample testcases. These testcases will not be used for final evaluation but will be available to developers as `Verify with sample testcases`.
- Testcases can be:
    - **I/O testcase based:** In I/O testcase based, each testcase is a set of an input file and an output file. During evaluation against each testcase, the text in input file is passed to `STDIN` for solution code to access. The solution code should output the required solution to `STDOUT`. And then the evaluation engine will compare the output in `STDOUT` against the output file.
    - **Automated Testing Framework (ATF):** In ATF mode, each testcase is a script which imports the user's code and checks the implementations for correctness.

### Stubs
Stubs help you add boilerplate code for the solutions. Stubs are added for each technology separately.

### Solution Code
The solution code in any accepted language. Make sure to add comments for better understanding.

### Editorial
Explanation of solution to the problem. Include image(s) if it can better explained using them.
