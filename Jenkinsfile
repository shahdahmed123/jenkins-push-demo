pipeline {
    agent any

    parameters {
        string(name: 'VERSION', defaultValue: '1.0.0', description: 'Application version')
        choice(name: 'ENV', choices: ['dev', 'test', 'prod'], description: 'Select environment')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Run unit tests before build?')
    }

    environment {
        APP_NAME = 'jenkins-push-demo'
    }

    stages {
        stage('Checkout') {
            steps {
                echo "🔍 Checking out branch: ${env.BRANCH_NAME}"
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo "🏗 Building ${env.APP_NAME} v${params.VERSION}"
                echo "Target environment: ${params.ENV}"
                // مثال: أوامر البناء الفعلية هنا
                // sh 'npm install && npm run build'
            }
        }

        stage('Test') {
            when {
                expression { return params.RUN_TESTS }
            }
            steps {
                echo "🧪 Running tests..."
                // sh 'npm test'
            }
        }

        stage('Deploy') {
            when {
                expression { return env.BRANCH_NAME == 'master' && params.ENV == 'prod' }
            }
            steps {
                echo "🚀 Deploying ${APP_NAME} version ${params.VERSION} to production!"
                // sh "./deploy.sh ${params.ENV}"
            }
        }
    }

    post {
        success {
            echo "✅ Build successful for branch: ${env.BRANCH_NAME}"
        }
        failure {
            echo "❌ Build failed for branch: ${env.BRANCH_NAME}"
        }
    }
}
