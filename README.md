# Getting Started [Mac OS]

## Installing Docker
Install Docker  

`brew cask install docker`

Once it's done installing, open up the application Launcher and start Docker. You'll be prompted for your password to complete the installation.

**At this time, there is no need to create a Docker ID if you don't have one.**


## Clone Repository
Open up a **Terminal** and navigate to a folder where you maintain your projects. In my case, I keep my projects in a **Projects** folder within my home directory.

To clone the repository, run  

`git clone --single-branch -b get-started https://github.com/ChicagoAssistant/chicago-assistant.git`

If you already have the repository cloned to your computer, copy the get-started repo to your machine by running

`git checkout --track origin/get-started`


## Create Your Own Branch
Create your own branch by running (**NOTE: do not use the brackets**):  

`git branch [yourname]-dev`  

Switch to your newly created branch:  

`git checkout [yourname]-dev`

Add everything and push your changes:  

`git add .`  
`git commit -m"initial commit"`  
`git push`

## Build Docker Image
Now, we're going to build the Docker Image. This make take around 10 minutes to complete.  

`docker build -t chicago-assistant .`

Once complete, you should be all set to start building a Chicago Assistant functionality! Before we get there, though, let's see exactly how that would happen.


## Starting Up the Container

You can start our virtual container environment by running:

`docker run --rm --name chicago-assistant -it -v [path for repo]:/chicago-assistant chicago-assistant bash`

Make sure to replace [path for repo] with the full path of your local repository for this project. So, in my case, my full path would be

`docker run --rm --name chicago-assistant -it -v /Users/vanguiano/Projects/chicago-assistant:/chicago-assistant chicago-assistant bash`

You'll know you've successfully started up the virtual container when you see:

`root@[somenum_letters]:/#`

Finally, you should navigate to your project repository by running:

`cd chicago-assistant`


## Training the Models

You can train the NLU and core functions of our project by running the following:

`make train-nlu`

`make train-core`

Running these commands should create a new folder in your repo called `models`.

## Chatting with the Bot

To chat with the newly trained bot, you can run:

`make run-cmdline`

and after a few seconds you should see (**Ignore the warnings**):

`WARNING  py.warnings  - /usr/local/lib/python3.5/site-packages/pykwalify/core.py:99: UnsafeLoaderWarning:
The default 'Loader' for 'load(stream)' without further arguments can be unsafe.
Use 'load(stream, Loader=ruamel.yaml.Loader)' explicitly if that is OK.
Alternatively include the following in your code:

  import warnings
  warnings.simplefilter('ignore', ruamel.yaml.error.UnsafeLoaderWarning)

In most other cases you should consider using 'safe_load(stream)'
  data = yaml.load(stream)

Bot loaded. Type a message and press enter: `

Try talking to it!
