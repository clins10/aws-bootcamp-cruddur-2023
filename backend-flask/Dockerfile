FROM python:3.10-slim-buster

#Inside-Container
#make a new folder inside the container
WORKDIR /backend-flask

#Outside-Container -> Inside-Container
#we are coping "requirement.txt" (outside -> inside) bcos it contains the libraries needed to install in orer to run the app
COPY requirements.txt requirements.txt

#Inside-Container
#this command installs the python libraries used for the app
RUN pip3 install -r requirements.txt

#period(.)     - means everything in the current directory
#1st period(.) - everything in the /backend-flask (outside-container)
#2nd period(.) - everything in the /backend-flask (inside-container)
COPY . .

#set the environment variable, and remain inside when the container is running
ENV FLASK_ENV=development

EXPOSE ${PORT}

#python3 -m flask run --host=0.0.0.0 --port=4567
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]