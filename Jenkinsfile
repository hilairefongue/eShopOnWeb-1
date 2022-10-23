pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet build eShopOnWeb.sln'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/Unittests'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/integrationtest'
          }
        }

        stage('Fontionnel') {
          steps {
            sh 'dotnet test tests/fonctionaltest'
          }
        }

      }
    }

    stage('Deploiement') {
      steps {
        sh 'dotnet publish eShopOnWeb.sln -o /var/aspnet'
      }
    }

  }
}