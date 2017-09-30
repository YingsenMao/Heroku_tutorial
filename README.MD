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
* Procfile explicitly declare which parts of your application are runnable. Procfile must be placed in the root directory of your application. It lists procces types. Each process type is a declaration of a command that is executed when a dyno of that process type is started. Blow is one process type.
```
<process type>: <command>
```
The syntax is defined as:
* process type: an alphanumeric string, is a name for your command, such as *web*, *worker*, etc.
* command: a command line to launch the process.
