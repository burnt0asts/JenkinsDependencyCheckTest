pipeline {
    agent any
    environment {
        NVD_API_KEY = credentials('NVD_API_KEY') // Use the ID you gave to the credential
    }
    stages {
        stage('Checkout SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/burnt0asts/JenkinsDependencyCheckTest'
            }
        }

        stage('OWASP Dependency-Check Vulnerabilities') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML --suppression suppression.xml --nvdApiKey $NVD_API_KEY', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
            }
        }
    }    
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
