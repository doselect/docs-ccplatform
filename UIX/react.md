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

```javascript
import React from 'react';
import Enzyme, { mount } from 'enzyme';
import Adapter from 'enzyme-adapter-react-16';

Enzyme.configure({ adapter: new Adapter() });

import {Hello} from '../scripts/hello';

test('Component renders the text inside it', () => {
  const wrapper = mount(
    <Hello/>
  );
  const p = wrapper.find('strong');
  expect(p.text()).toBe('ReactJS');
});
```
