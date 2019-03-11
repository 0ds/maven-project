 
   node{
 
      stage('SCM checkout')
    {
      git 'https://github.com/0ds/maven-project.git'
    }
    
    try{
      
      stage('compile-package')
       {
      def mvnHome = tool name: 'maven 3.6.0', type: 'maven'
      sh "${mvnHme}/bin/mvn -B -DskipTests clean package"
      }
 #   stage('Email-Notification'){
  #   mail bcc: '', body: 'file attached', cc: '', from: '', replyTo: '', subject: 'error report', to: 'odds.raj@gmail.com'
#    }
   }
      
      catch (err) {
       mail bcc: '', body: "${err}", cc: '', from: '', replyTo: '', subject: 'error report', to: 'odds.raj@gmail.com'
      }
   }    
