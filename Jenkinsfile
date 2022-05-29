node
{
    stage('ContinuousDownload') {
        git 'https://github.com/MRaju2022/maven.git'
    }
    stage('ContinuousBuild') {
        sh 'mvn package'
    }
    stage('ContinuousDeploy') {
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war  ubuntu@172.31.31.201:/var/lib/tomcat9/webapps/testenv.war'
    }
    stage('ContinuousTesting') {
        git 'https://github.com/MRaju2022/Testing.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery') {
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war  ubuntu@172.31.25.75:/var/lib/tomcat9/webapps/prodenv.war'
    }
}
