# <center>Full Stack</center>

___

## some resources

* [FSND Student Handbook](https://udacity.atlassian.net/wiki/display/BENDH/FSND+Student+Handbook)

* [some best python libraries](http://pypi-ranking.info/alltime)

* [Python FILE Tutorial](http://www.guru99.com/reading-and-writing-files-in-python.html)

* [Google Python Style Guide](https://google.github.io/styleguide/pyguide.html)

* [project submit checklist](https://discussions.udacity.com/t/movie-trailer-website-checklist-read-this-before-you-submit-your-project/39852)

* [udacity feedback extension](http://labs.udacity.com/udacity-feedback-extension/)

* [free domain names](http://labs.udacity.com/udacity-feedback-extension/)

* [Awesome README](https://github.com/matiassingers/awesome-readme)

* [good css reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference)








___

### Tips and tricks:

google search engine:
* "1 hour timer" to get timer and stopwatch
* to open console on chrome: ctrl+shift+j
* in head put the link to the css file before the js file




___

### Python

hashing in python:

``` python
import hashlib

x = hashlib.md5('hello world!')
print(x.hexdigest()) # will print the hashed value
```
there are another hashing library that takes also secret value

``` python
import hmac
hmac.new("secret", "udacity").hexdigest()
```
to hash value in cookies we put it in this form
"value|hashed_value"
but this method is not safe for storing passwords because something called rainbow tables that are available on the internet, so we generate a random string and use it in hashed value ex

name | value
-----|------
ali  | h, salt
where salt is a random string
the problem with most hashing functions that they are designed to be fast but this is not a good thing as computers becomes faster so we use something called `bcrypt`

the order of the hashing algorithms form from fast to slow and form not secure to more secure:

1. crc32
2. md5
3. sha1
4. sha256

* cookie domain and cookie expire
___

### Linux command line:

to use vm with ```vagrant``` first download and install virtual box and vagrant. then create a new dirctory and open the terminal on it write this commands:

``` bash
vagrant init hashicorp/precise64
# don't write this command if you already have a config file
vagrant up # to run the machine
vagrant ssh # to log into the machine
```

to log out or terminate the machine:

``` bash
exit # to log out
vagrant destroy # to terminate the machine
```

more on vagrant read this [article.](https://scotch.io/tutorials/get-vagrant-up-and-running-in-no-time)

to download file form the internet:
``` bash
curl http://udacity.github.io/ud595-shell/stuff.zip -o things.zip # curl is the download command
```


* $uname tells you what operating system you're running on.

* The $host command is a handy interface to the Domain Name System (DNS).
``` bash
expr 2 + 2 # simple calculations
date # to get date and time
uname -a # more info about your os
hostname # computer name
history # view all commands history
unzip things.zip # extract the files
bash --version
```
* you can search the commands history by: ctrl+r
* to print the content of a file:
``` bash
cat file_name.txt #you can give it more than one file
```
* you can use tab for auto completion.
* to analyze a file:
``` bash
wc file.txt # work count: tells the # lines, words, bytes
```
* to get the manual of any command:
``` bash
man command_name # ex: man cowsay
```
* once you done with the manual press q to exit
* both commands and their argument are case sensitive.
* $bc is a simple calculator, to exit it type quit or ctrl+d
* to show the content of a text file:
``` bash
less file_name.txt
# use d for page down and u for page up
# use > to get to last line and < to get to first line
# to go to specific line type line number then enter
# to search for a word /searching_word
# n for the next occurence of the word and N for prev
# search is case sensitive
# you can use regular expression in search  example:
ls *html # all the files that ends in html
ls app*  # starts with app
b*png # starts with b and ends. with png
*.{css, html} # ends with html or css
ls bea?.png # ? match one char
ls be[aeiou]r.png # one char a , e, i, o or u
```

to disable firewall:
``` bash
sudo ufw disable
sudo ufw enable
```
___








### Grunt:

to use Grunt for first time:
1. install nodejs and update npm
2. open terminal
``` bash
npm install -g grunt-cli
```
3. use terminal to go to project directory then:
``` bash
npm init
```
4. follow the instructions to create package.json file
5. then write:
``` bash
npm install grunt --save-dev
```
6. to install plugin
``` bash
npm install grunt-contrib-<blugin_name> --save-dev
npm install grunt-contrib-cssmin --save-dev
```
7. then create the Gruntfile.js



___

### Google app engine:

to install GAE:
1. download the GAE sdk
2. extract and move it to /opt
3. run
``` bash
./google-cloud-sdk/install.sh
./google-cloud-sdk/bin/gcloud init # and follow the instructions
```

to install python extension

``` bash
gcloud components install app-engine-python
```

to start working in a simple example:

``` bash
git clone https://github.com/GoogleCloudPlatform/python-docs-samples
```

then go to this directory and run:
```bash
cd python-docs-samples/appengine/standard/hello_world
dev_appserver.py .
```

then go to browser and open http://localhost:8000 you will see the output

the directory contains two files `app.yaml`, `main.py`:-

**app.yaml:** is the configuration file for GAE and contain the following:

```
application: your_app_id
runtime: python27
api_version: 1
threadsafe: true

handlers:
- url: /.*
  script: main.app

libraries:
- name: jinja2
  version: latest
```
you can add more parameters depending in your needs

**main.py:** is the python script that will run when opening your localhost and contians the following

``` python
import webapp2


class MainPage(webapp2.RequestHandler):
    def get(self):
        self.response.headers['Content-Type'] = 'text/plain'
        self.response.out.write('Hello, World!')

# ex
self.request.get("q") # to get the input from a form with name q


app = webapp2.WSGIApplication([('/', MainPage),], debug=True)
```

___


### Database:





___



### Ideas:-
* make personal website that has tab for:-
    * motivations
    * calendar
    * my to do list
    * my memories
    * ...
