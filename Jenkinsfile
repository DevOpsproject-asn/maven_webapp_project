pipeline {
 agent any 
 tools{
    maven 'maven3.9.3'
 }
 stages{
    //checkout code from github
    stage('scmcheckout'){
        steps{
            git branch: 'main', credentialsId: 'githubcred', url: 'https://github.com/DevOpsproject-asn/maven_webapp_project.git'
        }
    }
    //build the code and create war packages
    stage('buildthecode'){
        steps{
            sh "mvn clean package"
        }
    }
    //push to sonarqube for code quality check
    //stage('codequalitycheck'){
    //    steps{
    //        sh "mvn clean package sonar:sonar"
    //    }
    //}
    //send the packages to artifcatory repo
    //stage('sendpackagetoartifact'){
    //    steps{
    //        sh "mvn clean deploy"
    //    }
    //}
    //build the docker image 
    //stage('docker build'){
    //    steps{
    //        sh "docker build -t cloudcoker123456/maven_webapp_project2 ."
    //    }
   // }
    //Login into the dockerhub & push the image 
    //stage('docker login&push'){
     //   steps{
     //       withCredentials([string(credentialsId: 'dockerHUB_cred', variable: 'dockerHub')]) {
     //         sh "docker login -u cloudocker123456 -p ${dockerHub}"
     //   }
     //   sh "docker push cloudcoker123456/maven_webapp_project2:latest"
   // }
  //}
}