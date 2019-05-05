# Jenkins

Run docker-compose up -d


# Etape




## etape 1:

- docker exec -it jenkins/docker bash

- cat /var/jenkins_home/secrets/initialAdminPassword

- prendre le mot de passe affiche par cat 

- cliquer sur installer les pluggins personnaliser et ajouter en plus node.js

- crée son compte 

- http://localhost:8080/configureTools/ --> aller sur nodejs --> ensuite cliquer sur installer nodesjs et appeler en name node

- Ajouter les credentials pour git et dockerhub en global


- Cliquer sur nouveau item

- Select Pipeline script from SCM

- Ajouter l'url d'un repo --> https://github.com/florian92i/devContinu --> avec les bon credential

- Cliquer sur lancer un build 

- Le build a la fin marche pas ça vient de votre projet 







# Get started with Jenkins

1. Run docker-compose up -d

2. cat /var/jenkins_home/secrets/initialAdminPassword in the container

3. Go to [http://localhost:8080/](http://localhost:8080/) and click custom plugins add node js pluggins and install.

4. Then create your admin user.

5. Once the user created, add hub docker credential:
   - Click Credentials > System on the left
   - Under System, click the Global credentials (unrestricted) link to access this default domain. ([click here for quick access](http://localhost:8080/credentials/store/system/domain/_))
   - Click Add Credentials and set the Docker Hub username/password (for the ID, set eemi-devops-dockerhub)
   - Click Add Credentials and set the Git username/password (for the ID, set eemi-devops-git)
   - And save it and return to the dashboard ([http://localhost:8080/](http://localhost:8080/))
   
6. Create a new job   
   - Choose the name of the pipeline like 'Build next app'
   - Then choose pipeline option and confirm
   - Go to the pipeline section at bottom and change the definition Pipeline script to Pipeline script from SCM
   - For the SCM, choose Git and set the Repository URL as follow: https://github.com/florian92i/devContinu
   - Script Path field must be Jenkinsfile
   - add key pub on you server 
   - change  environment variable on file Jenkins for dockerhub remplace ssh <nom_utilisateur>@<ipaddress> -p <num_port> in script
   - Then save the pipeline
   - Click Build now, it will install dependance, run test, create a new image to Docker Hub, and deploy image on serveur, you can run project on server --> add 'sudo docker run nameOfImage'




