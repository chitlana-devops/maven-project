pipeline
{
agent any
  stages
  {
   stage('SCM Checkout') 
    {steps {git branch: 'master', url: 'https://github.com/chitlana-devops/maven-project'}
    }
    stage('Compile code')
    {steps
     {
       withMaven(jdk: 'localjdk', maven: 'localmaven') {
       sh'mvn compile'
      }
    }
    }
     stage('Testing of Code')
     {steps
      {
       withMaven(jdk: 'localjdk', maven: 'localmaven') {
       sh'mvn test'
      }
      }
     }
     stage('Package of Code')
     {steps
      {
       withMaven(jdk: 'localjdk', maven: 'localmaven') {
       sh'mvn package'
      }
      }
     }
    stage('Code Deployment to Tomcat')
     {steps
      {
       sshagent(['e70bf2d3-03e0-4815-adf2-98a42b8cebe2']) {
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.18.182:/var/lib/tomcat/webapps'
      }
      }
     }
  }
}
