node {
  stage('Clone repository') {
    checkout scm
  }
stage('Fargate Task call') {
          withCredentials([usernamePassword(credentialsId: 'twistlockDefenderManager', e54a0b24-5934-4cf0-94d7-b8765601b7de:TmGjLtV3DQc5k+CFW/90Uxg3l1s=)]) {
              sh 'curl -s -k -u e54a0b24-5934-4cf0-94d7-b8765601b7de:TmGjLtV3DQc5k+CFW/90Uxg3l1s= https://us-east1.cloud.twistlock.com/api/v1/defenders/fargate.json?consoleaddr=us-east1.cloud.twistlock.com -X POST -H "Content-Type:application/json" --data-binary "@fargate.json" | jq . > tw_fargate.json'
      sh 'cat tw_fargate.json'
          }
      }
  stage('Publish Function') {
    steps {
      archiveArtifacts artifacts: 'tw_fargate.json'
    }
  }
}
