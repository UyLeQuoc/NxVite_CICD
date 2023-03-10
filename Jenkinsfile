node {
  agent any
  def commit_id

  stage('Preparation') {
    checkout scm
    sh "git rev-parse --short HEAD > .git/commit-id"
    commit_id = readFile('.git/commit-id').trim()
  }
  stage('Installing dependencies') {
    nodejs(nodeJSInstallationName: 'nodejs') {
      sh 'npm install --loglevel verbose'
    }
  }
  stage('Testing') {
    nodejs(nodeJSInstallationName: 'nodejs') {
      sh 'npm run test'
    }
  }
  stage('Building') {
    nodejs(nodeJSInstallationName: 'nodejs') {
      sh 'npm run build'
    }
  }
  stage('Notify') {
    sh "echo Pipeline is finished and Hello World"
  }
}

