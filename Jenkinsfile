node{

def mavenHome = tool name: "maven3.9.3"
//github to pull the code 
stage('CheckOutCode'){
    git branch: 'main', credentialsId: 'gitgub_jenkins', url: 'https://github.com/DevOpsproject-asn/maven_webapp_project.git'
}

//maven build the package
stage('Build'){
    sh "${mavenHome}/bin/mvn clean package"
}

//to send the sonarqube for code quality check 
stage('ExecuteSonarQubeReport'){
    sh "${mavenHome}/bin/mvn clean sonar:sonar"
}

//send to nexus artifact to store all the packages
stage('UploadArtifcatsIntoArtifactoryRepo'){
   sh "${mavenHome}/bin/mvn clean deploy"
}
stage('docker build the image'){
    sh ""
}


}