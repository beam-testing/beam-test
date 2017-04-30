#!groovy
try {
    stage('Build') {
        node {
            checkout scm
            echo 'hello to the world'
            sh 'ls -l'
            stash 'all'
        }
    }
    
    stage('Test') {
        parallel unitTest: {
            node {
                unstash 'all'
                echo 'ut'
                sh 'ls -l'
            }
        },
        codeStyle: {
            node {
                unstash 'all'
                echo 'cs'
                sh 'ls -al'
            }
        }
    }
} catch (Exception e) {
    echo e
}
