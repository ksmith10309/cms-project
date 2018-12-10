![CF](http://i.imgur.com/7v5ASc8.png) Week 8 Project
=================================================

## CMS Project

### Author: Katherine Smith

### Links and Resources
* [Front-End Repository](https://github.com/ksmith10309/cms-front-end)
* [Deployed Front-End](http://cms-front-end-deploybucket-1jnzppinwtijs.s3-website-us-west-2.amazonaws.com/)

### Modules
#### `index.js`
- Imports App component
- Creates store and connects to store
- Contains Main component
  - Passes store down to App component
  - Renders App component

#### `app.js`
- Imports LoginContextProvider component, Login component, Auth component, and Records component
- Contains the App component
  - Contains selectModel() method which handles selecting a model
  - Contains componentDidMount() which handles displaying the models as buttons
  - Wraps Login component, Auth component, and Records component in LoginContextProvider component so that they and their children can subscribe to LoginContext as consumers
  - Renders Login component, Auth component, and Records component
- Exports App component

#### `list.js`
- Imports Auth component and Record component
- Imports If() helper function
- Imports actions from the store
- Contains Records component
  - Contains own state for id
  - Contains deleteRecord() method which handles deleting a record
  - Contains editRecord() method which handles changing id
  - Contains reset() method which handles setting id to null
  - Contains componentDidMount() and componentDidUpdate() which handle getting the records
  - Renders the list of records and Record component while utilizing Auth component and If() helper function
- Contains mapStateToProps() which maps records state to props
- Contains mapDispatchToProps() which maps records dispatch to props
- Exports connected Records component

#### `record.js`
- Imports Form from react-jsonschema-form
- Imports get() function
- Imports actions from the store
- Contains Record component
  - Contains own state for schema
  - Contains componentDidMount() and componentDidUpdate() which handle getting the schema
  - Contains resetPlayer() method which handles setting id to null
  - Contains handleSubmit() method which handles submitting the form
  - Renders the form
- Contains mapStateToProps() which maps records state to props
- Contains mapDispatchToProps() which maps records dispatch to props
- Exports connected Record component

### Store Modules
#### `store/index.js`
- Imports reducers and redux-thunk
- Exports function to create the store

#### `actions.js`
- Imports superagent
- Contains get(), destroy(), post(), and put() as actions to be dispatched
- Contains runGet(), runDestroy(), runPost() and runPut() as helper functions

#### `reducers.js`
- Maintains state for the store

### Auth Modules
#### `context.js`
- Creates LoginContext
- Contains LoginContextProvider component
  - Contains state for token and loggedIn
  - Contains login() method which handles logging in
  - Contains logout() method which handles logging out
  - Renders this.props.children wrapped in LoginContext.Provider with state passed in
- Exports LoginContext and LoginContextProvider component

#### `login.js`
- Imports LoginContext
- Imports superagent and If() helper function
- Contains Login component
  - Contains own state for username and password
  - Contains handleSubmit() method which handles submitting username and password
  - Contains handleChange() method which handles changes to input fields
  - Subscribes to LoginContext as a consumer
  - Renders login form and log out button while utilizing If() helper function
- Exports Login component

#### `auth.js`
- Imports LoginContext
- Imports jsonwebtoken and If() helper function
- Contains Auth component
  - Subscribes to LoginContext as a consumer
  - Utilizes jsonwebtoken and If() helper function to verify if it is ok to render this.props.children
- Exports Auth component

### Library Modules
#### `api.js`
- Contains and exports get() function for superagent get requests
#### `if/index.js`
- Contains and exports If() helper function

### Setup
#### Running the app
* `npm start`
* Displays the React app in the browser at localhost:3000

#### Tests
* `npm test`
* The assertion that the app component is alive at application start was made

#### UML
<img src="./cms-front-end.jpg" alt="cms-front-end.jpg" width="700px">