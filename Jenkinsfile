pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                git 'https://github.com/burnt0asts/JenkinsDependencyCheckTest'
            }
        }
        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML --suppression suppression.xml', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
            }
        }
    }    
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
