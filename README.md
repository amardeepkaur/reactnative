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

#### 6. Handle text input
  
