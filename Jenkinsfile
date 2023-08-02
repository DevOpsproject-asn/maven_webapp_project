node{

def mavenHome = tool name: "maven3.9.3"
echo "Jenkins url is: ${env.JENKINS_URL}" 
echo "Node Name is: ${env.NODE_NAME}"
echo "Job Name is: ${env.JOB_NAME}"

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
//docker image create
stage('docker build the image'){
    sh "docker build -t cloudoker123456/maven_webapp_project1 ."
}
stage('dockerlogin&pushtoregistry'){
    withCredentials([string(credentialsId: 'docker_cred', variable: 'dockerHub')]) {
    sh "docker login -u cloudocker123456 -p ${dockerHub}"
    }
    sh "docker push cloudoker123456/maven_webapp_project1"
}
}