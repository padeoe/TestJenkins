node {
stage('SCM') {
git 'https://github.com/padeoe/TestJenkins.git/'
}
stage('QA') {
bat 'sonar-scanner'
}
stage('build') {
def mvnHome = tool 'M3'
bat "${mvnHome}/bin/mvn -B clean package"
}
stage('deploy') {
bat "docker run --name my -p 11111:8080 -d tomcat"
bat "docker cp target/MavenDemo.war my:/usr/local/tomcat/webapps"

}
stage('results') {
archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
}
}