pipeline{
    agent any
    environment{
    PATH="$PATH:/usr/share/maven/bin/"
}
    
        stages
        {
            stage("clone from github")
            {
                steps{
                git branch: 'main', changelog: false, credentialsId: 'devaraj2002', poll: false, url: 'https://github.com/devaraj2002/maven_webapp.git'
                }
            }
            stage("maven built")
            {
                steps
                {
                    sh 'mvn clean package'
                }
            }
            stage('deploy')
            {
                steps
                {
                    sshagent(['tomcat demo']) {
                        sh 'scp -o StrictHostKeyChecking=no target/demo.war ubuntu@54.221.155.220:/opt/tomcat/webapps'
    // some block
}
                    
                }
            }
        }
    
}
