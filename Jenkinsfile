pipeline {
    agent any
    
    // Define GIT_COMMIT as a parameter (required for rollback)
    parameters {
        string(name: 'GIT_COMMIT', defaultValue: '', description: 'Git commit hash for rollback')
    }
    
    stages {
        stage('Checkout Old Commit') {
            steps {
                script {
                    // Force checkout the specified commit (or latest if not provided)
                    checkout([
                        $class: 'GitSCM',
                        branches: [[name: params.GIT_COMMIT ?: '*/main']], // Fallback to 'main' if no commit given
                        extensions: [],
                        userRemoteConfigs: [[
                            url: 'https://github.com/your/repo.git',
                            credentialsId: 'your-github-credentials' // Replace with your Jenkins credential ID
                        ]]
                    ])
                }
            }
        }
        
        stage('Run Python Script') {
            steps {
                // Use the full path to Python (cross-platform)
                script {
                    if (isUnix()) {
                        sh '/usr/bin/python3 hello_world.py'  // Linux/Mac path
                    } else {
                        bat '"C:/Users/Charan/AppData/Local/Programs/Python/Python310/python.exe" hello_world.py'  // Windows path
                    }
                }
            }
        }
    }
}
