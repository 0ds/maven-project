pipeline
{
  stages
  {
      stage('SCM checkout')
    {
      steps
      {
      git 'https://github.com/0ds/maven-project.git'
  
      }
    }
    
      
      stage('compile-package')
    {
      steps
      {  
      def mvnHome = tool name: 'maven 3.6.0', type: 'maven'
      sh "${mvnHome}/bin/mvn -B -DskipTests clean package"
      }
    }
  }
}   
