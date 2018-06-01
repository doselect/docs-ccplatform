## Example Full-Stack problem

### Problem name
Build To-Do App

### Problem Statement
Please access the Case Study details on this link: https://drive.google.com/file/d/1NcPfzlgdBT0vgmgcyzlrdNbQpIptoXk4/view

**Note:** The problem statement will be a type of case study. Please refer the above-given hyperlink.

###Evaluation master script

```bash
cd /home/user/workspace
node index.js &
/usr/bin/mongod --smallfiles &
sleep 10

for d in /code/testcases/*; do
    mv $d/eval.py3 test.py
    python test.py &>> $d/OUTPUT 
    exit_status=$?
    echo -n $exit_status > $d/STATUS
done
```

###Test cases

**Front-end Test case**

```python
from selenium import webdriver
import unittest
import time

class TasksAppTestCase(unittest.TestCase):

    def setUp(self):
        self.driver = webdriver.PhantomJS()
        self.driver.get("http://localhost:8000/")

    def test_adding_new_task(self):
        # get the initial number of tasks present
        time.sleep(0.5)
        self.tasks_count = 
        len(self.driver.find_elements_by_class_name('row'))
        time.sleep(0.5)
        self.assertEqual("Your tasks ({})".format(self.tasks_count),
                         self.driver.find_element_by_id("app-header").text,'Add task implemented incorrectly')

        # add three tasks
        for i in range(3):
            self.driver.find_element_by_id("text-area").click()
            self.driver.find_element_by_id("text-area").clear()
            self.driver.find_element_by_id("text-area").send_keys("dummy task")
            self.driver.find_element_by_id("add-btn").click()
            time.sleep(0.5)
            self.tasks_count += 1
            self.assertEqual("Your tasks ({})".format(self.tasks_count),
                             self.driver.find_element_by_id("app-header").text,msg='Add task implemented incorrectly')

    def test_deleting_a_task(self):
        # get the initial number of tasks present
        self.tasks_count = len(self.driver.find_elements_by_class_name('row'))
        # delete a task
        time.sleep(0.5)
        first_task = self.driver.find_elements_by_class_name('row')[0]
        first_task.find_element_by_class_name('delete-btn').click()
        time.sleep(0.5)
        self.tasks_count -= 1
        self.assertEqual("Your tasks ({})".format(self.tasks_count),
                         self.driver.find_element_by_id("app-header").text,'Remove task implemented incorrectly')


if __name__ == "__main__":
    unittest.main()
```	

**API Test case**

```python
# importing the requests library
import requests
import json
 
# defining the api-endpoint 
API_ENDPOINT = "http://localhost:8000/tasks/"

# Testing POST Request
data = {"name":"test_REST_API"}
r_post = requests.post(url = API_ENDPOINT, data = data)
assert r_post.status_code == 200, "POST method not implemented correctly"
post_data = r_post.text
post_data = json.loads(post_data)
obj_id = post_data.get('_id')
k = sorted(post_data.keys())
assert k == ['Created_date', '__v', '_id', 'name', 'status'],"Model is not implemented correctly"

# Testing GET Request
r_get = requests.get(url = API_ENDPOINT+obj_id)
get_data = r_get.text
assert r_get.status_code == 200
get_data = json.loads(get_data)
assert get_data["name"] == 'test_REST_API', "GET method not implemented correctly"
	
# Testing PUT Request
data = {"name": "bob"}
r_put = requests.put(url = API_ENDPOINT+obj_id, data = data)
put_data = r_put.text
put_data = json.loads(put_data)
assert r_put.status_code ==200
assert put_data["name"] == 'bob', "PUT method not implemented correctly"

# Testing DELETE Request
r_delete = requests.delete(url = API_ENDPOINT+obj_id)
delete_data = r_delete.text
assert r_delete.status_code ==200, "DELETE method not implemented correctly"
test_delete = requests.get(url = API_ENDPOINT+obj_id)
del_data = test_delete.text
del_data = json.loads(del_data)
assert del_data == None, "DELETE method not implemented correctly"
```

###Solution
You can find the solution here on this link: https://media-doselect.s3.amazonaws.com/generic/zKKPxwR5ggrY9dWWJo2nK212Q/MEANapp.zip


