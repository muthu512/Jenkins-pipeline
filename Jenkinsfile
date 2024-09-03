def agents = "$AGENTS".toString()
def agentLabel = "${ println 'Agents: ' + agents; return agents; }"

pipeline {
    agent none

    stages {
        stage('Prep') {
            steps {
                script {
                    if (agents == null || agents == "") {
                        println "Skipping build"
                        skipBuild = true
                    }
                                    
                    if (!skipBuild) {
                        println "Agents set for this build: " + agents
                    }
                }
            }
        }
    
        stage('Powershell deploy script checkout') {
            agent { label 'master' }
        
            when {
                expression {
                    !skipBuild
                }
            }
        
            steps {
                git url: 'https://github.com/owner/repo.git', credentialsId: 'git-credentials', branch: 'main'
                stash includes: 'deploy-script.ps1', name: 'deploy-script'
            }
        }
    
        stage('Deploy') {
            agent { label agentLabel }
        
            when {
                expression {
                    !skipBuild
                }
            }
        
            steps {
                unstash 'deploy-script'
            
                script {
                    println "Execute powershell deploy script on agents set for deploy"
                }
            }
        }
    }
}
