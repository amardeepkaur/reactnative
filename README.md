# Notes

#### 1.  Why do we not call a function with {} ? 

Without parenthesis, you're not calling the function. The name of the function without the parenthesis is a reference to the function. Parentheses is not used in the function at that point because we are not calling the function at the point where the code is encountered, but instead want to pass a reference to the function. If you use login() , the function will get called at that point, we instead want it to be called only after onClick, so we pass a reference to login there.
    
#### 2. Components: Functional and Class

  *Functional Component*
  ```
  const App = () => {
   return (
    <View>
      <Text> "Hello" </Text>
      <Button title="Login" onPress={ ()=> alert("Login pressed") } />
    </View>
    );
 }
```

  *Class Component*
  ```
  class App extends Component {
    render() {
      return(
        <View>
          <Text>"Hello"</Text>
          <Button title="Login" onPress={ ()=> alert("Login pressed") } />
        </View>
       );
    }
  }
  ```
  
#### 3. Props
  Used to pass data.
  
  >App.js
  ```
  import Home from './Home.js';
  
  const App = () => {
    const appData = "Data to be displayed"
    return(
      <View>
        <Home data = {appData} />
      </View> 
    );
  }
  
  export default App;
  ```
  >Home.js
  ```
  const Home =(props) => {
    console.warn(props) //To view all the props
    return(
      <View>
        <Text>{props.data}</Text>
      </View>
    );
  }
  
  export default Home;
  ```
  
  #### 4. State
  - Used in class component
  - object which manages the state of a component e.g. manage the changes happen on press of a button
  - can be used a variable
  
  ```
    class App extends Component {
    constructor() {
      super();
      this.state = { data: "Some app data" };
     }
     
     update() {
      this.setState(
        { data: "Updated State" }
      )
     }
     
     render() {
      return(
      <View>
        <Text>{this.state.data}</Text>
        <Button 
          title="Update"
          onPress= { ()=>{ 
            this.update()
           } }     
        />
      </View>
      );
     }
      
    }
```
  > Note: render() method will be called as many times as state will be updated.
    
  #### 5. Style
  - Inline, with stylesheet, apply multiple styles
  

  
  > App.js
  
```
  class App extends Component {
  render() {
    return(
      <View>
        <Text style={{color:'red', fontSize:30}}>"Hello"</Text>
        <Text style={[styles.colors, styles.fonts]}>Welcome to</Text>
        <Text style={styles.others}>Styles</Text>
        <Text style={[styles.fonts], {color:'blue'}}>of colours</Text>
      </View>
    )
  }
}

const styles = StyleSheet.create({
  colors: {
    color:'green',
    backgroundColor:'yellow',
  },
  fonts: {
    fontSize: 30,
    fontWeight: 'bold',
  },
  others:{
    color: 'gray'
  }
})


export default App;
```

#### 6. Handle text input using STATE
  Usage, events(onclick, onChange), get value from textInput, on button click and styling.

```
import React, { Component } from "react";
import { View, Button, Text, TextInput } from 'react-native';

class App extends Component {
  constructor() {
    super();
    this.state = { name };
  }

  render() {
    return(
      <View>
        <Text style={{fontSize:30}}>
          Name: {this.state.name}
        </Text>
        <TextInput style={{fontSize:20, color:'gray'}}
            placeholder={"Enter name"}
            onChangeText={ (e)=> {
            this.setState({name: e})
          } } >
        </TextInput>
        <Button 
          title='Submit'
          onPress={ ()=> { alert('Name is ' + this.state.name) }}
        />
      </View>
    );
  }
}

export default App;
```

#### 7. Handle form using STATE

```
import React, { Component } from "react";
import { View, Button, Text, TextInput, StyleSheet } from "react-native";

class App extends Component {
  constructor() {
    super();
    this.state = {
      name: "",
      password: "",
      address: ""
    };
  }
  render() {
    return (
      <View>
        <Text style={{ padding: 20, fontSize: 18 }}>
          Hello {this.state.name}
        </Text>
        <TextInput
          style={[styles.textbox, styles.borders]}
          placeholder="Enter name"
          onChangeText={(t) => {
            this.setState({ name: t });
          }}
        ></TextInput>
        <TextInput
          style={[styles.textbox, styles.borders]}
          placeholder="Enter password"
          secureTextEntry={true}
          onChangeText={(p) => {
            this.setState({ password: p });
          }}
        ></TextInput>
        <TextInput
          style={[styles.textbox, styles.borders]}
          placeholder="Enter address"
          onChangeText={(a) => {
            this.setState({ address: a });
          }}
        ></TextInput>
        <Button
          title="Submit"
          onPress={() => {
            this.submit(this.state);
          }}
        />
      </View>
    );
  }

  submit() {
    alert("Address is " + this.state.address);
    console.warn("Values are" + this.state.name + ' ' + this.state.password);
  }
}

const styles = StyleSheet.create({
  textbox: {
    color: "gray"
  },
  borders: {
    borderWidth: 2,
    borderRadius: 10,
    borderColor: "skyblue",
    padding: 10,
    marginHorizontal: 20,
    marginVertical: 10
  }
});

export default App;
```

#### 8. FLEX

- Used to control app layout, provides responsive UI by giving flexible height and width
- 
