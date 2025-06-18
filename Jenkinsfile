pipeline { 
    agent any 
 
    tools { 
        maven 'Maven 3.8.7' 
        jdk 'Java 11' 
    } 
 
    stages { 
        stage('Checkout') { 
            steps { 
                git 
'https://github.com/maazbinhasan/Petclinic.git' 
            } 
        } 
 
        stage('Build') { 
            steps { 
                sh 'mvn clean install' 
            } 
        } 
 
        stage('Test') { 
            steps { 
                sh 'mvn test' 
            } 
        } 
 
        stage('Archive Artifact') { 
            steps { 
                archiveArtifacts artifacts: 'target/*.jar', 
fingerprint: true 
            } 
        } 
    } 
 
    post { 
        success { 
            echo '
 ✅
 Build successful!' 
        } 
        failure { 
            echo '
 ❌
 Build failed!' 
        } 
    } 
}
