pipeline { 
    agent any 
 
    tools { 
        maven 'Maven 3.8.7' 
        jdk 'Java 11' 
    } 
	environment {
        JAVA_HOME = tool 'Java 11'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }
 
    stages { 
        stage('Checkout') { 
            steps { 
                git branch: 'main', url: 'https://github.com/maazbinhasan/Petclinic.git' 
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
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true 
            } 
        } 
    } 
 
    post { 
        success {
            echo "✅ Build successful!"
        }
        failure {
            echo "❌ Build failed!"
        }
    }
}

