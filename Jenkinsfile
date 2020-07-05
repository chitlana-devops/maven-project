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
    }
  }
}
