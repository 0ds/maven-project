 
   node{
 
      stage('SCM checkout')
    {
      git 'https://github.com/0ds/maven-project.git'
    }
    
      
      stage('compile-package')
       {
      def mvnHome = tool name: 'maven 3.6.0', type: 'maven'
      sh "${mvnHome}/bin/mvn -B -DskipTests clean package"
      }
    stage('Email-Notification'){
     mail bcc: '', body: 'file attached', cc: '', from: '', replyTo: '', subject: 'error report', to: 'odds.raj@gmail.com'
    }
   }


