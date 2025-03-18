import groovy.json.*

def parseJsonToMap(String json) {
    final slurper = new JsonSlurperClassic()
    return new HashMap<>(slurper.parseText(json))
}
pipeline {
    agent any
    //triggers {
       // cron('H/15 * * * *')
    //}
	 tools { 
        maven 'M3' 
        jdk 'java' 
    }
    stages {
        	stage('\u2776 CheckOut') {
            steps {
				echo "\u2600 BUILD_URL=${env.BUILD_URL}"
                //checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/sasikumarduraisamy/myApp.git']]])
				git url : 'https://github.com/sasikumarduraisamy/configs.git'
             }
        }
        
        stage('\u2705 Initialize') {
            steps {
                
				script{
                def inpJson = readFile file: 'jenkins.json'
				println inpJson
                def map = parseJsonToMap(inpJson)
                //println map
				//println inpJson.test.appName
				//println inpJson.test[1].appName
				echo  "appName = ${map.App1.appName}"
				echo  "appID = ${map.App1.appID}"
                echo  "flag = ${map.Flag}"
				}
            }
        }		
			
		stage('Build') {
		    steps {
		    sh 'echo "Build" '
		    }
        }
        stage('Build Environment & Deploy') {
            steps {
            sh 'echo "Build Environment & Deploy" '
            }
        }		
		
    } 
}
