
   node{
 
      stage('SCM checkout')
    {
      git 'https://github.com/0ds/maven-project.git'
    }
      
    //try{
      
       parallel firstbranch: {
       stage('compile-package')
       {
      def mvnHome = tool name: 'maven 3.6.0', type: 'maven'
      sh "${mvnHome}/bin/mvn  -B -DskipTests clean package"
      }
       }, secondbranch: {
       stage('checkstyle'){
          def mvnHome = tool name: 'maven 3.6.0', type: 'maven'
           sh "${mvnHome}/bin/mvn checkstyle:checkstyle"
          checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
       }
       }, failFast: true
    
        stage('email-notification-pre'){
           emailext attachLog: true, body: '$(err)', recipientProviders: [upstreamDevelopers()], subject: '', to: 'odds1.raj@gmail.com'

         // mail bcc: '', body: 'HELLO WORLD', cc: '', from: '', replyTo: '', subject: 'error report', to: "${_MY_EMAIL}"
        }
       
//}
      
  //    catch (err) {
    //     stage('email-notification'){
      //    mail bcc: '', body: "${err}", cc: '', from: '', replyTo: '', subject: 'error report', to: "${_MY_EMAIL}"
      //}
     //}
   }    
