pipeline {
    agent any

    // 🔧 Parameters
    parameters {
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Run Test Stage?')
        string(name: 'VERSION', defaultValue: '1.0', description: 'App Version')
    }

    // 🌍 Environment Variables
    environment {
        APP_NAME = "MyApp"
    }

    // 🛠 Tools (check name in Manage Jenkins → Tools)
    tools {
        maven 'Maven'
    }

    stages {

        // 🏗 Build Stage
        stage('Build') {
            steps {
                echo "Building %APP_NAME% Version %VERSION%"
                bat 'mvn -v'
            }
        }

        // 🧪 Test Stage (Conditional)
        stage('Test') {
            when {
                expression { params.executeTests == true }
            }
            steps {
                echo "Running Tests..."
                bat 'echo Tests executed'
            }
        }

        // 🚀 Deploy Stage
        stage('Deploy') {
            steps {
                echo "Deploying %APP_NAME%..."
                bat 'echo Deployment done'
            }
        }
    }

    // 📦 Post Actions
    post {
        always {
            echo "Pipeline finished (Always runs)"
        }
        success {
            echo "Pipeline SUCCESS 🎉"
        }
        failure {
            echo "Pipeline FAILED ❌"
        }
    }
}
