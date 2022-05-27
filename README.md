# Heroku-Python
Assignment repository
here are the all coding for GET API in flask(python framework)

(processWebhook.py)
import flask
import os
from flask import send_from_directory

app = flask.Flask(__name__)

@app.route('/favicon.ico')
def favicon():
    return send_from_directory(os.path.join(app.root_path, 'static'),
                               'favicon.ico', mimetype='image/favicon.png')

@app.route('/')
@app.route('/home')
def home():
    return "Hello World"

if __name__ == "__main__":
    app.secret_key = 'ItIsASecret'
    app.debug = True
    app.run()
    
(Procfile)
web: gunicorn processWebhook:app --log-file -

(requirments.txt)
astroid==2.4.2
autopep8==1.5.4
certifi==2020.12.5
click==7.1.2
Flask==1.1.2
gunicorn==20.0.4
isort==5.5.2
itsdangerous==1.1.0
Jinja2==2.11.3
lazy-object-proxy==1.4.3
MarkupSafe==1.1.1
mccabe==0.6.1
numpy==1.19.2
pycodestyle==2.6.0
pylint==2.6.0
toml==0.10.1
Werkzeug==1.0.1
wrapt==1.12.1

Above are all coding for application which is hosted on heroku




Now i am providing Dockerfile for the static website which is hosted on AWS

FROM ubuntu
RUN apt-get update && apt install -y apache2
RUN apt-get install -y tree openssh-server openssh-client
RUN cd /var/www/html
RUN echo "Hello World" > /var/www/html
RUN service apache2 start 
