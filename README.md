##### Recharts 라이브러리의 예제를 시작으로, M5프로젝트 페이지에 들어갈 수 있는 인터랙티브 시각화형태를 만들어보는 저장소.

## create-react-app으로 Recharts시작하기

1. 프롬프트를 켜고 `cd 작업폴더` 를 지정해준다.

2. `npx create-react-app with-recharts` 

3. `Happy hacking!` 이라는 문구가 뜨면 작업 폴더에 `with-recharts` 폴더가 생성된다.

4. `cd with-recharts` 

5. `npm start` --> http://localhost:3000/ 브라우저가 실행되면서 프로젝트가 떠있는 것을 확인할 수 있다. <br> 자, 이제 만들어진 파일을 요리조리 바꿔준다.

6. ATOM으로 `with-recharts` 폴더를 열고 `src/App.js` 파일을 수정해준다.

   - `public/index.html`과 `src/index.js`는 엔트리 포인트가 되는 소스로, <br>파일이름이 변경되면 create-react-app은 작동하지 않으므로 주의한다. 

7. [Recharts](http://recharts.org/en-US/examples)에서 제공하는 [예제코드](https://jsfiddle.net/alidingling/xqjtetw0/)로 SimpleLineChart를 그려보자.

8. 처음 생성된 `App.js` 의 코드는 이러한 상태!

   ```javascript
   import React, { Component } from 'react';
   import logo from './logo.svg';
   import './App.css';
   
   class App extends Component {
     render() {
       return (
         <div className="App">
           <header className="App-header">
             <img src={logo} className="App-logo" alt="logo" />
             <h1 className="App-title">Welcome to React</h1>
           </header>
           <p className="App-intro">
             To get started, edit <code>src/App.js</code> and save to reload.
           </p>
          </div>
       );
     }
   }
   
   export default App;
   ```

9. SimpleLineChart 코드에서 자바스크립트 부분을 보고 `App.js` 파일의 코드에 추가해준다. 

   ```javascript
   <!-- SimpleLineChart--JS CODE -->
   
   const {LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, Legend} = Recharts;
   const data = [
         {name: 'Page A', uv: 4000, pv: 2400, amt: 2400},
         {name: 'Page B', uv: 3000, pv: 1398, amt: 2210},
         {name: 'Page C', uv: 2000, pv: 9800, amt: 2290},
         {name: 'Page D', uv: 2780, pv: 3908, amt: 2000},
         {name: 'Page E', uv: 1890, pv: 4800, amt: 2181},
         {name: 'Page F', uv: 2390, pv: 3800, amt: 2500},
         {name: 'Page G', uv: 3490, pv: 4300, amt: 2100},
   ];
   const SimpleLineChart = React.createClass({
   	render () {
     	return (
       	<LineChart width={600} height={300} data={data}
               margin={{top: 5, right: 30, left: 20, bottom: 5}}>
          <XAxis dataKey="name"/>
          <YAxis/>
          <CartesianGrid strokeDasharray="3 3"/>
          <Tooltip/>
          <Legend />
          <Line type="monotone" dataKey="pv" stroke="#8884d8" activeDot={{r: 8}}/>
          <Line type="monotone" dataKey="uv" stroke="#82ca9d" />
         </LineChart>
       );
     }
   })
   
   ReactDOM.render(
     <SimpleLineChart />,
     document.getElementById('container')
   );
   ```

10.  `App.js` 에 추가, 수정해준다.

```javascript
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

<!-- const를 import로, = Recharts;를 from "recharts"로 수정한뒤 추가 -->
import {LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, Legend} from "recharts"

<!-- data 정보 추가 -->
const data = [
      {name: 'Page A', uv: 4000, pv: 2400, amt: 2400},
      {name: 'Page B', uv: 3000, pv: 1398, amt: 2210},
      {name: 'Page C', uv: 2000, pv: 9800, amt: 2290},
      {name: 'Page D', uv: 2780, pv: 3908, amt: 2000},
      {name: 'Page E', uv: 1890, pv: 4800, amt: 2181},
      {name: 'Page F', uv: 2390, pv: 3800, amt: 2500},
      {name: 'Page G', uv: 3490, pv: 4300, amt: 2100},
];

class App extends Component {
  render() {
    return (
      <div className="App">
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h1 className="App-title">Welcome to React</h1>
        </header>
        <p className="App-intro">
          To get started, edit <code>src/App.js</code> and save to reload.
        </p>
        
<!-- 차트 영역, 스타일 추가 -->
        <LineChart width={600} height={300} data={data}
          margin={{top: 5, right: 30, left: 20, bottom: 5}}>
         <XAxis dataKey="name"/>
         <YAxis/>
         <CartesianGrid strokeDasharray="3 3"/>
         <Tooltip/>
         <Legend />
         <Line type="monotone" dataKey="pv" stroke="#8884d8" activeDot={{r:8}}/>
         <Line type="monotone" dataKey="uv" stroke="#82ca9d" />
        </LineChart>
        );
      </div>
    );
  }
}

export default App;
```

11. `App.js` 파일을 저장한 뒤, http://localhost:3000/ 브라우저를 열어 영롱한 그래프를 확인한다!  :sunglasses: 

##### 이제 우리데이터로 그려보고, 페이지에 들어갈 수 있는 형태로 만들어 보자!

