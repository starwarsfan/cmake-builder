#!groovy

pipeline {
    agent {
        label "docker"
    }
    options {
        timestamps()
        timeout(time: 2, unit: 'HOURS')
        buildDiscarder(logRotator(numToKeepStr: '30', artifactNumToKeepStr: '5'))
        disableConcurrentBuilds()
    }
    environment {
        // In case another branch beside master or develop should be deployed, enter it here
        BRANCH_TO_DEPLOY = 'xyz'
    }
    stages {
        stage('Build image') {
            when {
                not {
                    anyOf { branch 'develop'; branch 'master'; branch "${BRANCH_TO_DEPLOY}" }
                }
            }
            //noinspection GroovyAssignabilityCheck
            parallel {
                stage('Debian') {
                    steps {
                        script {
                            withDockerRegistry(credentialsId: 'Docker-Registry') {
                                sh "docker build -f Debian/Dockerfile --rm -t starwarsfan/cmake-builder-debian:latest ."
                            }
                        }
                    }
                }
                stage('Fedora') {
                    agent {
                        label "docker"
                    }
                    steps {
                        script {
                            withDockerRegistry(credentialsId: 'Docker-Registry') {
                                sh "docker build -f Fedora/Dockerfile --rm -t starwarsfan/cmake-builder-fedora:latest ."
                            }
                        }
                    }
                }
            }
        }
        stage('Build and upload image') {
            when {
                anyOf { branch 'develop'; branch "${BRANCH_TO_DEPLOY}" }
            }
            //noinspection GroovyAssignabilityCheck
            parallel {
                stage('Debian') {
                    steps {
                        script {
                            withDockerRegistry(credentialsId: 'Docker-Registry') {
                                sh "docker build -f Debian/Dockerfile --rm -t starwarsfan/cmake-builder-debian:latest ."
                                sh "docker push starwarsfan/cmake-builder-debian:latest"
                            }
                        }
                    }
                }
                stage('Fedora') {
                    agent {
                        label "docker"
                    }
                    steps {
                        script {
                            withDockerRegistry(credentialsId: 'Docker-Registry') {
                                sh "docker build -f Fedora/Dockerfile --rm -t starwarsfan/cmake-builder-fedora:latest ."
                                sh "docker push starwarsfan/cmake-builder-fedora:latest"
                            }
                        }
                    }
                }
            }
        }
        stage('Info') {
            when {
                branch 'master'
            }
            steps {
                script {
                    sh "echo 'No build steps on master branch performed, use Job 'tagBuilderImage' to perform image releases'"
                }
            }
        }
    }
}
