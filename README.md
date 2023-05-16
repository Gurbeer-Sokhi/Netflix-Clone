# MovieMaster-OTT

MovieMaster
Project Description:
MovieMaster is an OTT platform hosting movies of various genres for a wide audience. Why 
should you choose our platform over Netflix or Prime? We offer many user interactivities that 
these platforms don't have, such as a comment section and chatrooms dedicated to movies, to 
discuss various plots or movie arcs with wild fans like you, as we promote fan 
theories! Additionally, we will recommend our users with movies according to genre page 
they are in, using a recommendation engine, so that our user can deeply emerge in triller, 
fantasy, romance or any genre they love with nonstop related movies.
Moreover, our platform is a safe place. With Firebase authentication, your account is secure 
from potential breaches.

## React
We will use React as the front-end framework for the single page application.
## Firebase
Firebase authentication will be used to authorize users for our website. It will 
include login/signup by email id, Google, and Facebook.
## Socket.io
We will use Socket.io to create a chat room for each movie where users can 
communicate in real-time using the full-duplex communication that Socket.io allows.

## ML/Flask (Python)
We will deploy Content-based Recommender Engine, which will 
recommend user with the similar movies, based on genre. We will use flask framework to 
deploy the Recommender Engine and create an API to fetch the list of the recommended 
movies.
## DigitalOcean
We will deploy our project on digital ocean, using many of the resources 
provided by the platform


## Welcome to guideline: how to run it locally!

There are 3 servers in the zip:
1) Flask-server
2) Express-server
3) React-server

The porject have to run in the above sequence, from 1 to 3.

### Step_1) Running the Flask Server (Contains Our recommender Engine)

Install virtual environment and setting it up inside our flask server.
>> pip install virtualenv
>> cd .\flask-server\

After Changing into the flask-server directory, setup virtual environment using cmd:
>> python -m venv ./venv

This will create a virtual environment folder name venv in the flask-server directory.
Now to activate this venv use cmd (This cmd is according to Windows. May change for Linux/MacOS):
>> .\venv\Scripts\activate

Now to install requirements.txt use cmd:
pip3 install -r requirements.txt

Now the environment for the flask server is created. Run the server using cmd:
>> python app.py

By default the server will run on: http://127.0.0.1:5000
To check if server is running correctly, trying running the urls given below:
To get movies recommendation based on genre, put below url in the browser:
http://127.0.0.1:5000/predict/genre/Comedy/5
To get movies recommendation based on movie, put below url in the browser:
http://127.0.0.1:5000/predict/movie/Toy%20Story/12

If above links work, and one can see a json movie list, the flask server is setup up successfully

Troubleshooting: If some package not install properly one can check it using:
>>pip freeze
This gives list of installed libraries and there dependencies. The list will contain the name of libraries mentioned in requirements.txt and others.

Another issue can be there, if you try to activate venv for the first time (Windows) using cmd:  >> .\venv\Scripts\activate
This gives out error of "cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at 
https:/go.microsoft.com/fwlink/?LinkID=135170."
To solve this run the below cmd in powershell as admistration.
>> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope LocalMachine
and press Y.

Any issue with virtual env, one can refer official page for the same: https://docs.python.org/3/library/venv.html

Note: These commands are given according to Windows. For Linux and Mac it may vary.


### Step_2) Running the Express Server (BackEnd Server)
First open another terminal and change directory to Express-server using cmd:
>> cd .\Express-server\ 

Install all dependencies in package.json using cmd:
>> npm install

Note: Before Running the Express server please start your Redis-server.
Now run the Express server using cmd:
>> npm start

By default it will run at localhost port 8000.
To just check if everythings is working including redis, use this url in your browser:
http://localhost:8000/recommend/genres/Comedy/6
This should return the json list of movies with id, title and image.
This url makes a call to get recommended movies from the flask server, check each title in redis server from given recommended list, if present add it to result else make a API call to TMDB to get movie info and save it in redis for later calls, and finally return result array.


### Step_3) Running the React Server (FrontEnd Server)
Again open another terminal and change the directory to react-server using cmd:
>> cd .\react-server\

Install all dependencies in package.json using cmd:
>> npm install

Now run the React server using cmd:
>> npm start

By default it will run at http://localhost:3000/


Troubleshooting:
Main error can be related to library compatibility with node version. For that we want to mention our project is build on node version: v16.17.0
