pipeline {
  agent {
    kubernetes {
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  nodeSelector:
    openstack-control-plane: enabled
  containers:
  - name: maven
    image: maven:alpine
    command:
    - cat
    tty: true
  - name: docker-dind
    image: docker-dind
    securityContext:
      privileged: true
    command:
    - cat
    tty: true
"""
    }
  }
  stages {
    stage('Test Stage1') {
      steps {
        container('maven') {
          sh 'mvn -version'
        }
        container('docker-dind') {
          sh 'cd /root && docker build -t busybox-with-ftp .'
        }
      }
    }
  }
}