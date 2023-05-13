node {
  stage('Clone repository') {
    checkout scm
  }
  stage('Fargate Task call') {
    withCredentials([usernamePassword(credentialsId: 'twistlockDefenderManager', passwordVariable: 'TL_PASS', usernameVariable: 'TL_USER')]) {
      sh 'curl -s -k -u $TL_USER:$TL_PASS https://us-east1.cloud.twistlock.com/api/v1/defenders/fargate.json?consoleaddr=us-east1.cloud.twistlock.com -X POST -H "Content-Type:application/json" --data-binary "@fargate.json" | jq . > tw_fargate.json'
      sh 'cat tw_fargate.json'
    }
  }
  stage('Publish Function') {
    steps {
      archiveArtifacts artifacts: 'tw_fargate.json'
    }
  }
}
