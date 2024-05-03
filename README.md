## CI/CD Pipeline using Jenkins

I built CI/CD pipeline for a web application using Jenkins. I used - [the Curriculum App](https://github.com/heyitsazar/curriculum-app-4cicd) to create this.

## Technologies
- Debian servers running on Linode (Jenkins from Linode marketplace)
- Jenkins
- Docker & Dockerhub
- Github
- Some command line for settings things up

### Project Architecture

![jenkins_architecture_balsamiq_diagram2](https://user-images.githubusercontent.com/10039233/190653544-48ea7cb1-bde8-4bf6-97b8-c1ff5bf854d2.png)

### Setting Up Linode
- [Jenkins in the Linode marketplace](https://www.linode.com/marketplace/apps/linode/jenkins/)

- Configuring Jenkins - admin account, plugins, settings
- Deploying an app to Github and using the Jenkins Github plugin  
- Using Jenkins to test and deploy to Dockerhub
- Another Linode server will be watching for updates on Dockerhub and pull & run the updated container  
- Reviewing Jenkins features like build history

### Jenkins Pipelines
Shell scripts:

```shell
ls -la

cd curriculum-front && npm i && npm run test:unit

docker build -f curriculum-front/Dockerfile . -t fuze365/curriculum-front

docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD

docker push heyitsazar/curriculum-front:latest
```

### SSH'ing into Linode Servers (installing Git)

Commands for installing Git and Node on server:

```shell
# install Git
apt install git
git --version

# node version 16 (comes with npm)
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
apt-get install -y nodejs
node --version
npm --version
```
