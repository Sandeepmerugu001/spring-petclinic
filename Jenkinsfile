pipeline {
    agent{
    	label  'L1'
    }
    triggers {
        pollSCM('* * * * *')
    }
    parameters {
         choice(name: 'mvn', choices: ['mvn package', 'mvn test', 'mvn validate'], description: 'this is options') 
         }
    stages {
        stage('clone') {
            steps {
                git url:'https://github.com/muthyalasaikiran/spring-petclinic.git',
                    branch: 'main'
            }
        }
	stage('install'){
		steps{
		sh 'sudo apt install openjdk-17-jdk -y'
		sh 'sudo apt install maven -y'
		}
	}
        stage('build') {
            steps {  
                 
                sh '$mvn'
            

            }
    }
    	stage('deploy'){
		steps{
		  sh 'java -jar /target/*.jar'
		}
	}
    
    }

}
