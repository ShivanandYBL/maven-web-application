node{
    
echo "job name is: ${env.JOB_NAME}"
echo "build number is: ${env.BUILD_NUMBER}"
echo "node name is: ${env.NODE_NAME}"
echo "jenkins home dir is: ${env.JENKINS_HOME}"
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])   
    
    
def mavenHome = tool name: "maven 3.9.0"

stage('checkoutcode'){
git branch: 'development', credentialsId: '431ee72b-1ba0-42bd-82f1-261082a87ecf', url: 'https://github.com/ShivanandYBL/maven-web-application.git'
}

stage('build'){
sh "${mavenHome}/bin/mvn clean package"
}
 /*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('UploadArtifactIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployApplicationIntoTomcatServer'){

sshagent(['7244d6c6-680a-476d-9abb-12dba2f3c255']) {
   sh "scp -o  StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.7.47:/opt/apache-tomcat-9.0.71/webapps "
}

}
/*
}
