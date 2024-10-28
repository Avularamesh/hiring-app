pipeline {
    agent any

    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main', description: 'Enter the branch to build')
        choice(name: 'BUILD_TYPE', choices: ['Debug', 'Release'], description: 'Select the build type')
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo "Cloning the branch: ${params.BRANCH_NAME}"
                git branch: "${params.BRANCH_NAME}", url: 'https://github.com/Avularamesh/hiring-app.git'
            }
        }

        stage('Build Project') {
            steps {
                echo "Building in ${params.BUILD_TYPE} mode"
                sh '''
                    if [ "$BUILD_TYPE" = "Debug" ]; then
                        echo "Running Debug Build..."
                    else
                        echo "Running Release Build..."
                    fi

                    # Call Maven
                    mvn clean install
                '''
            }
        }
    }
}
