# Week 1 — App Containerization

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

Now a ran the **commands**
```bash
export FRONTEND_URL="*" && export BACKEND_URL="*"
python3 -m flask run --host=0.0.0.0 --port=4567
```
And i was able to successfully access the backend api

success response in the terminal
![200-response in the terminal](/images/access-to-backend-api.PNG)

Access to backend api in the browser
![access to backend in the browser](/images/access-to-backend-api-browser.PNG)
