## Create React with Flask Application
In this article, I share how I learnt to create a SPA application using the [React](https://reactjs.org/) library with a backend server developed with [Flask](https://flask.palletsprojects.com/en/2.1.x/).

**Prerequisites**
Node.js
python3

**Side note**
Please now that during development of this article the following where my current workstation preference.

OS: linux(ubuntu 20.4 LTS)
editor: Vscode
node version 16.13.2
python version 3.8.10

Feel at liberty creating this project with your prefered modules.

---

### Create react application
There are many ways to create a new React application.
Open a terminal windown, select a suitable parent directoy, and then run the followinf command to create a new React project called ```react-flask-app```

```bash
    npx create-react-app react-flask-app
```

This will trigger the creation process which upon completion you will have a new git initialized repository with the project name.

Have a look further on the newly created project. Run;
``` bash
    cd react-flask-app
```
to change into the project root directory.

Start the React development server listening on port localhost:300 
``` bash
    npm start
```

### Create Flask Server
The following step with guide you to create a simple Flask application that we need to configure our backend logic and consume infomation from the local development server via api.

First, create and navigate into ```api``` which will act as the root folder for the Flask application.
```bash 
    mkdir api //creates api folder
    cd api //moves into folder
```

There are different kinds of setups and methods for creating scalable flask applications. Read my other how to article to guide you on starting a flask application [here](). 

For this case, I am creating a simple Flask project to create endpoints to show your local current time.
Either way you need to create and activate a virtual environment.
Run;
``` bash
    python3 venv venv //creates virtual environment named venv

    source venv/bin/activate //activates virtualenv
```
The second step is to install pip dependancies to create a flask application. On terminal run;
```bash
   (venv) pip install flask python-dotenv
```
The third step is to create the entry file ```api.py``` and other flask dependent files.
Run;
```bash
    (venv) touch api.py .flaskenv requirements.txt
```

This command create 3 files on the root level of our flask application.

1. Entry file  ```api.py```

Here is a snippet of code to configure your entry file.
```
    import time
    from flask import Flask 


    app = Flask(__name__) //application instance

    @app.route('/time')
    def get_current_time():
        return {'time':time.time()}
```
At the top, we import time and flsk modules to help create and configure our response logic.

We then create app variable which basically is our Flask app instance.

Below, we set up a view route ```localhost:5000/time``` that will display our infomation as a JSON object.

2. Flask variables ```.flaskenv```

Next, declare flask application variables in the .flaskenv file that are needed to run our flask application for local development server.
```
    FLASK_APP=api.py
    FLASK_ENV=development
```
3. Document project dependancies ```requirements.txt```

Document the projects dependacies but listing them to the *requirements.txt* file
```bash
    pip freeze > requirements.txt
```

Test the flask application by running the development server.
```bash
    flask run
```

output
1. on terminal:
    ```
    * Serving Flask app 'api.py' (lazy loading)
    * Environment: production
        WARNING: This is a development server. Do not use it in a production deployment.
     Use a production WSGI server instead.
    * Debug mode: off
    * Running on http://127.0.0.1:5000 (Press CTRL+C to quit)
    ```

2. on browser:
    The default landing page should throw a 404 page error but when you navigate to route ```time``` by adding ```/time``` on the url the rendered page ```http://127.0.0.1:5000/time``` should display a JSON object similar to the one below.
    ```
    {"time":1659045182.8446972}
    ```

Stop flask server press ```ctrl-c```

Now that the flask part is complete, lets leave the flask subfolder and go back to root of the react project.
#### Set up a connected development server for React and Flask.
At this point you might have noticed that the React application runs on port ```localhost:3000``` while the Flask application runs on port ```localhost:5000```

We could harmonize this and render our output in sync on the default SPA port by tweeking *package.json* file to help us avoid cross-origin issues. Add a ```proxy``` key at the bottom of the package.json file.
```
    {
        ... default config keys ...


        "proxy": "http://localhost:5000"
    }
```

**NB: Remember to add a comma at the end of the previous line to validate this JSON file.**

**Optional**
You could add related application management commands such as run and testing the backend application.

Somewhere in the middle of *package.json* you will find ```scripts``` key to app custom commands inside it.

```
"scripts": {
    "start": "react-scripts start",
    "start-api": "cd api && venv/bin/flask run --no-debugger",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "test-api": "cd api && flask test",
    "eject": "react-scripts eject"
}
```

I've added ```start-api``` and ```test-api``` keys, which I am going to use to run and test the Flask server if need be.

### Add Flask application to Git
By default, the react application project include a git initialized repository. To make it more friendly to python, there are a couple of things we need to add on the .gitignore file:
```
    venv
    __pycache__
```
This will ignore adding the virtual environment and python3 cache files to the git repository.

Add and commit all the new files of the backend project.
```
    $ git status //view all changes on this repo
    $ git add .gitignore packahe.json api
    $ git commit -m "Feat: Backend create flask application"
```

### Running the combined project.
Finally run the application!

```
    pwd // check that you are on the main root level
    npm start //starts react server on port localhost:3000
```
When you have the frontend running on ```localhost:3000```, split terminal and start the Flask backend on ```localhost:5000``` Run:
```bash 
    npm start api
```

### Read Flask Endpoint
Complete the setup buy testing the application with a simple ```CRUD``` operation concept *Read* by implementing the get method and functonality on the react application.

Below is a code snippet of the *src/app.js* file implemeting the result from Flask.
```
import React, { useState, useEffect} from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  const [currentTime, setCurrentTime] = useState(1);

  useEffect(() => {
    fetch('/time').then(res => res.json()).then(data => {
      setCurrentTime(data.time);
    })
  }, []);

  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <p>
          Edit <code>src/App.js</code> and save to reload.
        </p>
        <a
          className="App-link"
          href="https://reactjs.org"
          target="_blank"
          rel="noopener noreferrer"
        >
          Learn React
        </a>
        <p>The current time is {currentTime}</p>
      </header>
    </div>
  );
}

export default App;

```

As soon as you save this changes, the application should update (using the life cycle hook) modules imported from react library and render the a similar output as the time key on the JSON object from the backend project below the start react app template.

---

##### Acknowledgement
*You might notice a great resemblance on this step by step guide on setting up a complete fullstack application. I send my sincere gratitude to [Miguel Grunberg](https://blog.miguelgrinberg.com/post/about-me) for awesome [React Mega tutorial](https://blog.miguelgrinberg.com/post/introducing-the-react-mega-tutorial) that I used to learn how concepts discussed here in one lesson.*