pipeline {
    agent any
    stages{

    stage('Clone repository') {
        steps{
            script{
                checkout scm
            }
        }
      

    }

    stage('Update GIT') {
        steps{

        
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email vishal.sader@testingxperts.com"
                        sh "git config user.name VishalTx"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+vishal7500/python.*+vishal7500/python:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        // sh "git add ."
                        // sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/Automation-manifest-k8s-Pipeline-1.git HEAD:main"
                        
      }
    }
  }
}
 }
    
   
  }
}

   



            