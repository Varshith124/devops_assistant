pipeline {
    agent any
    stages {
         stage('Checkout Old Commit') {
            steps {
                script {
                    // Get the commit from the stable build (passed as parameter)
                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: params.GIT_COMMIT]],
                        extensions: [],
                        userRemoteConfigs: [[url: 'https://github.com/your/repo.git']]
                    ])
                }
            }
        }
        stage('Run python Script') {
            steps {
                // Use the full path to your Python executable (from 'where python')
                bat '"C:/Users/Charan/AppData/Local/Programs/Python/Python310/python.exe" hello_world.py'
           }
        }

    }
}
