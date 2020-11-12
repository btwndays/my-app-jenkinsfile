pipeline {
    agent any 
    stages {
        stage('Clone Repo and Clean') { 
            steps {
                bat "rmdir my-app-jenkinsfile /s /q" // inserted this line after my-app-jenkinsfile folder initially created. 
                // use rmdir /s /q for Windows, rm -rf for linux/mac
                // /s (Deletes a directory tree (the specified directory and all its subdirectories, including all files)
                // /q (Specifies quiet mode. Does not prompt for confirmation when deleting a directory tree. The /q parameter works only if /s is also specified.)
                bat "git clone https://github.com/btwndays/my-app-jenkinsfile.git"
                bat "mvn clean -f my-app-jenkinsfile"
            }
        }
        stage('Test') { 
            steps {
                bat "mvn test -f my-app-jenkinsfile"
            }
        }
        stage('Package') { 
            steps {
                bat "mvn package -f my-app-jenkinsfile"
            }
        }
    }
}
