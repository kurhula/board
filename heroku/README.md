# Building and Deploying the App with Heroku

# Local development
* Clone the repo: ```git clone git@github.com:kurhula/board.git```. This repo has been forked from [RestyaPlatform/board](https://github.com/RestyaPlatform/board).
* Specify which docker compose YML to build. ```docker compose -f docker-compose.yml up```

## Create Heroku app

Make sure Heroku CLI is installed. If not, run ```bash scripts/heroku/install_heroku_ubuntu_curl_script.sh``` from the scripts repo. See Heroku CLI in the references below if you don't have access to the scripts repo.

### Heroku CLI
* Type ```heroku create board-kurhula```. 

### Heroku Dashboard
* Go to https://dashboard.heroku.com/apps
* Click "New"
* Click "Create new app"
* Input app details. ```App-name: board-kurhula```.
* Click "Create app".

## Deploy the app

### Heroku CLI
* Make sure you're logged into Heroku on the terminal: ```heroku auth:login -i```. Input your password when prompted. This is the prefered interactive way when using WSL (Windows Subsystem to Linux) as the browser might not open up.
* Make sure you're logged into the Heroku Container Registry in order to push images. ``` heroku auth:token | docker login --username=_ registry.heroku.com --password-stdin```.
* Push container to the registry. ```heroku container:push web -a board-kurhula```.
* Deploy container to Heroku. It will build there. ```heroku container:release web -a board-kurhula```.

## Link to GitHub repo
* https://dashboard.heroku.com/apps
* https://dashboard.heroku.com/apps/board-kurhula
* https://dashboard.heroku.com/apps/board-kurhula/deploy/github

## References
* https://devcenter.heroku.com/articles/local-development-with-docker-compose
* https://salesforce.stackexchange.com/questions/344901/heroku-container-push-fail-no-basic-auth-credentials-error-docker-push-exit/348117#348117?newreg=d017b28c66ab4b42a158488d05c0b512
* https://stackoverflow.com/questions/71165830/go-application-failed-to-connect-to-local-postgresql-database-got-error-cannot-p
* https://devcenter.heroku.com/articles/heroku-cli
* https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers
* https://docs.docker.com/compose/reference/
* [container-registry-and-runtime](https://devcenter.heroku.com/articles/container-registry-and-runtime)