## Project based problems
Project based problems are problems where solution code can be written in multiple files rather than a single file (like Script based problems). The project structure is flexible.

** Supported technologies:** Java 7, Java 8, Python 2, Python 3

### Things to know for creating project based problems

** Evaluation master script:** A bash script which runs the unit tests
Example:
```bash
export PATH=$JAVA7_HOME:$PATH
cd /code/workspace
javac *.java
cp $eval_prog UnitTest.java
rm UnitTest.class &> /dev/null
javac -cp .:/usr/lib/jvm/java-7-oracle/jre/lib/ext/junit-4.12.jar UnitTest.java
java -cp .:/usr/lib/jvm/java-7-oracle/jre/lib/ext/junit-4.12.jar:/usr/lib/jvm/java-7-oracle/jre/lib/ext/hamcrest-core-1.3.jar org.junit.runner.JUnitCore UnitTest
```

** Testcases:** The unit tests or evalution script. Each of them is referenced from the `$eval_prog` file during evaluation (check Evaluation master script)
Example:
```java
import static org.junit.Assert.assertEquals;
import static junit.framework.TestCase.fail;
import org.junit.Test;

public class UnitTest {
  @Test
  public void testEmployeeClass() {
    Employee employee = new Employee();

    employee.setEmployeeId(12345);
    assertEquals(12345, employee.getEmployeeId());

  }
}
```

** Solution stub:** This will be loaded as the boilerplate code. Make sure the solution stub is clear

** Evaluation methods**
* Unit test cases (Check on `Enable import mode` in the problem settings)
    * Junit (java)
    * Unittest (python)
* ATF: Bash or python script (exit code 0 - success)
