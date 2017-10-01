## Application
Heroku lets you deploy, run and manage **applications** written in Ruby, Node.js,Java, Python, Clojure, Scala, Go and PHP.  
*Applications* consist of your *source code*, *a description of any dependencies*, and a *Procfile*.  
* For Python, A description of any dependencies is *requirements.txt* or *Pipfile* in the root directory  
The example of *Pipfile* is:
```
[[source]]
url = "https://pypi.python.org/simple"
verify_ssl = true

[packages]
dj-database-url = "*"
django = "*"
gunicorn = "*"
psycopg2 = "*"
whitenoise = "*"

[requires]
python_version = "3.6"
```
You can automatically populate the requirement.txt file by using:
```
pip freeze > requirements.txt
```
* Procfile explicitly declare which parts of your application are runnable. Procfile must be placed in the root directory of your application. It lists procces types. Each process type is a declaration of a command that is executed when a dyno of that process type is started. Blow is one process type.
```
<process type>: <command>
```
An example is:
```
web: gunicorn --pythonpath appName appName.wsgi --log-file -
```
Another example is:
```
web: gunicorn gettingstarted.wsgi --log-file -
```
The syntax is defined as:
* process type: an alphanumeric string, is a name for your command, such as *web*, *worker*, etc.
* command: a command line to launch the process.  
You can create a Application either in your account on website or by using the below code:
```
heroku create
``` 
You can use the **git remote** command to confirm that a remote named heroku has been set for you app:
```
git remote -v
```
If you have already created your Heroku app, you can easily add a remote to your local repository with the heroku git:remote command. All you need is your Heroku app’s name:
```
heroku git:remote -a thawing-inlet-61413
```
## Deployment
**Git** and **Heroku CLI** need to be installed.  
You need to initialize a local Git repository and commit your application code to it. Below is an example.  
```
cd myapp
git init
git add .
git commit -m "First commit"
```
You can push the code from your local repository's master brand to your heroku remote as follows:
```
git push heroku master
```

## dyno
dyno is a lightweight Linux container that runs the command specifed in the **Procfile**. You can check how many dynos are runnig as:
```
heroku ps
```
By default, your app is deployed on a free dyno. Free dynos will sleep after a half hour of inactivity (if they don’t receive any traffic). This causes a delay of a few seconds for the first request upon waking. 
## Basic Command
1. Login and authenticatation
```
heroku login
```
Run it after Heroku CLI is installed. Authenticating is required to allow both the heroku and git commands to operate.
2. See all deployed applications
```
heroku apps --all
```
3. See all add-ons
```
heroku addons
```
4. See list of basic CLI commands
```
heroku help
```