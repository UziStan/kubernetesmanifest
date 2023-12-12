node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
         userRemoteConfigs: [[credentialsId: 'github', url: 'https://github.com/UziStan/kubernetesmanifest.git']]) {
 {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email uzomasokonyia@gmail.com"
                        sh "git config user.name UziStan"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+deejayz/test.*+deejayz/test:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://UziStan:${GIT_ACCESS_TOKEN}:@github.com/UziStan/kubernetesmanifest.git HEAD:main"
      }
    }
  }
}
