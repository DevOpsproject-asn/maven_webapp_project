node{

def mavenHome = tool name: "maven3.8.6"
#github to pull the code 
stage('CheckOutCode'){
git branch: 'development', credentialsId: '166c70a2-1df5-4993-a566-0a795862da8c', url: 'https://github.com/MithunTechnologiesDevOps/maven-web-application.git'
}

#maven build the package
stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

#to send the sonarqube for code quality check 
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

#send to nexus artifact to store all the packages
stage('UploadArtifcatsIntoArtifactoryRepo'){
sh "${mavenHome}/bin/mvn clean deploy"
}


}