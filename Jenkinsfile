pipeline {
    agent any 
    stages {
        stage('clone repo and clean') { 
            steps {
                bat "rmdir my-app /s /q" 
                // use rmdir /s /q for Windows, rm -rf for linux/mac
                // /s (Deletes a directory tree (the specified directory and all its subdirectories, including all files)
                // /q (Specifies quiet mode. Does not prompt for confirmation when deleting a directory tree. The /q parameter works only if /s is also specified.)
                bat "git clone https://github.com/btwndays/my-app.git"
                bat "mvn clean -f my-app"
            }
        }
        stage('Test') { 
            steps {
                bat "mvn test -f my-app"
            }
        }
        stage('Deploy') { 
            steps {
                bat "mvn package -f my-app"
            }
        }
    }
}