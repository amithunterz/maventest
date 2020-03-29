pipeline{
agent any
stages{
stage('compile stage'){
steps{
bat 'mvn clean compile'}
}

stage('Sonar analysis'){
steps{
	bat 'mvn sonar-scanner.bat -D"sonar.projectKey=sonarpipelinetest" -D"sonar.projectName=sonarpipelinetest" -D"sonar.sources=." -D"sonar.host.url=http://localhost:9000" -D"sonar.login=79940f09ee84c726b644ddeb9fcefad5db6020ad"'
}}


stage('testing stage'){
steps{

bat 'mvn test'}

}
stage('package stage'){
steps{

bat 'mvn package'}

}

}
}