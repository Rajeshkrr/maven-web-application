node{
echo " the job name is ${JOB_NAME}"
echo  "the build number is :${BUILD_NUMBER}"
echo " the node name is : ${NODE_NAME}"
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome= tool name: 'maven-3.9.1' 
stage('CheckoutCode'){
git branch: 'development', credentialsId: '87801f3a-d0d7-4fc4-90e1-22f4e026e931', url: 'https://github.com/Rajeshkrr/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
   /*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}
stage('DeployAppintoTomcat'){
sshagent(['ad51fc7e-8c85-4378-b7bf-06fff643767d']) {
   sh"scp -o  StrictHostKeyChecking=no 
 target/maven-web-application.war ec2-user@3.1.194.249:/opt/apache-tomcat-9.0.73/webapps
 "
}
}
*/
} 
