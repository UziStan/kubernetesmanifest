node {
    def app

   environment {
        GIT_ACCESS_TOKEN = credentials('github') 
    }

    stage('Clone repository') {
      

        checkout scm
    }

    stages {
        stage('Update GIT') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    script {
                        checkout([$class: 'GitSCM', 
                                  branches: [[name: 'main']], 
                                  doGenerateSubmoduleConfigurations: false, 
                                  extensions: [], 
                                  userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/UziStan/kubernetesmanifest.git']]])

                        sh "git config user.email uzomasokonyia@gmail.com"
                        sh "git config user.name UziStan"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+deejayz/test.*+deejayz/test:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://UziStan:${GIT_ACCESS_TOKEN}@github.com/UziStan/kubernetesmanifest.git HEAD:main"
                    }
                }
            }
        }
    }
  }







