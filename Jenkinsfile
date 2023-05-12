{
  node {

      stage('Clone repository') {
          checkout scm
      }

      stage('Fargate Task call') {
  steps {
    withCredentials([usernamePassword(credentialsId: 'twistlockDefenderManager', passwordVariable: 'TL_PASS', usernameVariable: 'TL_USER')]) {
      sh 'curl -s -k -u $TL_USER:$TL_PASS https://$TL_CONSOLE/api/v1/defenders/fargate.json?consoleaddr=$TL_CONSOLE -X POST -H "Content-Type:application/json" --data-binary "@fargate.json" | jq . > tw_fargate.json'
      sh 'cat tw_fargate.json'
    }
  }
}

stage('Publish Function') {
  steps {
    archiveArtifacts artifacts: 'tw_fargate.json'
  }
}