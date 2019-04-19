properties([parameters([choice(choices: ['master', 'branch1', 'branch2'], description: 'select branch', name: 'branch_choise')])])

node{
 
      stage('SCM checkout')
    {
       git url: 'https://github.com/0ds/maven-project', branch: "${branch_choise}"
    }
      
    try{
      
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
          mail bcc: '', body: 'Built Pass', cc: '', from: '', replyTo: '', subject: 'Jenkins Report', to: "${_MY_EMAIL}"
        }
     
}
      
      catch (err) {
        stage('email-notification'){
          mail bcc: '', body: 'Built Fail', cc: '', from: '', replyTo: '', subject: 'Jenkins report', to: "${_MY_EMAIL}"
      }
     }
   }    
