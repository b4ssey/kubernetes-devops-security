@Library('slack') _

pipeline {
  agent any

   environment {
    deploymentName = "devsecops"
    containerName = "devsecops-container"
    serviceName = "devsecops-svc"
    imageName = "b4ssey/numeric-app:${GIT_COMMIT}"
    applicationURL = "http://devsecops-demo-ekemini.eastus.cloudapp.azure.com"
    applicationURI = "/increment/99"
  }

  stages {
    //   stage('Build Artifact') {
    //         steps {
    //           sh "mvn clean package -DskipTests=true"
    //           archive 'target/*.jar' 
    //         }
    //     }   
    //     stage('Unit Tests - JUnit and Jacoco') {
    //   steps {
    //     sh "mvn test"
    //   }
    // }

    // stage('Mutation Tests - PIT') {
    //   steps {
    //     sh "mvn test-compile org.pitest:pitest-maven:mutationCoverage"
    //   }
    // }



    // stage('SonarQube - SAST') {
    //   steps {
    //     withSonarQubeEnv('SonarQube') {
    //       sh "mvn clean verify sonar:sonar -Dsonar.projectKey=numeric-application -Dsonar.host.url=http://devsecops-demo-ekemini.eastus.cloudapp.azure.com:9000 -Dsonar.login=sqp_773d74cccb2691c883cb83c6ecf56874ad0e33bc"
    //     }
    //     timeout(time: 2, unit: 'MINUTES') {
    //       script {
    //         waitForQualityGate abortPipeline: true
    //       }
    //     }
    //   }
    // }    

    // stage('Vulnerability Scan - Docker') {
    //   steps {
    //     parallel(
    //       "Dependency Scan": {
    //         sh "mvn dependency-check:check"
    //       },
    //       "Trivy Scan": {
    //         sh "bash trivy-docker-image-scan.sh"
    //       },
    //       "OPA Conftest": {
    //         sh 'docker run --rm -v $(pwd):/project openpolicyagent/conftest test --policy opa-docker-security.rego Dockerfile'
    //       }
    //     )
    //   }
    // }
    
    // stage('Docker Build and Push') {
    //   steps {
    //     withDockerRegistry([credentialsId: "docker-hub", url: ""]) {
    //       sh 'printenv'
    //       sh 'sudo docker build -t b4ssey/numeric-app:""$GIT_COMMIT"" .'
    //       sh 'docker push b4ssey/numeric-app:""$GIT_COMMIT""'
    //     }
    //   }
    // }

    // // stage('Vulnerability Scan - Kubernetes') {
    // //   steps {
    // //     sh 'docker run --rm -v $(pwd):/project openpolicyagent/conftest test --policy opa-k8s-security.rego k8s_deployment_service.yaml'
    // //   }
    // // }

    // stage('Vulnerability Scan - Kubernetes') {
    //   steps {
    //     parallel(
    //       "OPA Scan": {
    //         sh 'docker run --rm -v $(pwd):/project openpolicyagent/conftest test --policy opa-k8s-security.rego k8s_deployment_service.yaml'
    //       },
    //       "Kubesec Scan": {
    //         sh "bash kubesec-scan.sh"
    //       }
    //       // ,
    //       // "Trivy Scan": {
    //       //   sh "bash trivy-k8s-scan.sh"
    //       // }
    //     )
    //   }
    // }

    // //  stage('Kubernetes Deployment - DEV') {
    // //   steps {
    // //     withKubeConfig([credentialsId: 'kubeConfig']) {
    // //       sh "sed -i 's#replace#b4ssey/numeric-app:${GIT_COMMIT}#g' k8s_deployment_service.yaml"
    // //       sh "kubectl apply -f k8s_deployment_service.yaml"
    // //     }
    // //   }
    // // }

    // stage('K8S Deployment - DEV') {
    //   steps {
    //     parallel(
    //       "Deployment": {
    //         withKubeConfig([credentialsId: 'kubeConfig']) {
    //           sh "bash k8s-deployment.sh"
    //         }
    //       },
    //       "Rollout Status": {
    //         withKubeConfig([credentialsId: 'kubeConfig']) {
    //           sh "bash k8s-deployment-rollout-status.sh"
    //         }
    //       }
    //     )
    //   }
    // }

    // stage('Integration Tests - DEV') {
    //   steps {
    //     script {
    //       try {
    //         withKubeConfig([credentialsId: 'kubeConfig']) {
    //           sh "bash integration-test.sh"
    //         }
    //       } catch (e) {
    //         withKubeConfig([credentialsId: 'kubeConfig']) {
    //           sh "kubectl -n default rollout undo deploy ${deploymentName}"
    //         }
    //         throw e
    //       }
    //     }
    //   }
    // }

    //  stage('OWASP ZAP - DAST') {
    //   steps {
    //     withKubeConfig([credentialsId: 'kubeConfig']) {
    //       sh 'bash zap.sh'
    //     }
    //   }
    // }

      stage('Testing Slack') {
      steps {      
          sh 'exit 1'
      }
    }
     
    }

    post {
      always {
        // junit 'target/surefire-reports/*.xml'
        // jacoco execPattern: 'target/jacoco.exec'
        // // pitmutation mutationStatsFile: '**/target/pit-reports/**/mutations.xml'
        // dependencyCheckPublisher pattern: 'target/dependency-check-report.xml'
        // publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, keepAll: true, reportDir: 'owasp-zap-report', reportFiles: 'zap_report.html', reportName: 'HTML ReportOWASP ZAP HTML report', reportTitles: 'OWASP ZAP HTML report', useWrapperFileDirectly: true])
        sendNotification currentBuild.result
      }

      // success {

      // } failure {

      // }
    }
}