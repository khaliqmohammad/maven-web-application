node
{  
  def mavenHome = tool name: "maven-3.8.3"
 stage('CheckoutCode')
 {
  git branch: 'development', credentialsId: 'fbeb40d8-5f11-4642-a441-a76662969fcd', url: 'https://github.com/khaliqmohammad/maven-web-application.git'
 }
 stage('Build')
 {
  sh "${mavenHome}/bin/mvn clean package"
  }
  stage('ExecuteSonarQubeReport')
 {
 sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 stage('UploadArtifactIntoNexus')
 {
 sh "${mavenHome}/bin/mvn deploy"
 }
 stage('SendEmailNotification')
 {
     mail bcc: '', body: '''Hi,

Please check build is successful.''', cc: 'm.khaliq562@gmail.com', from: '', replyTo: '', subject: 'Build Over', to: 'abdulkhaliq0562@gmail.com'
 }
} 
