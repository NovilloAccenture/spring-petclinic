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
  containers:
  - name: maven
    image: maven:alpine
    command:
    - cat
    tty: true
"""
    }
  }
  stages {
    stage('Run maven') {
      steps {
        container('maven') {
          sh 'mvn -version'
          sh 'curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3'
          sh 'chmod 700 get_helm.sh'
          sh './get_helm.sh'
          sh 'helm ls'
          //sh 'mvn sonar:sonar'
        }
      }
    }
    stage(' ') {
      steps {
        container('maven') {
          sh 'mvn -version'
          sh 'ls -la'
  }
}
