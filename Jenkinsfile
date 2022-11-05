pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'donet build eShopOnWeb.sln'
      }
    }

    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'dotnet test tests/UnitTests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTests'
          }
        }

        stage('fuctional') {
          steps {
            sh 'dotnet test tests/FunctionalTests'
          }
        }

      }
    }

    stage('Deployement') {
      steps {
        sh 'dotnet publish eShopOnweb.sln -o /var/aspnet '
      }
    }

  }
}