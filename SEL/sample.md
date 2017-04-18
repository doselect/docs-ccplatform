## Sample Selenium Testing Problem

### Name

Test the login page

### Description

PHPTravels is a web based booking software. You have been asked by the developers of PHPTravels to write Selenium tests to check the login page of their admin console.

http://www.phptravels.net/admin

**Check valid login**
- Use the following credentials to login to the administrator dashboard
 Email: admin@phptravels.com
 Password: demoadmin
- Check if you are successfully logged in by checking the page source

**Check invalid login**
- Use the following credentials to login to the administrator dashboard
 Email: invalid@invalid.com
 Password: invalid
- Check if the application throws the following error by checking the page source
Invalid Login Credentials

Note that the evaluation is not based on the output of your program, but on the ability of your program to execute the above scenarios.

### Solution

**python 2**

```python
import unittest
import time
from selenium import webdriver
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
from selenium.webdriver.common.keys import Keys

class PHPTravelsLogin(unittest.TestCase):

    def setUp(self):
        self.driver = webdriver.Remote(command_executor='http://127.0.0.1:4444/wd/hub',desired_capabilities=DesiredCapabilities.PHANTOMJS)

    def test_valid_login(self):
        driver = self.driver
        driver.get("http://www.phptravels.net/admin")
        elem = driver.find_element_by_name("email")
        elem.send_keys("admin@phptravels.com")
        elem = driver.find_element_by_name("password")
        elem.send_keys("demoadmin")
        elem.send_keys(Keys.RETURN)
        # Make sure you wait for the page to load completely
        time.sleep(3)
        assert "Quick Booking" in driver.page_source

    def test_invalid_login(self):
        driver = self.driver
        driver.get("http://www.phptravels.net/admin")
        elem = driver.find_element_by_name("email")
        elem.send_keys("invalid@invalid.com")
        elem = driver.find_element_by_name("password")
        elem.send_keys("invalid")
        elem.send_keys(Keys.RETURN)
        # Make sure you wait for the page to load completely
        time.sleep(3)
        assert "Invalid Login Credentials" in driver.page_source

    def tearDown(self):
        self.driver.close()

if __name__ == "__main__":
    unittest.main()
```
