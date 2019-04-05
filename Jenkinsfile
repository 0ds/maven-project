properties([parameters([choice(choices: ['master', 'branch1', 'branch2'], description: 'select branch', name: 'branch_choise')])])

node{
 
      stage('SCM checkout')
    {
       git url: 'https://github.com/0ds/maven-project', branch: "${branch_choise}"
    }
      
    //try{
      
   /*    parallel firstbranch: {
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
    */  
   /*    stage('Sonarqube-Analysis')
       {
      def mvnHome = tool name: 'maven 3.6.0', type: 'maven'
         def sonarHome= tool name: 'sonarqube', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
      
          withSonarQubeEnv('sonarqube') {
      sh "${sonarHome}/bin/sonar-scanner"
          }
          }
    */
     stage('email-notification-pre'){
         //    emailext attachLog: true, attachmentsPattern: '**/report-task.txt', body: 'report', recipientProviders: [upstreamDevelopers()], subject: '', to: 'odds1.raj@gmail.com'
        
        
          mail bcc: '', body: 'HELLO WORLD', cc: '', from: '', replyTo: '', subject: 'error report', to: 'odds1.raj@gmail.com'
        }
      
//}
      
  //    catch (err) {
    //     stage('email-notification'){
      //    mail bcc: '', body: "${err}", cc: '', from: '', replyTo: '', subject: 'error report', to: "${_MY_EMAIL}"
      //}
     //}
   }    
