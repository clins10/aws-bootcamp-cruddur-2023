# Week 1 — App Containerization

## **Containerizing The Backend** locally, issues encountered and how i solved them

Below, the **commands** and errors i encountered following the [instructional guide for week-1](https://github.com/omenking/aws-bootcamp-cruddur-2023/blob/week-1/journal/week1.md), and how i tackled them

### COMMAND
```bash
cd backend-flask
python3 -m flask run --host=0.0.0.0 --port=4567
```

- No module named flask  error
![module not found](/images/module-not-found-error.PNG)

- SOLUTION
```bash
cd ..
pip install flask
```

After solving the **No module named flask** error i **cd ..** and ran the **python3 -m flask run --host=0.0.0.0 --port=4567** command and encountered yet another error below as shown in the screenshot

![no flask-cors error](/images/no-module-named-flask-cors.PNG)

- SOLUTION
```bash
pip install flask-cors
```

Now i ran the **commands**
```bash
export FRONTEND_URL="*" && export BACKEND_URL="*"
python3 -m flask run --host=0.0.0.0 --port=4567
```
And i was able to successfully access the backend api

#### Success response in the terminal

![200-response in the terminal](/images/access-to-backend-api.PNG)

#### Access to backend api in the browser
![access to backend in the browser](/images/access-to-backend-api-browser.PNG)


## Building The Container

```bash
cd ..
docker build -t  backend-flask ./backend-flask
```
## Run The Container

```bash
docker run --rm -p 4567:4567 -it -e FRONTEND_URL='*' -e BACKEND_URL='*' backend-flask
```

### Running the container in detachable mode
| the **--rm** tells docker to remove the container whenever it's stopped

```bash
docker container run --rm -p 4567:4567 -d backend-flask
```
### Some Useful Docker Commands

- Get the ID of the running container or the images runnings
```bash
docker ps
docker images
```

- Check Container logs
```bash
docker logs CONTAINER_ID -f
docker logs backend-flask -f
docker logs $CONTAINER_ID -f
```
- Debugging adjacent containers with other containers
```bash
docker run --rm -it curlimages/curl "-X GET http://localhost:4567/api/activities/home -H \"Accept: application/json\" -H \"Content-Type: application/json\""
```

- Login to the Running container
```bash
docker exec CONTAINER_ID -it /bin/bash
```
- Delete an image
```bash
docker image rm backend-flask --force
```
- Overriding port
```bash
FLASK_ENV=production PORT=8080 docker run -p 4567:4567 -it backend-flask
```

## **Containerizing The Frontend**

Here just as specified the in the guide for week1
**cd** to the main working directory which is **aws-bootcamp-cruddur-2023**
then run the below command, to install the needed node.js modules

```bash
cd frontend-react-js && npm i
```
And 
```bash
cd ..
```
|| to go back the main working directory

#### Created a **Dockerfile** in the **frontend-react-js** directory for building of **frontend image**

#### Build the Container
```bash
docker build -t frontend-react-js ./frontend-react-js
```

#### Run the container in detached mode
```bash
docker run -p 3000:3000 -d frontend-react-js
```
##### That runs without error


## Running Multiple Containers

In the root directory i create a **docker-compose.yaml** file
- Run 
```bash
docker-compose up
```
#### Frontend result
![front-screenshot](/images/)

#### Backend result
![backend result browser](/images/)



## Adding DynamoDB Local and Postgres

Time to add some database services, we ain't making of them not just yet


## HomeWork - Implementing **Frontend and Backend Notifactions** Page

- Backend Notification page
following the video on [Write a Flask Backend Endpoint for Notifications](https://www.youtube.com/watch?v=k-_o0cCpksk&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=28) i was able to write the backend api for the notification successfully without stress

### The output
![flask backend for notification](/images/)
  


- Frontend Notifications page
following the video on [Write a React Page for Notifications](https://www.youtube.com/watch?v=k-_o0cCpksk&list=PLBfufR7vyJJ7k25byhRXJldB5AiwgNnWv&index=28) i was able to write the React code for the notification successfully without stress, and also went ahead to implement an **active** feature for **notifications, and messages pages** to improve the user experience - letting the users know which page they are currently on

and arrived at the result as shown below
![frontend notification page](/images/)