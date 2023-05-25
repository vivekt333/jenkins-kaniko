pipeline {
  agent {
    kubernetes {
      yamlFile 'builder.yaml'
    }
  }
  stages {
    stage('Build with Kaniko') {
      steps {
        container(name: 'kaniko', shell: '/busybox/sh') {
          sh '''#!/busybox/sh
            echo "FROM jenkins/inbound-agent:latest" > Dockerfile
            /kaniko/executor --context `pwd` --destination nexus.bmpdtravel.com:5001/jenkins-agent:kaniko-scm-test
          '''
        }
      }
    }
  }
}
