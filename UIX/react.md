## Creating React problems

### Solution stub
By default, all React problems are initialized with [this](https://github.com/doselect/dexter-stubs/tree/master/reactjs) code. If you need to change this behaviour, you can upload a different stub in the problem settings.

```
workspace/
├── scripts/
│   ├── app.jsx
│   └── hello.jsx
├── styles/
│   └── main.css
├── __tests__/
│   └── test.js
└── config.js
└── index.html
```

### Test runner
Choose `Jest` for React

### Sample testcase
The following testcase will pass for the default code stub loaded for React. During evaluation, `__tests__` directory is created and each testcase is run in that directory. 
#### Testcase #1
```javascript
import React from 'react';
import Enzyme, { shallow } from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';

Enzyme.configure({ adapter: new Adapter() });

import {Hello} from '../scripts/hello';

describe('<Hello />', () => {
  
  it('renders a <strong> with a static text', () => {
    const wrapper = shallow(<Hello/>);
    const p = wrapper.find('strong');
    expect(p.text()).toBe('ReactJS');
  });
  
});
```

Note that `scripts/hello.jsx` contains the following code.
```
import React from 'react';

class Hello extends React.Component {
  render() {
    return (
      <div className="hello">
      	<p>Your <strong>ReactJS</strong> project is ready!</p>
    	<p>ReactJS Version 15.6.2</p>
      </div>
    );
  }
}

export { Hello }
```

### Sample evaluation log
#### Accepted solution
```
PASS __tests__/test.js
  <Hello />
    ✓ renders a <strong> with a static text (9ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        3.31s
Ran all test suites.
```

#### Rejected solution
```
FAIL __tests__/test.js
  <Hello />
    ✕ renders a <strong> with a static text (13ms)

  ● <Hello /> › renders a <strong> with a static text

    Method “text” is only meant to be run on a single node. 0 found instead.

      13 |     const wrapper = shallow(<Hello/>);
      14 |     const p = wrapper.find('strong');
    > 15 |     expect(p.text()).toBe('ReactJS');
      16 |   });
      17 |   
      18 | });
      
      at ShallowWrapper.single (../../usr/local/lib/node_modules/enzyme/build/ShallowWrapper.js:1618:17)
      at ShallowWrapper.text (../../usr/local/lib/node_modules/enzyme/build/ShallowWrapper.js:844:21)
      at Object.<anonymous> (__tests__/test.js:15:14)

Test Suites: 1 failed, 1 total
Tests:       1 failed, 1 total
Snapshots:   0 total
Time:        3.482s
Ran all test suites.
```