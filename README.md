# Python-React Starter Project Guide

This README provides a guide on how to set up a starter project combining a Python backend (using Flask) with a React frontend. This setup is ideal for full-stack web development.

## Prerequisites

- Python environment
- Node.js and npm
- Basic knowledge of Python (Flask) and JavaScript (React)

## Setting Up the Project

1. **Create the project directories:**
   - One for the backend and one for the frontend.
   ```bash
   mkdir myproject
   cd myproject
   mkdir backend
   mkdir frontend
   ```

2. **Set up the Python backend:**
   - Navigate to the backend directory and set up a virtual environment.
   ```bash
   cd backend
   python -m venv venv
   source venv/bin/activate
   pip install flask
   ```

   - Create a simple Flask app.
   ```python
   from flask import Flask

   app = Flask(__name__)

   @app.route('/')
   def hello_world():
       return 'Hello, World!'

   if __name__ == '__main__':
       app.run(debug=True)
   ```

3. **Set up the React frontend:**
   - Navigate to the frontend directory and create a new React app.
   ```bash
   cd ../frontend
   npx create-react-app .
   ```

   - Modify the `App.js` to fetch data from the Flask backend.
   ```javascript
   import React, { useEffect, useState } from 'react';
   import './App.css';

   function App() {
       const [data, setData] = useState('');

       useEffect(() => {
           fetch('http://localhost:5000/')
               .then(response => response.text())
               .then(data => setData(data));
       }, []);

       return (
           <div className="App">
               <header className="App-header">
                   <p>
                       {data}
                   </p>
               </header>
           </div>
       );
   }

   export default App;
   ```

4. **Run the applications:**
   - Start the Flask app.
   ```bash
   # From the backend directory
   python app.py
   ```

   - Start the React app.
   ```bash
   # From the frontend directory
   npm start
   ```

## Conclusion

You now have a basic Python-React starter project set up. This configuration serves as a foundation for building more complex full-stack applications.

For more detailed information, visit the [Flask documentation](https://flask.palletsprojects.com/) and [React documentation](https://reactjs.org/).
