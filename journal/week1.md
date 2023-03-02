# Week 1 — App Containerization

### Running the docker command locally, issues encountered and how i solved them

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
