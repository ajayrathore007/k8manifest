node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email gauravshekhawat137@gmail.com"
                        sh "git config user.name ajayrathore007"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i '' 's+8946855548/argov2.*+8946855548/argov2:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://ajayrathore007:$aA@8107522894@github.com/ajayrathore007/kubernetesmanifest.git HEAD:main"
      }
    }
  }
}
}
